---
{"dg-publish":true,"permalink":"/1-project/an-toan-mang-nang-cao/cheatsheet-chuong-2/","title":"Cheatsheet chương 2","tags":["cheatsheet"],"created":"2025-06-24T19:59:27.423+07:00"}
---



# Cheetsheet - Prompt 1
Chào bạn, để giúp bạn ôn tập cho bài kiểm tra môn An toàn mạng nâng cao, tôi đã tổng hợp một cheatsheet chi tiết về **Chương 2: CÁC KỸ THUẬT BẢO MẬT THÔNG TIN TRUYỀN** từ các nguồn bạn cung cấp.

---

### **Cheatsheet Chương 2: CÁC KỸ THUẬT BẢO MẬT THÔNG TIN TRUYỀN**

#### **1. Các Yêu Cầu Bảo Mật Thông Tin Truyền**

Thông tin truyền/lưu thông là thông tin động, được vận chuyển trên hệ thống truyền thông. Các yêu cầu bảo mật cơ bản bao gồm:

- **Tính bí mật (Confidentiality)**
    - Đảm bảo thông tin truyền không bị tiết lộ cho các bên không có thẩm quyền.
    - Kỹ thuật phổ biến: mã hóa, kiểm soát truy cập, che giấu dữ liệu.
- **Tính toàn vẹn (Integrity)**
    - Đảm bảo thông tin không bị giả mạo hoặc sửa đổi trái phép (bao gồm bảo vệ khỏi sửa đổi, xóa, bổ sung trái phép).
    - Kỹ thuật phổ biến: chữ ký số, mã xác thực thông điệp (MAC), băm dữ liệu.
- **Tính xác thực (Authenticity)**
    - Đảm bảo thông tin đến từ một nguồn đáng tin cậy (bảo vệ chống mạo danh, giả mạo).
    - Kỹ thuật phổ biến: xác thực, chứng chỉ số, nhận dạng sinh trắc học.
- **Tính chống chối bỏ (Non-repudiation)**
    - Đảm bảo một bên không thể phủ nhận việc đã gửi hoặc nhận một thông điệp/giao dịch (chống tấn công giả mạo và phát lại).
    - Kỹ thuật phổ biến: chữ ký số, mã xác thực thông điệp, tem thời gian.

**Các Lĩnh Vực Ứng Dụng** Bảo mật thông tin truyền được ứng dụng rộng rãi trong:

- Các dịch vụ mạng (cổng thông tin điện tử, học tập trực tuyến, mạng xã hội).
- Trao đổi thông tin (ứng dụng nhắn tin, dạy học trực tuyến).
- Thương mại điện tử (sàn TMĐT, website TMĐT).
- Thanh toán, dịch vụ tài chính, ngân hàng (ngân hàng trực tuyến, thanh toán trực tuyến).

#### **2. Các Giải Pháp Bảo Mật Thông Tin Dựa Trên Mật Mã**

##### **2.1. Mã hóa dữ liệu**

Được sử dụng để đảm bảo **tính bí mật** của thông tin truyền.

- **Hệ mật mã khóa đối xứng:**
    - Sử dụng **chung một khóa bí mật** cho cả mã hóa và giải mã.
    - **Ưu điểm:** Kích thước khóa nhỏ, tốc độ cao, độ bảo mật cao.
    - **Thích hợp:** Mã hóa/giải mã lượng lớn dữ liệu.
    - **Khó khăn:** Trao đổi khóa dùng chung.
    - **Ví dụ:** DES, 3-DES, AES, IDEA, Twofish, Blowfish.
- **Hệ mật mã khóa bất đối xứng:**
    - Sử dụng **khóa công khai** cho mã hóa và **khóa riêng** cho giải mã.
    - **Ưu điểm:** Trao đổi khóa dễ dàng hơn do khóa mã hóa là công khai.
    - **Hạn chế:** Kích thước khóa lớn, tốc độ thấp (trừ ECC).
    - **Thích hợp:** Mã hóa/giải mã lượng nhỏ dữ liệu (trao đổi khóa bí mật, ký số).
    - **Ví dụ:** RSA, Elgamal, Elliptic Curve Cryptosystem (ECC).

