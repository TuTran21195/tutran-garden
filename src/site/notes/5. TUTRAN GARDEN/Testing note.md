---
{"dg-publish":true,"dg-permalink":"test/","permalink":"/test/","title":"Testing component","tags":["tutran-garden"],"created":"2025-05-09T16:25:36.286+07:00"}
---

# Heading 1 - test căn lề hai bên, chữ cái như ê ế ề ệ ê ư ứ ừ ơ ớ ờ ợ
## Heading 2: test mà của heading và `inline code` trong heading

### heading 3: test

#### Heading 4
##### Heading 5

###### Heading 6
[[1. PROJECT/Giấu tin (Steg)/tutorial - Cách imodule bài lab đã tạo để publish\|tutorial - Cách imodule bài lab đã tạo để publish]]

Hỗ trợ đến ==heading 6==, xem cách nó căn <font color="#b2a2c7">chỉnh lề </font>hai bên <font color="#b2a2c7">nè: lúc này phải chờ</font> khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
sau đó thì mình<u> imodule</u>. Nhưng nên<span style="background:#fdbfff"> nhớ khi dùng </span>`create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab -> -> -> 

Callout nè:
>[!warning] lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab


>[!danger]- Folded
>lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab 

code block: kiểm tra xem có được định dạng màu không
```sh
git add my-new-lab 
git commit my-new-lab-m "Adding an IModule" 
cd $LABTAINER_DIR/distrib 
./publish.py -d -l my-new-lab
```
---
```sh
cd ~/labtainer/trunk/labs git init
```

Code: kiểm tra xem có được định dạng màu không. →  xem kỹ việc nó có bị biến đổi ký tự != hay không -> kiểm tra kỹ lại → → → → 
```python
def text_to_bits(message_file):
    with open(message_file, 'r') as f:
        message = f.read()
    bits = ''.join(format(ord(c), '08b') for c in message)
    return bits

if __name__ == "__main__":
    import sys
    if len(sys.argv) != 2:
        print("Usage: python3 1_encode_message_to_bits.py <message_file>")
        sys.exit(1)
    
    message_file = sys.argv[1]
    bits = text_to_bits(message_file)
    
    with open("message_bits.txt", "w") as f:
        f.write(bits)
    
    print(f"Message length: {len(bits)} bits.")
    print("Step 1: Encoding message to bits completed. Output: message_bits.txt")
```


Checkbox nè
- [ ] Checkbox này oke khom: lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
	- sau đó thì mình **imodule. Nhưng nên nhớ** khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất *cả các lab đã được commit* trên repo local. Vì thế cần tạo nhánh cho ~~repo để lưu mỗi~~ bài lab riêng, hoặc có [thể xóa commi](http.)t cũ đi để trên nhánh main luôn chỉ có 1 bài lab
- [x] Checkbox này oke khom: lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
	- sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab 

Thử paste ảnh:
![Pasted image 20250509165435.png|400](/img/user/2.%20RESOURCE/attachments/Pasted%20image%2020250509165435.png)
![Pasted image 20250509165531.png](/img/user/2.%20RESOURCE/attachments/Pasted%20image%2020250509165531.png)

lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`) sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab

