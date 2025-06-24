---
{"dg-publish":true,"permalink":"/1-project/an-toan-mang-nang-cao/cheatsheet-chuong-1/","title":"Cheatsheet chương 1","tags":["cheatsheet"],"created":"2025-06-24T19:37:28.671+07:00"}
---



# Cheetsheet - Prompt 1
Chào bạn, để giúp bạn ôn tập cho bài kiểm tra môn An toàn mạng nâng cao, tôi đã tổng hợp một cheatsheet chi tiết cho Chương 1 – "Các Kỹ thuật và Công nghệ Đảm bảo An toàn Mạng" dựa trên các tài liệu bạn cung cấp. Tôi sẽ tập trung vào các khái niệm chính, phân loại, đặc điểm, ưu nhược điểm và các điểm nổi bật mà bài trắc nghiệm đã nhấn mạnh.

---

### **CHEATSHEET CHƯƠNG 1: CÁC KỸ THUẬT VÀ CÔNG NGHỆ ĐẢM BẢO AN TOÀN MẠNG**

**Mục lục Môn học:** Môn học "An toàn mạng nâng cao" bao gồm các nội dung chính sau:

- Các kỹ thuật và công nghệ đảm bảo an toàn mạng.
- Các kỹ thuật bảo mật thông tin trên đường truyền.
- Bảo mật cho các hệ thống mạng.
- Bảo mật cho điện toán đám mây.
- Lưu ý: **"Phân tích rủi ro tài chính" không thuộc nội dung môn học này**.

---

#### **1. Kiểm soát truy cập (Access Control)**

**Khái quát về kiểm soát truy cập:**

- **Định nghĩa:** Là quá trình mà trong đó người dùng được nhận dạng và trao quyền truy cập đến các thông tin, các hệ thống và tài nguyên.
- **Hệ thống kiểm soát truy cập cấu thành từ 3 dịch vụ chính**:
    - **Xác thực (Authentication):** Xác minh tính chân thực của thông tin nhận dạng người dùng cung cấp.
    - **Trao quyền (Authorization):** Xác định các tài nguyên người dùng được phép truy cập sau khi xác thực.
    - **Quản trị (Administration):** Cung cấp khả năng thêm, bớt và sửa đổi thông tin tài khoản người dùng và quyền truy cập.
    - **Lưu ý:** Xác thực và Trao quyền là 2 dịch vụ thiết yếu. **Mã hóa (Encryption) không phải là một phần của hệ thống kiểm soát truy cập**.
- **Mục đích chính:** Đảm bảo **tính bí mật, toàn vẹn và sẵn dùng của thông tin, hệ thống và các tài nguyên**.
    - **Tính bí mật (Confidentiality):** Đảm bảo chỉ người có thẩm quyền mới truy cập dữ liệu và hệ thống.
    - **Tính toàn vẹn (Integrity):** Đảm bảo dữ liệu không bị sửa đổi bởi bên không có thẩm quyền.
    - **Tính sẵn dùng (Availability):** Đảm bảo tính sẵn sàng (đáp ứng nhanh/kịp thời) của dịch vụ cung cấp cho người dùng thực sự.

**Các biện pháp kiểm soát truy cập:** Có nhiều biện pháp kiểm soát truy cập:

- **Kiểm soát truy cập tuỳ chọn (Discretionary Access Control - DAC):**
    - **Định nghĩa:** Cơ chế hạn chế truy cập đến các đối tượng dựa trên thông tin nhận dạng của chủ thể và/hoặc nhóm chủ thể.
    - **Thông tin nhận dạng:** **Bạn là ai?** (CMND, bằng lái xe, vân tay...), **Những cái bạn biết** (tên truy cập, mật khẩu, số PIN...), **Bạn có gì?** (Thẻ ATM, thẻ tín dụng,...). **Vân tay thuộc thông tin nhận dạng của người dùng**.
    - **Đặc điểm:** Cho phép người dùng cấp hoặc hủy quyền truy cập cho người dùng khác đến các đối tượng thuộc quyền điều khiển của họ.
    - **Chủ sở hữu của các đối tượng (owner of objects) là người có toàn quyền điều khiển các đối tượng này**.
    - **Ví dụ:** Người dùng có quyền tạo, sửa, xóa files trong thư mục riêng và có thể trao/hủy quyền truy cập files của mình cho người khác.
    - **Hai kỹ thuật phổ biến để cài đặt DAC:** Ma trận kiểm soát truy cập (Access Control Matrix - ACM) và Danh sách kiểm soát truy cập (Access Control List - ACL).
        - **ACM:** Mô tả kiểm soát truy cập qua ma trận 2 chiều gồm chủ thể, đối tượng và quyền truy cập.
            - Đối tượng (Objects): Thực thể cần bảo vệ (files, processes).
            - Chủ thể (Subjects): Người dùng, tiến trình tác động lên objects.
            - Quyền truy cập: Hành động Subject thực hiện trên Object (r: read, w: write, x: execute, o: own).
        - **ACL:** Danh sách các quyền truy cập của một chủ thể đối với một đối tượng.
            - Chỉ ra người dùng/tiến trình được truy cập vào đối tượng nào và thao tác cụ thể.
            - Bản ghi điển hình: (subject, operation).
            - Khi yêu cầu truy cập, HĐH kiểm tra ACL. Áp dụng cho một hoặc nhóm đối tượng.
