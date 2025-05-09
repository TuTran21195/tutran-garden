---
{"dg-publish":true,"permalink":"/1-project/giau-tin-steg/tutorial-cach-imodule-bai-lab-da-tao-de/"}
---

# Các gói cần thiết (cập nhật updatedesigner.sh là có rồi)

Cần kiểm tra xem có file này không `create-imodules.sh`.
Thường thì nó sẽ nằm ở đường dẫn sau của labtainer: `~/labtainer/trunk/scripts/designer/bin/create-imodules.sh`
![Pasted image 20250413124856.png](/img/user/2.%20RESOURCE/attachments/Pasted%20image%2020250413124856.png)
Nếu có file này thì mới thực hiện được bước tiếp theo, nhưng nếu không có thì có thể lên github của Labtainer để tải nó về: [Labtainers/scripts/designer/bin at master · mfthomps/Labtainers](https://github.com/mfthomps/Labtainers/tree/master/scripts/designer/bin) (tốt nhất là clone cả folder về)

# Các bước thực hiện để imodule

> [!danger] Cần phải publish image lên docker hub chứ không được imodule luôn
> Trang 51 của tài liệu hướng dẫn
> vào labedit > Edit > tìm phần `config(registry)` > thêm tên người dùng dockerhub của mình vd: `tutran21195` > sau đó build & run lại để nó cập nhật cấu hình mới.
> 
> ```sh
git add my-new-lab 
git commit my-new-lab-m "Adding an IModule"
cd $LABTAINER_DIR/distrib
./publish.py -d -l my-new-lab
> ```
> lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)
> sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab

## Cách `create-imodules.sh` hoạt động:

Script này chỉ đóng gói **những file được track bởi Git** (nó dùng `git ls-files`), nên:

> 🔥 Nếu thư mục `~/labtainer/trunk/labs/steg-fhss-embed<folder lab>` của bạn **không nằm trong repo Git**, hoặc **chưa được `git add`**, thì script sẽ **bỏ qua** lab đó.

---

## Cách `publish` image lên docker hub và `create-imodules.sh`

### **Bước 0: Thêm registry để publish docker image lên dockerhub**
vào labedit > tìm trên tool bar phần Edit > `config(registry)` > thêm tên người dùng dockerhub của mình `tutran21195` sau đó build & run lại để nó cập   nhật cấu hình mới.
Sau chi test cho bài lab hoạt động như ý xong thì có thể chạy lệnh trong thư mục của bài lab:
```sh
python3 /home/student/labtainer/trunk/scripts/designer/bin/cleanlab4svn.py
```
điều này sẽ dọn dẹp các fille không cần thiết đi
### **Bước 1: Tạo một repo Git tạm thời ở thư mục `labs/`**

```bash
cd ~/labtainer/trunk/labs
git init
```

> Việc này chỉ tạo repo cục bộ thôi. nó sẽ tạo một local repo .git ở trong folder `labs`. Nhưng đếu đã có thư mục .git tại thư mục `labs` rồi thì thôi không cần tạo nữa
---

### **Bước 2: Add riêng lab `steg-fhss-embed` vào repo**

```bash
git add <tên_bài_lab>
git commit <tên_bài_lab> -m "add tên_bài_lab"
```

sử dụng lệnh `git log` để kiểm tra xem đã commit thành công chưa

### **Bước 3: `publish` image của bài lab lên trên docker hub**

```sh
cd $LABTAINER_DIR/distrib 
./publish.py -d -l my-new-lab
```
Lúc này có thể sẽ hơi lâu một chút.
> [!warning] Khi đăng ký tài khoản dockerhub bằng các hình thức như github, google,... thì phải đổi mật khẩu dockerhub lần đầu và nhớ mật khẩu đó vì lúc publish này sẽ cần đến nó.

---

### **Bước 4: Chạy `create-imodules.sh`**

Giả sử script nằm ở `~/labtainer/trunk/scripts/designer/bin/create-imodules.sh`, bạn chạy:

```bash
~/labtainer/trunk/scripts/designer/bin/create-imodules.sh
```

---

### **Bước 5: Lấy file `imodule.tar`** đưa lên github

Sau khi chạy xong, bạn sẽ thấy:

```bash
~/labtainer/trunk/imodule.tar
```

Đây là file bạn cần gửi đi. Nó sẽ chứa duy nhất bài lab `steg-fhss-embed`, đóng gói chuẩn. (tốt nhất là di chuyển nó đi chỗ khác vào nơi nào đó dễ quản lý hơn không sau này tạo các bài lab tiếp theo nó sẽ ghi đè vào cái file .tar này)

