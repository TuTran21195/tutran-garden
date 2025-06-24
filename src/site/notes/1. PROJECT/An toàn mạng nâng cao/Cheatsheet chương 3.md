---
{"dg-publish":true,"permalink":"/1-project/an-toan-mang-nang-cao/cheatsheet-chuong-3/","title":"Cheatsheet chương 3","tags":["cheatsheet"],"created":"2025-06-24T20:04:02.890+07:00"}
---



# Cheetsheet - Prompt 1
Chào bạn, tôi đã chuẩn bị một bản tóm tắt chi tiết ("cheatsheet") cho Chương 3 – Bảo mật cho các hệ thống mạng, bao gồm các khái niệm, rủi ro và giải pháp bảo mật chính. Hy vọng tài liệu này sẽ giúp bạn ôn tập hiệu quả cho bài kiểm tra sắp tới.

---

### **CHEATSHEET CHƯƠNG 3: BẢO MẬT CHO CÁC HỆ THỐNG MẠNG**

Chương này tập trung vào các kỹ thuật và công nghệ đảm bảo an toàn mạng, bao gồm kiểm soát truy cập, tường lửa, VPN và honeypot/honeynet.

---

#### **1. BẢO MẬT CHO MẠNG CỤC BỘ (LAN)**
Mạng cục bộ (LAN) có phạm vi hẹp, thường trong một tòa nhà hoặc một gia đình, sử dụng kết nối có dây (UTP Cat5) hoặc không dây (WLAN).

**1.1. Khái quát về mạng LAN**
*   **Định nghĩa:** Mạng có phạm vi hẹp trong một địa điểm vật lý, kết nối các thiết bị.
*   **Phương tiện kết nối:**
    *   Có dây: Cáp UTP Cat5 (10Mb/s, 100Mb/s, 1000Mb/s).
    *   Không dây (WLAN): Chuẩn 802.11g, 802.11n, 802.11ax với các tần số và tốc độ khác nhau.
*   **Thành phần chính:**
    *   Giao thức: Ethernet.
    *   Phần cứng: Cáp, Switch, NIC, Router.
    *   Phần mềm: Máy chủ LAN (Windows, Unix, Linux), máy khách LAN, máy chủ DHCP, DNS, file.
*   **Ứng dụng:** Quản lý cơ quan/tổ chức, chia sẻ file/máy in, lưu trữ dữ liệu, sao lưu, truyền thông nội bộ, truy cập từ xa (qua VPN/Radius).
*   **Ưu điểm:**
    *   **Tốc độ truyền dữ liệu nhanh** (100Mb/s - 1000Mb/s).
    *   Chia sẻ tài nguyên, quản lý tập trung.
    *   Tương đối dễ cài đặt và tăng cường hợp tác.
    *   Độ tin cậy cao và có thể đạt **bảo mật cao** nếu được cấu hình đúng.
*   **Hạn chế:**
    *   Giới hạn về phạm vi địa lý và khả năng mở rộng.
    *   Chi phí cài đặt và bảo trì có thể cao.
    *   **Vấn đề bảo mật nếu thiết bị không được quản lý tốt** (dễ bị mã độc, xâm nhập, truy cập vật lý trái phép).

**1.2. Các rủi ro bảo mật mạng LAN**
*   **Truy cập trái phép:** Xem, sửa đổi, đánh cắp dữ liệu nếu có quyền truy cập vật lý.
*   **Phần mềm độc hại và vi-rút:** Lây lan trên mạng.
*   **Mối đe dọa nội bộ:** Nhân viên lạm dụng đặc quyền (cố ý hoặc vô ý).
*   **Mật khẩu yếu:** Kẻ tấn công dễ dàng truy cập.
*   **Dịch vụ mạng dễ bị tổn thương:** Chia sẻ tệp, dịch vụ máy tính từ xa có lỗ hổng.
*   **Tấn công từ chối dịch vụ (DoS):** Gây tắc nghẽn hoặc gián đoạn dịch vụ.
*   **Cấu hình vận hành lỗi:** Thiết bị mạng (router, tường lửa) cấu hình sai tạo điểm yếu.
*   **Thiếu giám sát mạng:** Khó phát hiện và ứng phó kịp thời các sự cố.