- **Kiểm soát truy cập bắt buộc (Mandatory Access Control - MAC):**
    - **Định nghĩa:** Cơ chế hạn chế truy cập đến đối tượng dựa trên **tính nhạy cảm (sensitivity) của thông tin** và **sự trao quyền chính thức (formal authorization)** cho chủ thể.
    - **Đặc điểm:** **Không cho phép người tạo ra các đối tượng có toàn quyền truy cập**. Quyền truy cập do **người quản trị hệ thống định ra trước trên cơ sở chính sách an toàn thông tin của tổ chức**.
    - **Thường được sử dụng phổ biến trong các cơ quan an ninh, quân đội và ngân hàng**.
    - **Các mức nhạy cảm của thông tin:** Tối mật (Top Secret - T), Tuyệt mật (Secret - S), Mật (Confidential - C), Không phân loại (Unclassified - U).
    - **Ví dụ:** Tài liệu "Mật" chỉ được xem và phổ biến bởi người có trách nhiệm, tác giả không được quyền phổ biến.
- **Kiểm soát truy cập dựa trên vai trò (Role-Based Access Control - RBAC):**
    - Cho phép người dùng truy cập thông tin và hệ thống dựa trên **vai trò (role) của họ trong công ty/tổ chức**.
    - Có thể áp dụng cho một nhóm người dùng hoặc từng người dùng riêng lẻ.
    - Quyền truy cập được tập hợp thành các nhóm "vai trò" với các mức quyền khác nhau.
    - **Liên kết người dùng và vai trò:** Người dùng được cấp "thẻ thành viên" dựa trên năng lực, vai trò, và trách nhiệm. Trong nhóm "vai trò", người dùng được cấp vừa đủ quyền cần thiết. Liên kết có thể tạo/hủy dễ dàng.
    - **Quản lý phân cấp vai trò:** Các vai trò được tổ chức thành cây theo mô hình phân cấp tự nhiên của tổ chức.
    - **Ví dụ:** Trường học chia nhóm Quản lý, Giáo viên, Sinh viên với các quyền truy cập khác nhau.
- **Kiểm soát truy cập dựa trên nhiệm vụ (Task-Based Access Control - TBAC):**
    - Cho phép người dùng truy cập dựa trên **nhiệm vụ (task) họ được giao thực hiện**.
    - **Nhiệm vụ có tính tạm thời hơn so với vai trò**.
- **Kiểm soát truy cập dựa trên luật (Rule-Based Access Control):**
    - Cho phép truy cập dựa trên các **luật (rules) đã được định nghĩa trước**.
    - Các luật có thể thiết lập để cho phép truy cập tài nguyên cho người dùng thuộc một tên miền, một mạng hay một dải địa chỉ IP.
    - **Firewalls/Proxies là ví dụ điển hình** sử dụng tập các luật để kiểm soát truy cập.
    - Thông tin sử dụng trong luật: địa chỉ IP nguồn/đích, phần mở rộng files, địa chỉ IP/tên miền để lọc/chặn website, tập từ khóa để lọc nội dung cấm.
- **Kiểm soát truy cập dựa trên thuộc tính (Attribute-Based Access Control - ABAC):**
    - Còn gọi là kiểm soát truy cập dựa trên chính sách.
    - Quyền của chủ thể được xác định bằng cách đánh giá **các thuộc tính liên quan đến chủ thể, đối tượng, các hoạt động được yêu cầu, và thuộc tính môi trường**.
- **Kiểm soát truy cập dựa trên lưới (Lattice-Based Access Control - LBAC):**
    - Sử dụng ma trận hoặc mạng lưới các chủ thể và đối tượng để gán đặc quyền.
    - Là một ví dụ về NDAC (Non-Discretionary Access Control).

**Các mô hình kiểm soát truy cập:**

- **Mô hình bí mật Bell-LaPadula:**
    - Mô hình bảo mật đa cấp, thường dùng trong quân sự.
    - **Tài liệu được gán mức độ bảo mật** (không phân loại, mật, bí mật, tối mật), người dùng cũng được ấn định cấp độ tương ứng.
    - **Nguyên tắc bảo mật tài nguyên**:
        - **Nguyên tắc đọc xuống:** **Một người dùng ở mức độ bảo mật k chỉ có thể đọc các đối tượng ở cùng mức bảo mật hoặc thấp hơn**. (Ví dụ: Tướng đọc tài liệu của trung úy, nhưng trung úy không đọc được tài liệu của tướng).
        - **Nguyên tắc ghi lên:** **Một người dùng ở mức độ bảo mật k chỉ có thể ghi các đối tượng ở cùng mức bảo mật hoặc cao hơn**. (Ví dụ: Trung úy có thể thêm tin nhắn vào hộp thư chung, nhưng tướng không thể ghi tin nhắn vào hộp thư của trung úy nếu tin nhắn đó chứa thông tin bảo mật cao hơn mức trung úy được phép).
