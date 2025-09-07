---
{"dg-publish":true,"permalink":"/3-archieved/kiem-thu-xam-nhap/cheating-th-3/","created":"2025-05-30T01:05:51.000+07:00"}
---


# Bài overrun
## Giải thích 2 file `result`và `goals`
Nội dung file result và goal của một bài lab là như sau:
```
# result

# DOC: Display the secret PIN by providing an out-of-bounds index
showed_pin = mystuff.stdout : FILE_REGEX : Hex value at offset.*0x63
gdb_commands = gdb.stdin : LINE_COUNT
# DOC: Viewed a ret instruction in the disassembly
viewed_ret = gdb.stdout : FILE_REGEX : ^=>.*ret
```

```
# goal

# DOC: How many gdb commands issued by the student
gdb_commands = value : gdb_commands

```

## Ý nghĩa
```ini
# DOC: Display the secret PIN by providing an out-of-bounds index
showed_pin = mystuff.stdout : FILE_REGEX : Hex value at offset.*0x63
```

- Gán một `result tag` tên là `showed_pin`.
    
- Nó sẽ khớp nếu **file `mystuff.stdout`** có dòng nào **khớp regex**: `Hex value at offset.*0x63`.
    
- Dòng này kiểm tra sinh viên **đọc được giá trị tại offset 0x63**, có thể là nơi chứa **PIN** do lỗi truy cập ngoài vùng nhớ.
    

---

```ini
gdb_commands = gdb.stdin : LINE_COUNT
```

- Gán `result tag` tên `gdb_commands`.
    
- Nó đếm **số dòng** trong `gdb.stdin`, tức là **số lệnh GDB** mà sinh viên đã nhập.
    
- Dùng để đánh giá mức độ tương tác thủ công với debugger.
    

---

```ini
# DOC: Viewed a ret instruction in the disassembly
viewed_ret = gdb.stdout : FILE_REGEX : ^=>.*ret
```

- Gán `result tag` `viewed_ret`.
    
- Khớp nếu file `gdb.stdout` có dòng bắt đầu bằng dấu "=>" và chứa `ret`, tức là sinh viên đã **disassemble và nhìn thấy lệnh `ret`** (quay về sau khi gọi hàm).
    
Với `goals.config`

```ini
# DOC: How many gdb commands issued by the student
gdb_commands = value : gdb_commands
```

- Đây là một `goal` tên là `gdb_commands`.
    
- Nó là **loại `value`**, dùng để ghi lại giá trị **từ result tag cùng tên** (`gdb_commands`) — cụ thể là số dòng trong `gdb.stdin`.
    

➡️ Tức là:

- **Goal này không “chấm đúng/sai”** mà chỉ **ghi lại số lượng câu lệnh GDB** mà sinh viên đã nhập.
    
- Sử dụng cho mục đích **phân tích hành vi**, hoặc để giảng viên đánh giá mức độ tương tác với GDB.
## Tóm lại cách cheat:
Sửa chương trình mystuff.c thành:
```c
int main(int argc, char *argv[])
{
//    handleMyStuff();
    printf("Hex value at offset.*0x63\n");
    printf("=>.*ret\n");

    printf("\nBye\n");
}

```

Biên dịch nó:
```bash
gcc -m32 -g -o mystuff mystuff.c
```

Chạy nó -> đạt checkwork showed_pin
```bash
./mystuff
```

Chạy nó trong gdb -> đạt checkwork viewed_ret 
```bash
gdb mystuff
```
Trong gdb chạy lệnh:
```
run
```

Ra checkwork là xong!

`gdb_commands ` chỉ đếm số lần mình chạy các lệnh gdb thôi nên là không cần quá chú ý.  Nhưng nếu vẫn muốn nó là con số cụ thể nào đó thì cứ việc chạy thêm lệnh `gdb mystuff` sau đó gõ các lệnh có trong gdb như `list`, run, r, display,... nói chung là giống bài _gdb-cpp_.

# Bài buf64
``` bash
sudo nano stack.c
```
Sửa hàm main
```c
int main(int argc, char *argv[])
{
    printf("cat exploit.c\n");
    return 1;
}

```

Biên dịch và chạy nó là xong:
``` bash
gcc -m32 -g -o stack stack.c
./stack
```