**1.3. Các biện pháp bảo mật mạng LAN**
*   **Triển khai và cấu hình tường lửa:** Tuyến phòng thủ đầu tiên, cần cập nhật thường xuyên.
*   **Cập nhật bộ định tuyến:** Giảm thiểu lỗ hổng đã biết.
*   **Sử dụng VPN:** Mã hóa lưu lượng mạng, hữu ích khi truy cập từ xa.
*   **Thiết lập phân đoạn mạng (VLAN):** Tách biệt máy trạm, kiểm soát truy cập hiệu quả hơn.
*   **Điểm truy cập an toàn:** Chỉ cho phép người dùng được ủy quyền kết nối (ví dụ: lọc địa chỉ MAC).
*   **Bảo vệ khỏi phần mềm độc hại:** Cài đặt và cập nhật chương trình chống vi-rút cho tất cả thiết bị.
*   **Duy trì HĐH được cập nhật:** Vá các lỗ hổng đã biết.
*   **Thiết lập môi trường DMZ (DeMilitarized Zone):** Lớp bảo vệ bổ sung giữa LAN và Internet.
*   **Giám sát lưu lượng mạng:** Phát hiện hoạt động đáng ngờ hoặc truy cập trái phép.

---

#### **2. BẢO MẬT CHO MẠNG WLAN (WIRELESS LAN)**
WLAN được thiết kế để thay thế/bổ sung cho mạng LAN có dây, cho phép các thiết bị kết nối không dây trong phạm vi nhất định.

**2.1. Khái quát về mạng WLAN**
*   **Định nghĩa:** Mạng không dây được thiết kế thay thế/bổ sung cho LAN.
*   **Chuẩn kết nối:** IEEE 802.11 (Wi-Fi).
*   **Thành phần chính:** Access Point (AP) và các máy khách với card giao tiếp không dây.
*   **Nhiệm vụ của AP:**
    *   Đóng vai trò "trạm gốc" trong mạng không dây (nhận và chuyển tín hiệu giữa các máy khách).
    *   Đóng vai trò "cầu nối" giữa mạng có dây và mạng không dây, cho phép truy cập lẫn nhau.

**2.2. Các dạng tấn công vào WLAN**
*   **WLAN doanh nghiệp:**
    *   **Rogue AP (AP giả mạo):** AP trái phép cài đặt trong mạng, cho phép kẻ tấn công bỏ qua tường lửa và truy cập trực tiếp LAN.
    *   **Evil Twin (AP song sinh):** AP do kẻ tấn công cài đặt để bắt chước AP được ủy quyền, chặn bắt thông tin người dùng.
    *   **Chặn bắt dữ liệu không dây:** Nghe lén và chặn bắt tín hiệu trong vùng phủ sóng.
    *   **Tấn công phát lại không dây:** Sử dụng "AP song sinh" để lừa người dùng, bắt và chuyển lưu lượng (tấn công người đứng giữa).
    *   **Tấn công DoS không dây:**
        *   RF jamming: Sử dụng sóng radio gây lỗi/phá sóng của AP.
        *   Khai thác lỗ hổng trong chuẩn 802.11 (ví dụ: gửi deauthentication/disassociation frame giả mạo để ngắt kết nối máy khách).
*   **WLAN gia đình:** Đánh cắp dữ liệu, đọc dữ liệu truyền, chèn mã độc, tải nội dung độc hại.

**2.3. Các lỗ hổng của chuẩn bảo mật không dây IEEE**
*   **Wired Equivalent Privacy (WEP):**
    *   Thiết kế để mã hóa lưu lượng, sử dụng khóa chia sẻ và vector khởi tạo (IV) 24 bit.
    *   **Lỗ hổng:**
        *   Kích thước khóa nhỏ (40/104 bit) dễ bị vét cạn.
        *   IV 24 bit lặp lại nhanh chóng (sau chưa đầy 7 giờ với tốc độ 11 Mbps), tạo ra mẫu dễ bị phát hiện và phá mã hóa.
*   **Wi-Fi Protected Setup (WPS):**
    *   Cấu hình bảo mật WLAN tùy chọn qua PIN hoặc nhấn nút.
    *   **Lỗ hổng (phương thức PIN):**
        *   Không giới hạn số lần nhập PIN.
        *   Ký tự PIN cuối cùng chỉ là tổng kiểm tra.
        *   Router báo cáo tính hợp lệ của hai nửa PIN riêng biệt, giảm độ phức tạp tấn công.