- **Mô hình toàn vẹn Biba:**
    - **Đảm bảo tính toàn vẹn của dữ liệu**.
    - Tính toàn vẹn bị đe dọa khi chủ thể ở mức toàn vẹn thấp ghi vào đối tượng có mức toàn vẹn cao hơn, hoặc chủ thể đọc dữ liệu ở mức toàn vẹn thấp hơn.
    - Áp dụng hai quy tắc:
        - **Không ghi lên:** Chủ thể không thể ghi dữ liệu vào đối tượng có mức toàn vẹn cao hơn.
        - **Không đọc xuống:** Chủ thể không thể đọc dữ liệu có mức toàn vẹn thấp hơn.
    - Tương tự Bell-LaPadula trong việc sử dụng nhãn an ninh nhưng **luồng thông tin được kiểm soát ngược lại**.
    - Chủ thể có yêu cầu an ninh cao không được sử dụng thông tin từ nguồn có độ tin cậy thấp. (Ví dụ: Máy chủ web không tin cậy dữ liệu đầu vào từ nguồn không tin cậy).
- **Mô hình toàn vẹn Clark-Wilson:**
    - Tập trung vào **ngăn chặn người dùng sửa đổi trái phép dữ liệu**.
    - Người dùng không thao tác trực tiếp với đối tượng mà **thông qua một chương trình** hạn chế các thao tác.
    - Tính toàn vẹn dựa trên **nguyên tắc các công việc (thủ tục) được định nghĩa tường minh và việc tách biệt trách nhiệm**.
- **Mô hình kiểm soát truy cập Graham-Denning:**
    - Gồm 3 thành phần: Tập các đối tượng, tập các chủ thể, tập các quyền.
    - Mỗi chủ thể gồm 1 tiến trình và 1 miền (domain).
    - Tập hợp các quyền chi phối cách chủ thể xử lý đối tượng thụ động.
    - Mô tả **8 quyền bảo vệ nguyên thủy** (lệnh) mà chủ thể có thể thực thi: Create object/subject, Delete object/subject, Read/Grant/Delete/Transfer access right.
- **Mô hình Harrison-Ruzzo-Ullman (HRU):**
    - Định nghĩa phương pháp cho phép **thay đổi quyền truy cập, thêm/xóa chủ thể và đối tượng** do hệ thống thường thay đổi theo thời gian.
    - Xây dựng trên ma trận kiểm soát truy cập và gồm tập các quyền chung và tập cụ thể các lệnh.
- **Mô hình Brewer-Nash (Bức tường Trung Hoa - Chinese Wall):**
    - Được thiết kế để **ngăn chặn xung đột lợi ích giữa 2 bên**.
    - Yêu cầu người dùng chọn một trong hai bộ dữ liệu xung đột, sau đó họ không thể truy cập dữ liệu xung đột đó.
    - **Ví dụ:** Công ty luật đại diện cho 2 người trong vụ tai nạn ô tô, luật sư cá nhân không được phép truy cập thông tin riêng tư của cả hai.

**Các dạng phương pháp xác thực:**

- **Xác thực dựa trên mật khẩu (Password-based authentication):**
    - Đơn giản, dễ sử dụng, an toàn thấp. Dễ bị tấn công từ điển, vét cạn.
    - Độ an toàn phụ thuộc vào: **Độ dài mật khẩu, Số loại ký tự sử dụng, Tuổi thọ của mật khẩu**. **Tần suất thay đổi mật khẩu không phải là yếu tố đánh giá độ khó của mật khẩu**.
- **Xác thực đa nhân tố (Multi-factor authentication):**
    - Là phương pháp **kết hợp nhiều nhân tố xác thực người dùng**.
    - Ví dụ: Thẻ ATM + PIN; Vân tay + PIN; Vân tay + Thẻ truy cập + PIN.
    - Độ an toàn cao, nhưng phức tạp và đắt tiền.
- **Xác thực sinh trắc học (Biometric authentication):**
    - Sử dụng các **đặc điểm sinh trắc để nhận dạng và xác thực**.
    - Các đặc điểm thường dùng: Vân ngón tay, Dấu tay/lòng bàn tay, Hình học bàn tay/khuôn mặt, Dấu võng mạc, Mống mắt.
    - **Ba đặc điểm được coi là thực sự duy nhất (unique): Vân ngón tay, Dấu võng mạc, Mống mắt**.