##### **2.2. Hàm băm (Hash function)**

- **Định nghĩa:** Ánh xạ chuyển đổi dữ liệu có kích thước thay đổi về dữ liệu có kích thước cố định, thường được gọi là bản tóm lược (digest) của thông điệp.
- **Công dụng:** Mã hóa mật khẩu, tạo chuỗi xác thực thông điệp (MAC), tạo và kiểm tra chữ ký số.
- **Các loại hàm băm thông dụng:** CRC-32, họ MD (MD2, MD4, MD5, MD6), họ SHA (SHA0, SHA1, SHA2, SHA3).

##### **2.3. Các hệ mật mã lai (Hybrid cryptosystem)**

- **Kết hợp:** Hệ mật khóa công khai và hệ mật khóa bí mật để tận dụng điểm mạnh của cả hai.
    - **Khóa công khai:** Để trao đổi khóa bí mật (dễ dàng trao đổi khóa).
    - **Khóa bí mật:** Để mã hóa/giải mã dữ liệu truyền (tốc độ cao).
- **Ví dụ:** RSA + AES, Diffie-Hellman + AES, RSA + 3-DES.

##### **2.4. Chữ ký số (Digital signature)**

- Một chuỗi dữ liệu liên kết với một thông điệp và thực thể tạo ra thông điệp.
- Thường được sử dụng để đảm bảo **tính toàn vẹn** của thông điệp.
- **Giải thuật:** Khóa riêng của người gửi để tạo chữ ký, khóa công khai của người gửi để kiểm tra.
- **Quá trình ký (bên gửi):**
    1. Tính **chuỗi đại diện (hash value)** của thông điệp.
    2. Ký chuỗi đại diện bằng **khóa riêng** của người gửi để tạo **chữ ký số** (chuỗi đại diện được mã hóa).
    3. Ghép thông điệp gốc với chữ ký số để tạo **thông điệp đã ký**.
    4. Gửi thông điệp đã ký cho người nhận.
- **Quá trình kiểm tra (bên nhận):**
    1. Tách chữ ký số và thông điệp gốc.
    2. Tính chuỗi đại diện MD1 của thông điệp gốc.
    3. Sử dụng **khóa công khai** của người gửi để giải mã chữ ký số → chuỗi đại diện thông điệp MD2.
    4. **So sánh MD1 và MD2:**
        - Nếu **MD1 = MD2:** Chữ ký hợp lệ, thông điệp đảm bảo tính toàn vẹn và xác thực từ người gửi.
        - Nếu **MD1 ≠ MD2:** Chữ ký không hợp lệ, thông điệp có thể đã bị sửa đổi hoặc không từ người gửi.
- **Một số giải thuật:** RSA, DSA, ECDSA, EdDSA.

##### **2.5. Chứng chỉ số (Digital certificate)**

- Tài liệu điện tử sử dụng chữ ký số để liên kết một khóa công khai với thông tin nhận dạng của một thực thể.
- **Thông tin chính:** Thông tin định danh của chủ thể, khóa công khai của chủ thể, chữ ký số của CA (Certificate Authority - Cơ quan cấp chứng chỉ).
- **Tiêu chuẩn:** X.509 là chuẩn quốc tế được sử dụng rộng rãi (ví dụ: SSL/TLS).
- **Các loại chứng chỉ X.509:**
    - **Root certificate:** Chứng chỉ tự ký của một CA, là điểm kết thúc của chuỗi chữ ký.
    - **Intermediate certificate:** Chứng chỉ nhánh của CA, được ký bởi Root certificate.
    - **End-entity certificate:** Chứng chỉ cấp cho người/tổ chức sử dụng.
- **Sử dụng:** Đảm bảo an toàn giao dịch trên nền web (HTTPS), email, FTP, v.v..

##### **2.6. Hạ tầng khóa công khai (Public-key infrastructure - PKI)**