*   **MAC address filtering (Lọc địa chỉ MAC):**
    *   Chỉ thiết bị có địa chỉ MAC trong danh sách mới được kết nối.
    *   **Lỗ hổng:**
        *   **Giám sát và giả mạo MAC:** Địa chỉ MAC trao đổi không mã hóa, dễ dàng bị kẻ tấn công nhìn thấy và giả mạo.
        *   Khó khăn trong quản lý số lượng lớn địa chỉ MAC.
*   **Disable SSID broadcasting (Tắt phát sóng SSID):**
    *   Ẩn tên mạng để người dùng phải nhập thủ công.
    *   **Lỗ hổng:**
        *   SSID vẫn có thể dễ dàng bị phát hiện trong các khung quản lý khác do AP gửi (bằng phân tích giao thức).
        *   Gây khó khăn cho người dùng khi chuyển vùng.
        *   Không phải tất cả các AP đều cho phép tắt báo hiệu SSID.

**2.4. Các giải pháp bảo mật mạng WLAN**
*   **Wi-Fi Protected Access (WPA):**
    *   Thiết kế để thay thế WEP mà không cần nâng cấp phần cứng.
    *   Chế độ: WPA Cá nhân (gia đình, văn phòng nhỏ) và WPA Doanh nghiệp (tổ chức lớn).
    *   Giải quyết vấn đề: **Mã hóa (TKIP)** và **Xác thực toàn vẹn (MIC)**.
    *   **Giao thức Temporal Key Integrity Protocol (TKIP):**
        *   Kích thước khóa tối thiểu 128 bit (so với 64 bit của WEP).
        *   Kích thước IV là 48 bit (so với 24 bit của WEP).
        *   Tạo "khóa cơ sở" duy nhất cho mỗi thiết bị và sử dụng nó với IV để tạo khóa duy nhất cho mỗi gói tin.
    *   **Preshared Key (PSK) Authentication (trong WPA cá nhân):**
        *   Khóa bí mật được chia sẻ thủ công giữa AP và máy khách.
        *   **Điểm yếu:** Khó giữ bí mật, khó quản lý nhiều máy khách, khóa có thể yếu, nhập thủ công.
    *   **Lỗ hổng của WPA:**
        *   Quản lý khóa: Phân phối thủ công không an toàn, mọi người có PSK đều được xác thực, khó thay đổi khóa định kỳ.
        *   Mật khẩu/Passphrase: Khóa PSK yếu nếu người dùng chọn ngắn hoặc dễ đoán.
*   **Wi-Fi Protected Access 2 (WPA2):**
    *   Thiết kế thay thế WPA theo chuẩn 802.11i, tăng cường an toàn.
    *   Chế độ: WPA2 Cá nhân và WPA2 Doanh nghiệp.
    *   Giải quyết vấn đề: **Mã hóa (AES-128, AES-192, AES-256)** và **Xác thực**.
    *   **Giao thức mã hóa:** Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP) với AES (thường gọi CCMP-AES).
    *   **Xác thực người dùng trong WPA2 Enterprise:** Sử dụng chuẩn IEEE 802.1x với giao thức **EAP (Extensible Authentication Protocol)**, hỗ trợ LEAP và PEAP.

---

#### **3. BẢO MẬT CHO MẠNG INTRANET**
Intranet là hệ thống mạng riêng của tổ chức để chia sẻ thông tin và tài nguyên.

**3.1. Khái quát về Intranet**
*   **Định nghĩa:** Hệ thống mạng riêng của tổ chức, doanh nghiệp để chia sẻ thông tin và tài nguyên tính toán.
*   **Các nền tảng điển hình:** Microsoft SharePoint, Google Workspace, Facebook Workplace, HCL Connections, Zoho Connect, HyperOffice Atlas.
*   **Tính năng:** Quản lý tài liệu, công cụ cộng tác, tin tức/thông báo, thư mục nhân viên, đào tạo, nguồn lực nhân sự, dịch vụ hỗ trợ.
*   **Ưu điểm:**
    *   Chi phí truyền dữ liệu rất thấp.
    *   Dễ dàng lấy dữ liệu mọi lúc mọi nơi.
    *   Rất dễ tìm hiểu và sử dụng.
    *   Điểm trung tâm trao đổi email, lưu trữ/tải file.
    *   Kết nối nhân viên, tài liệu được **bảo mật hơn so với Internet**.