- **Xác thực dựa trên chứng chỉ (Certificate-based authentication):**
    - Sử dụng **chứng chỉ số (digital certificate)** để xác thực người dùng/máy chủ.
    - **Chứng chỉ số là tài liệu số do CA cấp, gồm 3 thông tin chính:** Thông tin định danh của chủ thể, Khóa công khai của chủ thể, Chữ ký số của CA. **Địa chỉ IP của chủ thể không phải là thông tin chính trong chứng chỉ số**.
    - Máy chủ xác minh chữ ký số và cơ quan cấp, dùng mật mã để xác nhận khóa riêng.
- **Xác thực dựa trên mã thông báo (Token-based authentication):**
    - Cho phép người dùng **nhập thông tin xác thực một lần và đổi lại nhận được một chuỗi ký tự ngẫu nhiên được mã hóa duy nhất (mã thông báo)**.
    - Sau đó, người dùng có thể **sử dụng mã thông báo để truy cập các hệ thống được bảo vệ thay vì nhập lại thông tin đăng nhập của mình**.
    - Mã thông báo chứng minh người dùng đã có quyền truy cập.
    - Ví dụ: Giao thức Kerberos.

**Các giao thức xác thực:**

- **PAP (Password Authentication Protocol):**
    - Người dùng gửi username + password, máy chủ kiểm tra và trả lời.
    - **Sử dụng bắt tay hai chiều**.
- **Kerberos:**
    - Giao thức mật mã để xác thực trong mạng máy tính hoạt động trên đường truyền không an toàn.
    - Chống nghe lén, gửi lại gói tin cũ, đảm bảo toàn vẹn dữ liệu.
    - Mục tiêu: mô hình client-server, nhận thực cả hai chiều.
    - Dựa trên mật mã hóa khóa đối xứng và cần bên thứ ba (KDC) tin cậy.
- **LDAP (Lightweight Directory Access Protocol):**
    - Giao thức ứng dụng cho phép truy cập và duy trì dịch vụ thông tin thư mục phân tán qua Internet.
    - Dịch vụ thư mục quan trọng cho ứng dụng mạng nội bộ và Internet (chia sẻ thông tin người dùng, hệ thống, mạng, dịch vụ, ứng dụng).
    - Ví dụ: Active Directory của Windows server sử dụng LDAP.
- **OAuth2:**
    - Giao thức ủy quyền cho phép ứng dụng (Facebook, GitHub) có được **quyền truy cập hạn chế vào tài khoản người dùng trên dịch vụ HTTP**.
    - Ủy quyền xác thực người dùng cho dịch vụ lưu trữ tài khoản, và ủy quyền cho ứng dụng bên thứ ba truy cập tài khoản.
    - Cung cấp luồng ủy quyền cho ứng dụng web, máy tính để bàn, thiết bị di động.
    - **Bốn vai trò:**
        - Chủ sở hữu tài nguyên (Resource owner): Người dùng cho phép ứng dụng truy cập tài khoản.
        - Ứng dụng (Client): Ứng dụng muốn truy cập tài khoản người dùng.
        - **Máy chủ ủy quyền (Authorisation server): Xác minh danh tính người dùng và cấp mã thông báo truy cập cho ứng dụng**.
        - Máy chủ tài nguyên (Resource server): Lưu trữ tài khoản người dùng được bảo vệ.
    - **Luồng giao thức:** Ứng dụng yêu cầu ủy quyền từ **người dùng**. Nếu được cấp, ứng dụng nhận ủy quyền. Ứng dụng yêu cầu mã thông báo từ máy chủ ủy quyền. Máy chủ ủy quyền cấp mã thông báo. Ứng dụng yêu cầu tài nguyên từ máy chủ tài nguyên và xuất trình mã thông báo.
- **SAML (Security Assertion Markup Language):**
    - **Tiêu chuẩn mở cho trao đổi dữ liệu xác thực và ủy quyền giữa các bên**, đặc biệt là giữa nhà cung cấp danh tính và nhà cung cấp dịch vụ.
    - Ngôn ngữ đánh dấu dựa trên XML cho xác nhận bảo mật.
    - Thường được sử dụng trong cơ chế đăng nhập một lần trên trình duyệt web (SSO).
- **RADIUS (Remote Authentication Dial-In User Service):**
    - Giao thức cho phép máy chủ truy cập từ xa liên lạc với máy chủ trung tâm để xác thực người dùng quay số và cho phép truy cập hệ thống/dịch vụ.
    - Xác thực bằng PAP và CHAP.
- **CHAP (Challenge-Handshake Authentication Protocol):**
    - **Sử dụng bắt tay ba chiều để xác minh danh tính người dùng**.
    - Cho phép người dùng từ xa nhận dạng mà không để lộ mật khẩu.
    - Hệ thống xác thực sử dụng bí mật chung (mật khẩu) để tạo giá trị băm mật mã bằng MD5.
    - **Hoạt động:** Máy khách và máy chủ có bí mật chung. Máy chủ gửi thử thách ngẫu nhiên. Máy khách tính hash1 = MD5(challenge + secret) và gửi. Máy chủ tự tính hash2. Nếu hash1 = hash2, xác thực thành công.
