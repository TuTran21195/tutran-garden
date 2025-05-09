---
{"dg-publish":true,"dg-permalink":"/test/","permalink":"/test/","title":"Testing component","tags":["tutran-garden"],"created":"2025-05-09T16:25:36.286+07:00"}
---

# Heading 1 - test căn lề hai bên, chữ cái như ê ế ề ệ ê ư ứ ừ ơ ớ ờ ợ
## Heading 2: test mà của heading và `inline code` trong heading

### heading 3: test

#### Heading 4
##### Heading 5

###### Heading 6

Hỗ trợ đến heading 6, xem cách nó căn chỉnh lề hai bên nè: lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab

Callout nè:
>[!waning] lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab


>[!danger]- Folded
>lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab 

code block
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

Checkbox nè
- [ ] Checkbox này oke khom: lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
	- sau đó thì mình **imodule. Nhưng nên nhớ** khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất *cả các lab đã được commit* trên repo local. Vì thế cần tạo nhánh cho ~~repo để lưu mỗi~~ bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab
- [x] Checkbox này oke khom: lúc này phải chờ khá lâu, đồng thời khi xong thì nó sẽ yêu cầu nhập mật khẩu của dockerhub của mình (vd: `tutran21195` `<matkhau>`)  
	- sau đó thì mình imodule. Nhưng nên nhớ khi dùng `create-imodules.sh` thì nó sẽ đóng hết tất cả các lab đã được commit trên repo local. Vì thế cần tạo nhánh cho repo để lưu mỗi bài lab riêng, hoặc có thể xóa commit cũ đi để trên nhánh main luôn chỉ có 1 bài lab