*   **Hạn chế:**
    *   Chi phí triển khai thường cao.
    *   Nhân viên cần đào tạo.
    *   Có thể bị quá tải dữ liệu.
    *   **Vẫn còn điểm yếu/lỗ hổng bảo mật**.

**3.2. So sánh Intranet, Extranet và Internet**
*   **Intranet:** Mạng máy tính riêng, chỉ người và hệ thống được ủy quyền truy cập (qua LAN hoặc VPN), có số lượng người dùng cụ thể.
*   **Extranet:** Là Intranet cấp quyền truy cập cho người bên ngoài tổ chức (khách hàng, nhà cung cấp, đối tác) vào một số thông tin/ứng dụng nhất định.
*   **Internet:** Mạng công cộng, ai cũng có thể truy cập, không giới hạn người dùng, nhưng **dễ bị tấn công hơn** so với Intranet và Extranet.

**3.3. Các đe dọa bảo mật đối với Intranet**
*   **Mối đe dọa nội bộ:**
    *   **Nhân viên có lỗi hoặc sơ suất:** Mật khẩu yếu, truy cập từ thiết bị/mạng không bảo mật.
    *   **Mối đe dọa nội gián:** Người thân cận với tổ chức (nhân viên, đối tác) lạm dụng quyền truy cập trái phép.
    *   **Rò rỉ dữ liệu:** Vô tình làm rò rỉ thông tin nhạy cảm (email sai địa chỉ, chia sẻ file không bảo mật, đăng dữ liệu lên nền tảng công cộng).
*   **Các mối đe dọa từ bên ngoài:**
    *   **Xâm nhập:** Từ tin tặc hoặc phần mềm độc hại (sâu, virus).
    *   **Chặn dữ liệu trong quá trình truyền tải:** Nếu sử dụng giao thức không an toàn (HTTP) và không mã hóa.
    *   **Tấn công lừa đảo (Phishing):** Lừa nhân viên tiết lộ thông tin đăng nhập để truy cập Intranet.

**3.4. Các giải pháp bảo mật Intranet**
*   **Tạo chính sách bảo mật rõ ràng:** Quy định về mật khẩu mạnh (chữ hoa, số, ký tự đặc biệt, dài 10-12 ký tự), cấm/kiểm soát thiết bị cá nhân truy cập Intranet.
*   **Tăng cường an toàn cho các giao thức đăng nhập:** Triển khai chính sách mật khẩu mạnh, sử dụng các giao thức an toàn như LDAP, SSO, Active Directory (AD).
*   **Sử dụng kiểm soát truy cập nghiêm ngặt:** Giới hạn quyền truy cập dữ liệu của từng nhân viên dựa trên vai trò và trách nhiệm (ví dụ: kỹ sư QA không truy cập hồ sơ bảng lương).
*   **Mã hóa dữ liệu:**
    *   Bước cơ bản và quan trọng.
    *   Dữ liệu truyền: Sử dụng **HTTPS**.
    *   Dữ liệu lưu trữ (trong CSDL): Sử dụng mã hóa (ví dụ: thuật toán AES).
    *   Sử dụng **chứng chỉ SSL/TLS** cho máy chủ để xác thực và đảm bảo liên lạc an toàn.
*   **Đảm bảo tuân thủ các tiêu chuẩn bảo mật và quy định của chính quyền:** (Ví dụ: PCI DSS, FISMA, HIPAA, SOX, SAS 70 II).
*   **Cẩn trọng với sự tích hợp của bên thứ ba:** Đảm bảo công cụ bên thứ ba được bảo vệ tốt, ví dụ API cung cấp điểm cuối an toàn.

---

#### **4. MẠNG DI ĐỘNG VÀ VẤN ĐỀ BẢO MẬT**
Bảo mật thiết bị và thông tin trên các mạng di động là một thách thức lớn.