- **EAP (Extensible Authentication Protocol):**
    - Giao thức xác thực được thiết kế để **hỗ trợ nhiều phương pháp xác thực**.
    - **Chỉ định cấu trúc của giao tiếp xác thực giữa máy khách và máy chủ xác thực** mà không xác định nội dung dữ liệu xác thực.
    - Các phương pháp hỗ trợ: Thử thách MD5, Mật khẩu một lần, Thẻ token chung, TLS.

---

#### **2. Tường lửa (Firewall)**

**Khái quát về tường lửa:**

- **Định nghĩa:** Là một thiết bị phần cứng hoặc một chương trình phần mềm có chức năng cơ bản là **sàng lọc lưu lượng mạng nhằm mục đích ngăn chặn truy cập trái phép giữa các mạng máy tính** (ví dụ: giữa Internet và mạng nội bộ).
- Có thể là hệ thống máy tính chạy phần mềm, dịch vụ phần mềm trên router/máy chủ, hoặc mạng riêng biệt chứa thiết bị hỗ trợ.
- **Sự phát triển qua các thế hệ:**
    - **Thế hệ 1:** Lọc đơn giản, cho phép/từ chối gói tin ở lớp 3 dựa trên header, hỗ trợ ACL.
    - **Thế hệ 2:** Hỗ trợ giám sát, lọc theo phiên, kết nối (tường lửa có trạng thái), lọc đến lớp 4.
    - **Thế hệ 3:** Hỗ trợ lọc đến lớp 7 (lớp ứng dụng). Một số hỗ trợ UTM.
    - **Thế hệ 4 (NGFW):** Tích hợp hỗ trợ **lọc đa lớp mạng, lọc nội dung, lọc mã độc, lọc lưu lượng mã hóa**.
    - **Thế hệ 5 (ML-Powered NGFW):** NGFW hỗ trợ bởi học máy, sử dụng ML để chủ động phát hiện nhiều dạng tấn công đã biết và chưa biết (kể cả zero-day).
- **Các thuộc tính cần có của tường lửa để đảm bảo hiệu quả**:
    - **Tất cả thông tin trao đổi phải đi qua tường lửa:** Hiệu quả giảm nếu có định tuyến thay thế.
    - **Tường lửa chỉ cho phép lưu lượng truy cập được ủy quyền:** Nếu không thể phân biệt hoặc cấu hình cho phép liên lạc nguy hiểm, tính hữu dụng giảm. Trong tình huống lỗi/quá tải, **phải luôn chuyển sang trạng thái từ chối hoặc đóng** (Thà gián đoạn liên lạc còn hơn để hệ thống không được bảo vệ).
    - **Tường lửa có thể tự chống lại các cuộc tấn công:** Phải có khả năng chống lại tấn công trực tiếp vào chính nó.
- **Điểm mạnh của tường lửa**:
    - Rất hiệu quả trong việc thực thi chính sách bảo mật của công ty.
    - Hạn chế quyền truy cập vào các dịch vụ cụ thể.
    - Mục đích duy nhất, không cần thỏa hiệp giữa bảo mật và khả năng sử dụng.
    - Hỗ trợ tốt việc kiểm toán (ghi nhật ký tất cả lưu lượng đi qua).
    - Nhanh chóng cảnh báo về các sự kiện cụ thể.
- **Điểm yếu của tường lửa**:
    - **Không thể bảo vệ chống lại những gì đã được ủy quyền** (ví dụ: virus trong email mà tường lửa cho phép đi qua).
    - **Chỉ hiệu quả khi các luật được cấu hình chặt chẽ/đầy đủ**.
    - **Không thể ngăn chặn các cuộc tấn công sử dụng kỹ thuật xã hội** hoặc người dùng được ủy quyền cố ý sử dụng quyền truy cập xấu.
    - Không thể khắc phục các vấn đề quản trị kém hoặc chính sách bảo mật thiết kế kém.
    - **Không thể ngăn chặn các cuộc tấn công nếu lưu lượng truy cập không đi qua chúng**. **"Không hỗ trợ kiểm toán" không phải là điểm yếu của tường lửa**.

**Các dạng tường lửa (Firewall Processing Mode):** Các tường lửa hiện đại hầu hết là tường lửa lai (hybrid firewalls).

