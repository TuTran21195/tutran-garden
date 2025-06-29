---
{"dg-publish":true,"permalink":"/1-project/an-toan-mang-nang-cao/chu-y-nhung-cau-sau/","title":"Cheatsheet chương 4","tags":["cheatsheet"],"created":"2025-06-24T20:19:09.235+07:00"}
---

- biện pháp kiểm soát truy cập dựa trên chính sách được sử dụng cho cho <u>quản lý danh tính</u>: **ABAC**
- **RBAC** (rule base access control) - dựa trên vai trò →  ứng dụng: **firewall**
- **DAC**: kiểm soát truy cập - tạo ra đối tượng có thể cấp quyền truy cập cho người dung khác - **Trojan horse**
- **MAC**: kiểm soát truy cập dựa trên **tính nhạy cảm** về thông tin.
- ACL: Mỗi **đối tượng** được gán 1 dsach người dùng kèm quyền truy cập


- Biba - Đọc lên ghi xuống
- Bella - Đọc xuống ghi lên → là một phương pháp triển khai biện pháp kiểm soát truy cập **MAC**.
	Còn **ACL** → là một phương pháp triển khai biện pháp kiểm soát truy cập **DAC** nhé.
- HRU:  cho phép **thay đổi quyền truy cập** của chủ thể lên đối tượng, thêm hoặc xóa các chủ thể và đối tượng
- Clark-Wilson: tập trung vào việc **ngăn chặn người dùng sửa đổi** trái phép dữ liệu thông qua một chương trình

- giao thức PPP, khóa chung được trao đổi để mã hóa và giải mã → thông qua giao thức **CHAP**

- PGP: 
	- xác thực thông điệp bằng: **tạo và kiểm tra chữ ký số**
	- Trong giao thức PGP chỉ đảm bảo tính <u>xác thực</u>, khóa công khai và khóa riêng được sử dụng là...   **của người gửi.**
	- Trong giao thức PGP chỉ đảm bảo tính <u>bí mật</u>, khóa công khai và khóa riêng được sử dụng là... **của người nhận**
	- PGP đảm bảo tính bí mật thông điệp bằng cách sử dụng: Mã hóa khóa **bất đối xứng** sử dụng khóa công khai


- AH không cung cấp **tính bí mật**
- ESP không cung cấp **tính sẵn dùng**
- xác thực: xác minh tính chân thực của thông tin nhận dạng ng dùng cung cấp 
- IPsec:
	- ứng dụng của nó: **VPN**
	- **DH** Không phải thành phần của IPsec

- ứng dụng của mô hình <u>nền tảng</u> như 1 dịch vụ: Google App Engine
- ứng dụng thực tế của mô hình <u>phần mềm</u> như một dịch vụ: Google Gmail
- ứng dụng thực tế của mô hình <u>hạ tầng</u> như 1 dịch vụ là: Amazon EC2

- WPA: TKIP
- WPA2: CBC-AES,


- PKI: {**CA, RA, VA**}
	- CA: xác minh kiểm tra tính hợp lệ của chứng chỉ số khóa công khai của ng dùng
	- RA
	- VA

- Chứng chỉ số
	- Thuộc tính chứa thông tin định danh chủ thể của chứng chỉ số khóa công khai là: **Subject**
	- mục đích sử dụng của chứng chỉ số là để xác minh ... của một khóa công khai. →  **chủ thể thực sự**
	- Một kỹ thuật đảm bảo tính xác thực thông tin truyền?

- Chữ ký số
	- Chữ ký số (sử dụng riêng) thường được sử dụng để đảm bảo thuộc tính nào sau đây của thông điệp truyền đưa:   **Tính toàn vẹn**

## Tường lửa
- Tường lửa:
	- tính năng của kiểm soát truy cập sử dụng tường lửa:  **Kiểm soát dịch vụ và hướng**
	- không thể chông lại tấn công hướng dữ liệu
	- Đâu **KHÔNG PHẢI** là một kiến trúc triển khai phổ biến của tường lửa? - Packet-filtering firewalls
	- Một Screened host firewall là sự kết hợp của: Một packet-filtering router và một tường lửa riêng, chuyên dụng
	- Đâu **KHÔNG PHẢI** là một dạng tường lửa lọc gói? - Stateless packet inspection

## Mã hóa đx và bất đx
- Các loại mã hóa khóa đối xứng: AES, DES, IDEA, Blowfish, Twofish
- Các loại mã hóa khóa bất đối xứng: RSA, Elgamal, Elliptic curve cryptosystem (ECC)

## WLAN
- Đâu **KHÔNG PHẢI** là một dạng tấn công vào WLAN <u>doanh nghiệp</u>: Chèn mã độc
- Đâu **KHÔNG PHẢI** là một dạng tấn công vào WLAN <u>gia đình</u>: Chặn bắt dữ liệu không dây
## VPN

- giao thức bảo mật trong VPN: PPTP, IPSec, SSL/TLS
- - L2TP - có giao thức bảo mật: **PPP và IPsec** (là một giao thức mạng riêng ảo)
## Điện toán đám mây
- Đâu là đặc tính thiết yếu của điện toán đám mây cho phép <u>thay đổi qui mô</u> sử dụng tài nguyên dễ dàng? - **Rapid elasticity**
- Đâu là đặc tính thiết yếu của điện toán đám mây cho phép <u>gộp, cấp phát động và cấp phát lại</u> tài nguyên tính toán? - **Resource pooling**
- Đâu **KHÔNG PHẢI** là 1 đặc tính thiết yếu của điện toán đám mây? - **Resource queueing**

- Đâu **KHÔNG PHẢI** là một biện pháp bảo mật dữ liệu và ứng dụng trong điện toán đám mây? - **Bảo mật các server**

- Đâu **KHÔNG PHẢI** là một mô hình triển khai điện toán đám mây? - **Hibrid** (vì nó nên là H**y**brid)
- Đâu KHÔNG PHẢI là một mô hình triển khai điện toán đám mây? **Privacy** (vì nó nên là Private)

- Đâu **KHÔNG PHẢI** là một công nghệ nền tảng xây dựng điện toán đám mây? - Grid Computing
-  Salesforce CRM, Gmail, Microsoft Office 365
-   laaS, PaaS, SaaS
	- IaaS cho phép khách hàng: thuê máy chủ và kết nối mạng
	- Saas Cho phép khách hàng: thuê phần mềm của nhà cung cấp





## Intranet
- intranet:
	- Đâu **KHÔNG PHẢI** là một mối đe dọa bảo mật <u>từ bên ngoài</u> đối với Intranet?  - Rò rỉ dữ liệu
	- Đâu **KHÔNG PHẢI** là một mối đe dọa bảo mật <u>nội bộ </u>đối với Intranet? - Chặn dữ liệu trong quá trình truyền tải
	- Đâu **KHÔNG PHẢI** là một giải pháp bảo mật Intranet? -  Cấm tích hợp của bên thứ ba.