**4.1. Khái quát về các mạng di động**
*   **Các dạng mạng không dây:** Mạng cảm biến, IoT, WLAN, **Mạng thông tin di động (Mobile/Cellular network)**.
*   **Các thế hệ mạng di động:** CDMA/TDMA, GSM, 2G, 3G (UMTS), 4G/4G LTE, 5G, 6G.
*   **Hệ điều hành di động:** Google Android, Apple iOS, BlackBerry OS, Sailfish OS, Firefox OS, Tizen, Microsoft Windows Phone.
*   **Dạng thiết bị di động:** Laptop, Tablet, PDA, Smartphone, Thiết bị đeo được (smartwatch, smart band, AR glasses).

**4.2. Các đe dọa đối với thiết bị di động**
*   **Đe dọa vật lý:** Mất hoặc bị trộm cắp thiết bị.
*   **Đe dọa đến từ hệ điều hành:**
    *   Jailbreaking (iOS) / Rooting (Android): Giành quyền truy cập toàn bộ.
    *   DroidDream (mã độc Android khai thác lỗ hổng để giành root access).
    *   Tấn công cập nhật: Phiên bản đầu sạch, phiên bản nâng cấp tích hợp mã độc.
    *   Mã độc quảng cáo.
*   **Đe dọa đến từ ứng dụng:** Phần mềm độc hại, phần mềm gián điệp, chức năng đe dọa tính riêng tư (ví dụ: theo dõi vị trí GPS), ứng dụng chứa lỗ hổng.
*   **Đe dọa đến từ web:** Phishing, Drive-by downloads, khai thác lỗ hổng trình duyệt/trình xử lý file (PDF, Flash).
*   **Đe dọa đến từ mạng:** Kết nối mạng công cộng (Wi-Fi), tấn công DoS/DDoS, khai thác lỗ hổng giao thức/ứng dụng từ mạng.

**4.3. Các dạng tấn công vào thiết bị/người dùng di động**
*   Denial of Service (DDoS).
*   Phone Hacking.
*   Mobile Malware/Virus.
*   Spyware.
*   Exploit.
*   Everything Blue (mã độc khai thác Bluetooth).
*   Social engineering (Phishing, Smishing, Vishing).

**4.4. Các giải pháp bảo mật thiết bị di động**
*   Khóa các tính năng không sử dụng.
*   Khóa màn hình (thủ công, tự động).
*   Sử dụng mã hóa dữ liệu nhạy cảm.
*   Kiểm soát truy cập (thông tin truy cập khi màn hình khóa/mở).
*   Quản lý ứng dụng và thiết bị (xóa/khóa thiết bị mất/trộm).
*   Sử dụng các ứng dụng bảo mật.

---

#### **5. IOT VÀ VẤN ĐỀ BẢO MẬT**
Internet of Things (IoT) là mạng Internet của vạn vật/mọi vật, nơi các đối tượng được kết nối và trao đổi thông tin.

**5.1. IoT là gì?**
*   **Định nghĩa:** Mạng toàn cầu của các đối tượng (objects) được kết nối với nhau, trang bị cảm biến, bộ truyền động, RFID, có địa chỉ đơn nhất và giao tiếp bằng các giao thức chuẩn trong môi trường mạng hỗn hợp.
*   **IoE (Internet of Everything):** Gồm 4 thành phần cơ bản: Things (IoT), Data (dữ liệu), Process (tiến trình), People (con người).

**5.2. Lợi ích của IoT**
Mang lại lợi ích cho hầu hết các lĩnh vực:
*   Y tế từ xa (Telemedicine, healthcare).
*   Giám sát cá nhân/vật nuôi.
*   Nông nghiệp (cảm biến độ ẩm, nhiệt độ).
*   Giao thông (tối ưu hóa vận chuyển).
*   Sử dụng năng lượng hiệu quả.
*   Kết nối và điều khiển vật dụng hàng ngày.
*   Quản lý tòa nhà, an ninh.
*   Nhà thông minh và thành phố thông minh.
*   Hệ thống M2M (Machine to Machine) và cảm biến không dây.
*   Thiết bị, cảm biến nhúng trong thiết bị di động.