- **Tường lửa lọc gói (Packet-filtering firewalls):**
    - Kiểm tra thông tin trong **header của các gói tin**.
    - Thường triển khai tại **lớp IP của mạng TCP/IP** để từ chối/cho phép gói tin đi qua dựa trên luật cấu hình.
    - Lọc từng gói tin dựa trên thông tin header: **Địa chỉ IP đích/nguồn, Hướng di chuyển, Giao thức, Cổng TCP/UDP nguồn/đích**. **Nội dung của gói tin không được sử dụng để lọc trong tường lửa lọc gói**.
    - **Các dạng lọc:**
        - **Lọc tĩnh (Static filtering):** Luật lọc được tạo và cài đặt sẵn. Phổ biến dưới dạng router hoặc gateway.
        - **Lọc động (Dynamic filtering):** **Có thể phản ứng với sự kiện mới xuất hiện và cập nhật/tạo luật để xử lý sự kiện đó**. Có thể đóng/mở "cửa" dựa trên thông tin header.
        - **Kiểm tra gói có trạng thái (Stateful packet inspection - SPI):** Giám sát từng kết nối mạng sử dụng bảng trạng thái, theo dõi trạng thái và ngữ cảnh của từng gói trong phiên giao tiếp.
- **Tường lửa lớp ứng dụng (Application layer firewalls):**
    - Còn gọi là cổng ứng dụng (Application gateway) hoặc máy chủ proxy (proxy server, reverse proxy).
    - Thường cài đặt trên máy tính chuyên dụng tách biệt với router lọc/tường lửa mạng.
    - Thường được thiết kế riêng cho từng lớp ứng dụng (web proxy, FTP proxy, mail proxy).
- **Cổng chuyển mạch (Circuit gateways)**.
- **Tường lửa lớp MAC (MAC layer firewalls):**
    - Thiết kế để vận hành ở **lớp con MAC của lớp liên kết dữ liệu**.
    - Thực hiện chức năng lọc dựa trên **địa chỉ MAC của các máy (host)**.
    - Liên kết địa chỉ MAC của máy cụ thể với các mục ACL xác định loại gói được phép, chặn tất cả lưu lượng khác.
- **Tường lửa lai (Hybrid firewalls):**
    - Dạng tường lửa kết hợp một số dạng khác (ví dụ: Lọc gói + dịch vụ proxy; Lọc gói + cổng chuyển mạch).
    - Thường gồm 2 thiết bị tường lửa riêng biệt nhưng kết nối và làm việc song song.
    - **Ưu điểm:** **Cải thiện mức bảo vệ mà không cần thay thế toàn bộ các tường lửa hiện có**.
    - **UTM (Unified Threat Management):** Là một dạng tường lửa lai rất mạnh, kết hợp tính năng của nhiều thiết bị mạng hiện đại.
        - Có khả năng thực hiện tính năng của: Tường lửa SPI, NIDS/NIPS, Bộ lọc nội dung, Bộ lọc spam, Bộ quét và lọc mã độc.
        - **Ưu điểm của UTM:** **Dễ triển khai và cấu hình nhờ việc chỉ cần triển khai 1 UTM để bảo vệ tổng thể**, thay vì nhiều thiết bị. Bảo vệ tốt từ mối đe dọa vòng ngoài đến mối đe dọa sâu trong nội dung.
        - **Nhược điểm của UTM:** Có thể tạo **1 điểm lỗi duy nhất** nếu thiết bị gặp sự cố kỹ thuật (cả hệ thống phụ thuộc vào UTM).

**Kiến trúc triển khai tường lửa:** Cấu hình tốt nhất phụ thuộc vào mục tiêu mạng, khả năng triển khai, và ngân sách. Có 4 cách triển khai phổ biến:

- **Bộ định tuyến lọc gói (Packet-filtering routers):**
    - Thường triển khai ở điểm kết nối mạng nội bộ và mạng ngoài.
    - Router cấu hình để từ chối gói tin không phép.
    - **Ưu điểm:** Đơn giản và hiệu quả để giảm rủi ro tấn công từ bên ngoài.
    - **Hạn chế:** Không hỗ trợ kiểm toán và xác thực mạnh; lọc dựa trên ACL phức tạp có thể làm suy giảm hiệu năng mạng.
- **Tường lửa kép / máy chủ pháo đài (Dual homed firewalls / bastion hosts):**
    - Triển khai tường lửa để bảo vệ phía sau router.
    - Tường lửa triển khai in-line trên đường kết nối mạng ngoài (1 giao diện kết nối với router, 1 giao diện với switch mạng nội bộ).
    - Thường tích hợp NAT, PAT.
- **Tường lửa lọc host (Screened host firewalls):**
    - Kết hợp một router lọc gói và một tường lửa riêng, chuyên dụng (ví dụ: máy chủ proxy ứng dụng).
- **Tường lửa lọc mạng con (Screened subnet firewalls):**
    - Kết hợp 2 hoặc nhiều bastion host đứng sau router lọc gói, mỗi bastion host bảo vệ 1 mạng.

**Lựa chọn và cấu hình tường lửa:**