- Một tập hợp các phần cứng, phần mềm, nhân lực, chính sách và thủ tục để tạo, quản lý, phân phối, sử dụng, lưu trữ và thu hồi các chứng chỉ số.
- **Các thành phần chính:**
    - **Certificate Authority (CA):** Cấp và kiểm tra chứng chỉ số.
    - **Registration Authority (RA):** Kiểm tra thông tin nhận dạng người dùng theo yêu cầu của CA.
    - **Validation Authority (VA):** Xác nhận thông tin nhận dạng người dùng thay mặt CA.
    - **Central Directory (CD):** Nơi lưu danh mục và lập chỉ số các khóa.
    - **Certificate Management System:** Hệ thống quản lý chứng chỉ.
    - **Certificate Policy:** Chính sách về chứng chỉ.
- **Lưu đồ cấp và sử dụng chứng chỉ số:**
    1. **Người dùng** tạo cặp khóa (công khai + riêng) và yêu cầu cấp chứng chỉ (gồm khóa công khai và thông tin định danh).
    2. **RA** kiểm tra yêu cầu, chuyển đến CA.
    3. **CA** xác minh thông tin, nếu thành công thì cấp chứng chỉ số (được CA ký bằng khóa riêng của mình).
    4. **CA** chuyển thông tin chứng chỉ đã cấp cho VA để xác nhận.
    5. **Người dùng** cài đặt và sử dụng chứng chỉ.
    6. Khi giao dịch, người dùng gửi chứng chỉ và đơn hàng đã ký cho nhà cung cấp.
    7. **Nhà cung cấp** chuyển chứng chỉ cho VA kiểm tra, sau đó dùng khóa công khai từ chứng chỉ để xác thực chữ ký số của người dùng.

##### **2.7. Giấu tin (Steganography)**

- Kỹ thuật giấu một lượng thông tin nhất định vào một vật mang (ảnh, video, văn bản) mà không làm thay đổi đáng kể hình thức và nội dung của vật mang.
- **Sự khác biệt với mật mã:** Bên thứ ba không biết sự tồn tại của thông tin mật nếu chỉ quan sát vật mang (trong mật mã thì biết sự tồn tại của bản mã).
- Có thể kết hợp với mật mã để tăng cường độ an toàn.

#### **3. Các Giao Thức Bảo Mật Thông Tin**

##### **3.1. PGP (Pretty Good Privacy)**

- Cung cấp **tính riêng tư (bí mật)** và **tính xác thực**.
- Cho phép:
    - **Mã hóa dữ liệu** sử dụng kết hợp mã hóa khóa bí mật (cho thông điệp) và mã hóa khóa công khai (để trao đổi khóa bí mật).
    - **Tạo và kiểm tra chữ ký số**.

##### **3.2. SSL/TLS**

- **SSL** (Netscape, 1993, các phiên bản 1.0, 2.0, 3.0) hiện ít được sử dụng.
- **TLS** (IETF, 1999, dựa trên SSL 3.0, các phiên bản 1.0, 1.1, 1.2, 1.3) là giao thức hiện hành.
- **Đặc điểm:**
    - Sử dụng mã hóa **khóa công khai** để trao đổi **khóa phiên** (session key).
    - Sử dụng khóa phiên và mã hóa **khóa bí mật** để mã hóa toàn bộ dữ liệu trao đổi.
    - Sử dụng **hàm băm có khóa (MAC)** để đảm bảo **tính toàn vẹn** và **xác thực** thông điệp.
    - Ít nhất một thực thể (thường là server) phải có **chứng chỉ số** cho khóa công khai.
- **Các giao thức con của SSL:** Handshake Protocol, Change Cipher Spec Protocol, Alert Protocol, Record Protocol.

##### **3.3. IPSec (Internet Protocol Security)**