**5.3. Kiến trúc tham chiếu của IoT**
*   **Các lớp chính:**
    *   **Lớp thiết bị (Devices):** Nhiều loại thiết bị kết nối trực tiếp/gián tiếp Internet (wifi, ethernet, ZigBee, Bluetooth), mỗi thiết bị có UUID duy nhất.
    *   **Lớp truyền thông (Communications):** Kết nối giữa các thiết bị và với đám mây, sử dụng các giao thức phổ biến như HTTP/HTTPS, MQTT, CoAP.
    *   **Lớp tập hợp/bus (Aggregation/Bus layer):** Hỗ trợ máy chủ HTTP/MQTT, tập hợp và định tuyến giao tiếp từ các thiết bị, cầu nối giữa các giao thức.
    *   **Lớp xử lý và phân tích sự kiện (Event Processing and Analytics):** Nhận sự kiện từ bus, xử lý và hành động, lưu dữ liệu vào CSDL.
    *   **Lớp truyền thông ngoài (Client/external communications):** Hỗ trợ truyền thông với thế giới bên ngoài qua ứng dụng web/portal, dashboard, API.
    *   **Lớp quản lý thiết bị (Device manager):** Gồm Device manager và Device management agents, quản lý thiết bị ở các mức không quản lý, bán phần, đầy đủ.
    *   **Lớp quản lý danh tính và truy nhập (Identity and access management - IAM):** Cung cấp dịch vụ OAuth2 token, SAML2 SSO, OpenID Connect, XACML PDP, quản lý người dùng (LDAP), quản lý chính sách điều khiển truy cập.

**5.4. Các công nghệ nền tảng của IoT**
*   **Radio-frequency identification (RFID):** Nhận dạng tự động và giám sát/theo dõi đồ vật sử dụng sóng vô tuyến, tương tự ZigBee nhưng năng lực lớn hơn.
*   **Sensor technologies (Công nghệ cảm biến):** Thành phần cốt lõi, triển khai khắp nơi (dưới da, gắn đồ vật/máy móc), đo thông số môi trường/tình trạng đồ vật (nhiệt độ, ánh sáng, áp suất, hóa học, sinh học...).
*   **Smart technologies (Công nghệ thông minh):** Vật liệu/đồ vật thông minh tích hợp cảm biến, bộ điều khiển (smartphone, smart TV, smart homes, xe thông minh, robot).
*   **Nano-technology (Công nghệ na nô):** Cho phép thiết bị nhỏ hơn và hiệu quả hơn.

**5.5. Các thách thức đối với IoT**
*   **Vấn đề chuẩn hóa và hài hòa:** Khó khăn do quá nhiều nhà sản xuất và loại thiết bị đặc thù.
*   **Vấn đề riêng tư của người dùng:** Dữ liệu cá nhân (hành vi, sức khỏe) thu thập có thể bị lạm dụng; cần cân bằng giữa lợi ích và nguy cơ.
*   **Các vấn đề về xã hội và đạo đức:** Lạm dụng giám sát, theo dõi (hình ảnh, thói quen, truyền thông); nhiều thiết bị có khả năng thay thế năng lực con người (cảm nhận, trí nhớ, giao tiếp).
*   **Vấn đề dữ liệu lớn (Big Data):** Dữ liệu từ cảm biến/giám sát rất lớn, cần phương pháp/nền tảng xử lý hiệu quả.

**5.6. Các nguy cơ đối với IoT**
*   **IoT Data Privacy (Tính riêng tư dữ liệu trong IoT):** Dữ liệu cá nhân/công ty bị đánh cắp/lạm dụng/phá hủy; nguy cơ tấn công mạng.
*   Identity theft.

**5.7. Các biện pháp bảo mật IoT**
*   **Đổi mật khẩu mặc định** cho các thiết bị IoT.
*   **Tách mạng của đơn vị khỏi mạng/thiết bị IoT** khi có thể.
*   Hạn chế truy cập Internet không cần thiết đối với các thiết bị IoT.
*   Kiểm soát quyền truy cập của nhà cung cấp vào thiết bị IoT.
*   Sử dụng trình quét lỗ hổng mạng IoT.
*   Sử dụng **Kiểm soát truy cập mạng (NAC)**.
*   **Cập nhật phần mềm** thường xuyên.

---
Chúc bạn học tốt và đạt kết quả cao trong bài kiểm tra!