- **Khi lựa chọn:** Cân nhắc công nghệ phù hợp (bảo vệ vs chi phí), tính năng cơ bản và bổ sung, dễ thiết lập và cấu hình, khả năng thích ứng với mạng đang phát triển.
- **Cấu hình:** Cần cấu hình tập luật riêng cho mỗi tường lửa. Mỗi gói tin/yêu cầu được kiểm tra bằng tập luật để cho phép/từ chối. Mỗi luật cần được tạo, kiểm tra cẩn thận và đưa vào ACL theo đúng trật tự. Tập luật tốt đảm bảo tường lửa tuân thủ chính sách bảo mật.

---

#### **3. Công nghệ mạng riêng ảo (Virtual Private Network - VPN)**

**Khái quát về VPN:**

- **Định nghĩa:** Là một mạng riêng được xây dựng trên nền tảng 1 mạng công cộng như Internet sử dụng các kỹ thuật định tuyến và mật mã.
- **Mục tiêu chính:** **Tạo ra một kênh truyền thông bảo mật thông qua một mạng công cộng**.
- **Các thuộc tính quan trọng:**
    - **Mạng riêng (Private network):** Dữ liệu truyền trong mạng đảm bảo tính riêng tư (bí mật, toàn vẹn, xác thực) bằng kỹ thuật mật mã.
    - **Mạng ảo (Virtual network):** Mạng logic được xây dựng trên nền tảng mạng khác (WAN, Internet) bằng kỹ thuật định tuyến.
- **Kỹ thuật sử dụng:** VPN sử dụng kỹ thuật **tạo đường hầm (tunneling)** để định tuyến lưu lượng mạng riêng. Lưu lượng mạng được mã hóa và đóng gói với header gồm thông tin định tuyến.

**Lợi ích và nhược điểm của VPN:**

- **Ưu điểm:**
    - Giữ an toàn truy cập (bảo mật thông tin, chống lừa đảo, tin tặc).
    - Bảo vệ dữ liệu (mã hóa, gửi qua đường hầm ảo).
    - **Truy cập nội dung bị chặn** (ẩn IP, thay đổi vị trí, truy cập trang web/dịch vụ bị kiểm duyệt).
    - **Tiết kiệm** (giá cả khác nhau giữa các quốc gia, mua dịch vụ VPN rẻ hơn thuê chuyên gia).
    - Bảo mật ở mức chấp nhận được.
    - Bỏ qua bộ lọc và hạn chế truy cập theo địa lý.
    - Ẩn danh và quyền riêng tư trực tuyến.
    - Bảo mật nâng cao: ẩn danh tính, dữ liệu mã hóa.
- **Nhược điểm:**
    - Làm chậm kết nối.
    - VPN có thể ghi lại hoạt động của bạn (tùy nhà cung cấp).
    - Một số dịch vụ trực tuyến chặn truy cập từ VPN.
    - Chi phí (VPN miễn phí thường chậm/hạn chế, cần trả phí cho gói thuê bao).

**Các loại mạng riêng ảo:**

- **Remote Access VPN:** Dùng cho người dùng từ xa kết nối đến mạng riêng (ví dụ: nhân viên kết nối về mạng công ty).
- **Site to Site VPN:** Tạo kết nối riêng giữa 2 mạng qua mạng công cộng (ví dụ: kết nối mạng chi nhánh về trụ sở chính).
    - **Intranet based VPN:** Kết nối mạng các VP của 1 đơn vị.
    - **Extranet based VPN:** Kết nối mạng của đơn vị này với mạng của đơn vị khác.
- **Cloud VPN:** Cho phép người dùng/mạng kết nối VPN đến hạ tầng/dịch vụ đám mây.
- **Mobile VPN:** Cho phép người dùng kết nối VPN đến mạng riêng sử dụng mạng di động.

**Các giao thức mạng riêng ảo:**

- **PPTP (Point-to-Point Tunneling Protocol):**
    - Giao thức mạng cho phép truyền dữ liệu an toàn từ máy khách ở xa đến máy chủ riêng bằng cách tạo VPN trên mạng TCP/IP.
    - Hỗ trợ VPN, đa giao thức, theo yêu cầu trên mạng công cộng.
    - Là mở rộng của PPP (Point-to-Point Protocol).
    - Sử dụng kênh điều khiển TCP và đường hầm GRE để đóng gói gói tin PPP trong IP datagram.
    - Triển khai liên quan 3 máy tính: Máy khách PPTP, Máy chủ truy cập mạng, Máy chủ PPTP.
    - Mã hóa dữ liệu dựa vào PPP, sử dụng hệ mã hóa khóa bí mật. Khóa chung trao đổi dùng RAS (Microsoft MS-RAS hỗ trợ PAP, CHAP, MS-CHAP).
- **L2TP (Layer 2 Tunneling Protocol):**
    - Giao thức tạo đường hầm được sử dụng để tạo VPN.
    - Hoạt động ở lớp mạng 2, chỉ tạo đường hầm, không tích hợp sẵn bảo mật dữ liệu.
    - Sử dụng các giao thức mật mã như IPSec để bảo mật dữ liệu truyền (**L2TP/IPSec VPN**), hoặc PPP (**L2TP/PPP VPN**).
    - Kết hợp tính năng của PPTP (Microsoft) và L2F (Cisco).
    - Hai thành phần đầu cuối: L2TP access concentrator (LAC) và L2TP network server (LNS).