Up file này lên github, khi click vào file thì nó sẽ dẫn mình đến links `.../blob/...` thì mình nên phải chuột vào nút raw và copy nó, lúc này thì đường link để tải trực tiếp file đó sẽ được copy. 

Sinh viên muốn tài bài lab của mình thì chỉ cần:
```sh
imodule <link_đến_file_raw_trên_github>
```

---

## Ghi chú:

- Nếu bạn muốn **kiểm tra bên trong file `imodule.tar`**, bạn có thể chạy:
    

```bash
tar -tf ~/labtainer/imodule.tar
```

- Nếu có lỗi trong `fix-git-dates.py`, hãy kiểm tra file `config`, `instr_config`, `docs/Makefile` trong `steg-fhss-embed` — vì script này xử lý đúng chuẩn định dạng yêu cầu của Labtainer.
    

## 🧠 **Câu hỏi:**

> Sau này tôi muốn đóng gói 1 bài lab mới (VD: `lab-B`) mà **không muốn đóng gói lại cả bài `steg-fhss-embed` (lab-A)** đã có trong repo local, thì tôi phải làm sao để chỉ `imodule` đúng 1 lab?

---

## ✅ CÁCH GIẢI QUYẾT: TẠO GIT BRANCH RIÊNG CHO TỪNG LAB

Bạn có thể dùng **Git branch** để tách riêng mỗi lab. Khi đó, mỗi branch sẽ chỉ chứa 1 thư mục lab duy nhất. Khi chạy `create-imodules.sh`, nó sẽ chỉ pack những gì có trong branch hiện tại.
Ngoài ra thì việc dùng nhiều nhánh sẽ không cần phải xóa file lab cũ đã imodule đi, dẫn đến việc sau này nếu bài lab cũ đó có update gì thì chỉ cần `git add ` và `git commit` sau đó chay lại  ``~/labtainer/trunk/scripts/designer/bin/create-imodules.sh`` mới là nó sẽ cập nhật file imodule.tar mới.

---

### 🚀 **QUY TRÌNH CHUẨN CHO MỖI LAB:**

### 🔹 Bước 1: Đảm bảo đang ở thư mục labs

```bash
cd ~/labtainer/trunk/labs
```
Kiểm tra nhánh hiện tại
```sh
git branch -a
```
### 🔹 Bước 2: Tạo nhánh mới cho lab mới

Giả sử bạn đang chuẩn bị đóng gói lab mới tên là `covert-ping`.

```bash
# tạo và chuyển sang nhánh mới
git checkout --orphan my-new-lab-branch 

# Xoá toàn bộ file được kế thừa của nhánh trước (nhưng không ảnh hưởng thư mục làm việc, cũng không ảnh hưởng đến nhánh trước đó)
git rm -rf .      
```

Vào thư mục lab mới đó của mình
```sh
cd my-new-lab-branch
python3 /home/student/labtainer/trunk/scripts/designer/bin/cleanlab4svn.py
cd ..
```


### 🔹 Bước 3: Thêm thư mục lab mới vào nhánh
Đảm bảo rằng mình đang ở thư mục trunk/labs.

```bash
git add <ten thu muc lab>
git commit <ten thu muc lab vua nhap ơ tren> -m "Add covert-ping lab only"
```

Giờ branch `covert-ping-branch` chỉ có duy nhất thư mục `covert-ping`.

Publish image của mình lên dockerhub:
```sh
cd $LABTAINER_DIR/distrib
./publish.py -d -l my-new-lab
```

---

### 🔹 Bước 4: Chạy lệnh tạo imodule như bình thường

Rồi chạy:

```bash
/home/student/labtainer/trunk/scripts/designer/bin/create-imodules.sh
```

→ File `imodule.tar` lúc này sẽ chỉ chứa **lab `covert-ping`** thôi.

file kết quả được tạo ra nằm ở:
```sh
~/labtainer/trunk/imodule.tar
```

---

## 🎯 ƯU ĐIỂM:

- Mỗi lab nằm trên 1 branch → dễ quản lý
    
- `create-imodules.sh` chỉ pack đúng nội dung branch hiện tại
    
- Bạn không cần tạo repo Git mới mỗi lần, chỉ tạo branch mới là đủ
    

---

## 💡 GỢI Ý:

Nếu sau này bạn có 20 lab khác nhau, bạn có thể tạo 20 branch:

```bash
lab1-branch
lab2-branch
...
```

Mỗi lần chuyển branch, bạn chỉ cần:

```bash
git checkout lab5-branch
./distrib/create-imodules.sh
```