- Bộ chuẩn gồm các giao thức cung cấp **tính bí mật, toàn vẹn và xác thực** thông tin giao tiếp giữa 2 điểm trên mạng IP.
- Bảo mật dữ liệu truyền tại **lớp Mạng (IP)** trong mô hình OSI/TCP/IP.
- Sử dụng rộng rãi trong **VPN**.
- Bao gồm các giao thức cho trao đổi và quản lý khóa an toàn.
- **Đặc điểm:** Xác thực, bí mật, toàn vẹn, quản lý khóa, tạo đường hầm, linh hoạt, khả năng tương tác.
- **Ưu điểm:** Bảo mật mạnh mẽ, khả năng tương thích rộng, linh hoạt, khả năng mở rộng, cải thiện hiệu suất mạng.
- **Nhược điểm:** Cấu hình phức tạp, sự cố tương thích, tác động đến hiệu suất, quản lý khóa, hạn chế miền bảo vệ (chỉ IP).
- **Các thành phần chính:**
    - **IP security policy:** Nền tảng hoạt động của IPSec, xác định SA phù hợp.
        - **Security Association (SA):** Kết nối logic 1 chiều giữa người gửi và người nhận để cung cấp dịch vụ bảo mật. Nhận dạng bởi SPI, IP Destination Address, Security Protocol Identifier.
        - **Security Association Database (SAD):** Định nghĩa các tham số liên quan đến mỗi SA.
        - **Security Policy Database (SPD):** Hỗ trợ xác định SA cho lưu lượng IP.
    - **IKE (Internet Key Exchange):** Giao thức sinh, trao đổi và duy trì khóa trong IPSec.
    - **AH (Authentication Header):** Cung cấp **xác thực** (toàn vẹn dữ liệu, nguồn gốc, chống phát lại) cho toàn bộ gói IP.
    - **ESP (Encapsulating Security Payload):** Cung cấp **tính bí mật (mã hóa)** và **xác thực** (toàn vẹn, nguồn gốc, chống phát lại) cho phần datagram IP.
- **Các chế độ hoạt động:**
    - **Chế độ vận chuyển (Transport mode):** Chỉ bảo vệ **dữ liệu (payload)** gói tin. Kém an toàn hơn, nhanh hơn.
    - **Chế độ đường hầm (Tunnel mode):** Bảo vệ **toàn bộ gói tin ban đầu** (header + payload). An toàn cao hơn, chậm hơn.

##### **3.4. HTTPS**

- Sự kết hợp của giao thức **HTTP và SSL/TLS** để bảo mật giao tiếp giữa máy chủ và máy khách web.
- Các thành phần được mã hóa: URL, nội dung tài liệu, form, cookie, HTTP header.
- Các request/response được đóng gói trong SSL/TLS để đảm bảo tính bí mật, toàn vẹn và xác thực chủ thể.

##### **3.5. SSH (Secure Shell)**

- Giao thức bảo mật thông tin truyền với thiết kế đơn giản, chi phí thấp.
- Cung cấp tiện ích bảo mật cho đăng nhập từ xa (thay thế Telnet).
- **Các thành phần:**
    - **Transport Layer Protocol:** Hỗ trợ xác thực máy chủ, tính bí mật và toàn vẹn dữ liệu.
    - **User Authentication Protocol:** Xác thực người dùng với máy chủ.
    - **Connection Protocol:** Hỗ trợ nhiều kênh giao tiếp đồng thời trên một kết nối SSH.
- **Các phương pháp xác thực người dùng:** publickey (khóa công khai), password (mật khẩu), hostbased (theo host).

##### **3.6. S/MIME (Secure/Multipurpose Internet Mail Extension)**

- Giải pháp bảo mật tăng cường an toàn cho giao thức vận chuyển email MIME.
- **Cung cấp:**
    - **Tính bí mật dữ liệu** (kết hợp mã hóa khóa công khai và bí mật).
    - **Xác thực tính toàn vẹn** (sử dụng chữ ký số).
    - Nén dữ liệu.

---

Hy vọng cheatsheet này sẽ giúp bạn hệ thống lại kiến thức và ôn tập hiệu quả cho bài kiểm tra! Chúc bạn thành công!