- **OpenVPN:**
    - Giao thức và hệ thống VPN cung cấp kỹ thuật tạo kết nối bảo mật điểm-điểm hoặc mạng-mạng.
    - Bao gồm máy khách và máy chủ VPN.
    - Sử dụng thư viện mật mã OpenSSL và giao thức TLS để bảo mật dữ liệu.
    - Hỗ trợ NAT và tường lửa. Triển khai trên cả phần cứng và phần mềm.
- **WireGuard:**
    - Giao thức truyền thông và phần mềm hỗ trợ VPN bảo mật.
    - Vận hành trên giao thức UDP, thiết kế dễ sử dụng, hiệu năng cao, bề mặt tấn công thấp.
    - Sử dụng nhiều giao thức/thuật toán mật mã: Curve25519 (trao đổi khóa), ChaCha20 (mã hóa/giải mã dữ liệu), Poly1305 (tạo và kiểm tra mã xác thực thông điệp).
- **SSTP (Secure Socket Tunneling Protocol)**.
- **Các giao thức bảo mật dữ liệu (học ở Chương 2):** IPSec, SSL/TLS.

---

#### **4. Honeypot và Honeynet**

**Khái quát:**

- **Honeypot:** Là hệ thống bẫy, mồi nhử được thiết kế để **thu hút kẻ tấn công tiềm năng tránh xa các hệ thống quan trọng**.
- **Honeynet:** Là một tập hợp các hệ thống honeypot kết nối trên một phân đoạn mạng.
- **Đặc điểm:** Honeypot hoặc Honeynet chứa **các dịch vụ giả mô phỏng các dịch vụ thực nhưng được định cấu hình theo cách khiến nó có vẻ dễ bị tấn công**.
- **Mục đích chính:** Sự kết hợp này nhằm mục đích **thu hút những kẻ tấn công lộ diện**. Ý tưởng là một khi các tổ chức đã phát hiện ra những kẻ tấn công này, họ có thể bảo vệ mạng của mình tốt hơn trước các cuộc tấn công trong tương lai nhắm vào tài sản thực.
- **Các nhiệm vụ của honeypot**:
    - Chuyển hướng kẻ tấn công khỏi các hệ thống quan trọng.
    - Thu thập thông tin về hoạt động của kẻ tấn công.
    - Khuyến khích kẻ tấn công ở lại hệ thống đủ lâu để quản trị viên ghi lại sự kiện và có thể phản hồi.

**Phân loại Honeypot:**

- **Theo mục đích sử dụng:** Để nghiên cứu (Research) hoặc để ứng dụng thực tế (Production).
- **Theo mức độ tương tác:** Thuần túy (Pure), Tương tác thấp (Low interaction), Tương tác trung bình (Mid interaction), Tương tác cao (High interaction).
    - **Honeypot thuần túy:** Hệ thống hoàn chỉnh giám sát tấn công thông qua dò lỗi trên liên kết kết nối honeypot với mạng. Không quá phức tạp.
    - **Honeypot mức độ tương tác thấp:** Bắt chước dịch vụ và hệ thống thực để thu hút tội phạm. Thu thập dữ liệu từ các cuộc tấn công mù (botnet, sâu mạng).
    - **Honeypot mức độ tương tác trung bình và cao:** Thiết lập phức tạp, hoạt động giống hạ tầng sản xuất thực. Không hạn chế mức độ hoạt động của tội phạm, cung cấp thông tin chuyên sâu về an ninh mạng. Yêu cầu bảo trì cao, chuyên môn, sử dụng máy ảo để đảm bảo kẻ tấn công không truy cập hệ thống thực.
- **Theo miền chức năng:** Để bẫy thư rác (Spam), cơ sở dữ liệu (Database), mã độc (Malware), hoặc để tạo Honeynet.

**Hạn chế của Honeypot:**

- **Không thể phát hiện các vi phạm bảo mật trong các hệ thống hợp pháp**.
- **Không phải lúc nào cũng xác định được kẻ tấn công**.
- **Có rủi ro là sau khi khai thác thành công honeypot, kẻ tấn công có thể di chuyển ngang để xâm nhập vào mạng sản xuất thực**.
- **Lưu ý:** Để ngăn chặn vấn đề di chuyển ngang, cần **đảm bảo Honeypot được cách ly đầy đủ với mạng sản xuất thực**. **"Dễ dàng ngăn chặn các cuộc tấn công từ chối dịch vụ (DoS)" không phải là hạn chế của honeypot**.

---

Hy vọng cheatsheet này sẽ giúp bạn ôn tập hiệu quả cho bài kiểm tra! Chúc bạn đạt kết quả tốt!