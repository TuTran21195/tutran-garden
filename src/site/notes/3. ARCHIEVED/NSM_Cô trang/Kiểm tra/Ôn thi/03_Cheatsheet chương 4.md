---
{"dg-publish":true,"permalink":"/3-archieved/nsm-co-trang/kiem-tra/on-thi/03-cheatsheet-chuong-4/","created":"2025-06-06T15:24:53.978+07:00"}
---



---

## Cheatsheet Chương 4: Phân tích dữ liệu

Chương 4 này bao gồm 4 nội dung chính: Phân tích gói tin, Mối đe dọa bảo mật và tài nguyên cần bảo vệ, Quy trình phân tích, và Truy tìm các mối đe dọa.

### 1. Phân tích gói tin

- **Khái niệm gói tin**:
    
    - Gói tin là một đơn vị dữ liệu được định dạng và truyền qua mạng.
    - Gói tin là những đơn vị cơ bản nhất để tạo kết nối giữa các máy tính và là bản chất của NSM (Network Security Monitoring).
- **Xâm nhập vào gói tin**:
    
    - Là việc truy cập vào nội dung của gói tin.
    - Có thể sử dụng các lệnh như `tcpdump –nnxr ansm-13-httpget.pcapng` để xử lý file gói tin.
- **Phân tích chi tiết gói tin**:
    
    - Phân tích sâu vào gói tin theo từng giao thức.
    - **Cấu trúc gói tin**: được xây dựng từ dữ liệu tầng ứng dụng, sau đó thêm tiêu đề của các giao thức ở tầng thấp hơn, từ trên xuống dưới. Tiêu đề giao thức cuối cùng thêm vào là của tầng liên kết dữ liệu, và đây là phần thấy đầu tiên. Giao thức liên kết dữ liệu phổ biến nhất là Ethernet.
    - Cần tìm ra độ dài tiêu đề IP và giao thức tiếp theo.
    - Cần xác định độ dài của phần tiêu đề TCP, phụ thuộc vào tập tùy chọn hỗ trợ.
- **Phân tích NSM với Tcpdump**:
    
    - Dữ liệu đầu ra mặc định của tcpdump cung cấp thông tin cơ bản về mỗi gói tin.
    - Định dạng đầu ra có thể khác nhau tùy thuộc giao thức sử dụng.
- **Phân tích NSM với Wireshark**:
    
    - Cho phép **bắt gói tin, lưu vào file và xem lại**.
        - Xem tóm tắt thông tin chung: Statistics/Capture File Properties.
        - Xem cấu trúc giao thức: Statistics/Protocol Hierarchy (Cây giao thức).
        - Xem các thiết bị tham gia: Statistics/Endpoints (Các thiết bị đầu cuối).
        - Xem các luồng giao tiếp: Statistics/Conversations (Các lưu lượng hội thoại).
        - Hiển thị luồng dữ liệu.
        - Đồ thị IO.
        - Trích xuất đối tượng.
        - Sử dụng bộ lọc hiển thị và bắt gói tin.
    - **Lọc gói tin**:
        - Sử dụng **BPF (Berkeley Packet Filter)**:
            - Là cú pháp lọc gói tin phổ biến nhất, sử dụng trong nhiều ứng dụng như tcpdump, Wireshark, tshark.
            - BPF được dùng khi thu thập dữ liệu để loại bỏ dữ liệu không mong muốn, không hữu ích cho việc phát hiện và phân tích.
            - Bộ lọc sử dụng cú pháp BPF gọi là một biểu thức, gồm một hoặc nhiều đơn vị kết hợp bằng các phép toán.
        - **Bộ lọc hiển thị Wireshark**:
            - Chỉ sử dụng trên dữ liệu đã bắt.
            - Sử dụng bộ phân tích giao thức để bắt thông tin về các trường giao thức riêng lẻ.
            - Wireshark hỗ trợ khoảng 1000 giao thức và 141.000 trường giao thức.

### 2. Mối đe dọa bảo mật và tài nguyên cần bảo vệ

- **Thông tin về mối đe dọa bảo mật và tài nguyên cần bảo vệ (Threat Intelligence – TI)**:
    
    - Là thông tin giúp xác định các mối đe dọa bảo mật và đưa ra quyết định đúng đắn.
    - Giúp cập nhật thông tin khổng lồ về mối đe dọa, dự đoán tương lai mối đe dọa, và thông báo nguy hiểm cho người quản lý.
    - **Định nghĩa TI**: "thông tin dựa trên bằng chứng, bao gồm ngữ cảnh, cơ chế, IOC (Indicators of Compromise), các tin tức liên quan về mối đe dọa đối với tài sản – có thể được sử dụng để đưa ra quyết định phản ứng xử lý" (Gartner); "Tập hợp dữ liệu thu thập được, định mức và áp dụng đối với mối đe dọa bảo mật, nhân tố đe dọa, khai thác, mã độc, lỗ hổng và các chỉ số xâm hại" (SANS Institute).
- **Các loại TI**:
    
    - **TI chiến lược**: Liên quan các chiến lược, chính sách, kế hoạch của kẻ tấn công ở mức cao. Thường được thu thập/phân tích bởi chính phủ, quân sự hoặc các tổ chức lớn. Sản phẩm có thể là tài liệu chính sách, thuyết chiến tranh.
    - **TI khai thác**: Liên quan cách kẻ tấn công lập kế hoạch và hỗ trợ mục tiêu chiến lược. Tập trung mục tiêu hẹp, ngắn hạn. Thường dùng trong chính phủ hoặc quân sự.
    - **TI chiến thuật**: Liên quan các hành động cụ thể khi tiến hành hoạt động. Đi sâu vào công cụ, chiến thuật, thủ tục của kẻ tấn công. Là nơi các doanh nghiệp thực hiện NSM tập trung nỗ lực. Gồm các chỉ báo tấn công (địa chỉ IP, tên file, chuỗi văn bản). Thông tin này thường tạm thời và nhanh chóng lỗi thời.
- **Chu trình thu thập thông tin về các mối đe dọa NSM (Intelligence Cycle)**:
    
    - Một khung làm việc gồm **6 bước**:
        - **Bước 1: Xác định yêu cầu**: Đặt câu hỏi cụ thể để tạo ra thông tin (ví dụ: mẫu giao tiếp bình thường, giao tiếp với thực thể ngoài, dịch vụ thường cung cấp, tỷ lệ giao tiếp trong-ngoài). Hoặc câu hỏi theo tình huống cho điều tra cụ thể (ví dụ: máy tính nguy hại từng liên lạc máy cần bảo vệ không, đăng ký ISP độc hại không, nội dung lưu lượng so với hoạt động độc hại đã biết).
        - **Bước 2: Lập kế hoạch**: Đảm bảo hoàn thành các bước, lập kế hoạch và gán tài nguyên.
        - **Bước 3: Thu thập**: Thực hiện thu thập thông tin theo yêu cầu. Dữ liệu thường từ các nguồn NSM sẵn có như FPC (Full Packet Capture) hay dữ liệu phiên.
        - **Bước 4: Xử lý**: Chuyển dữ liệu thu thập thành dạng hữu ích hơn, dễ đọc hơn cho phân tích.
        - **Bước 5: Phân tích**: Kiểm tra, xem xét mối liên hệ, đưa ngữ cảnh cho dữ liệu đã xử lý để làm cho chúng có ích. Biến dữ liệu rời rạc thành sản phẩm hoàn thiện cho ra quyết định.
        - **Bước 6: Truyền đi**: Truyền các sản phẩm thông tin tới các cá nhân hoặc nhóm đã đưa ra yêu cầu thu thập. (Lưu ý: thường chuyên gia phân tích NSM tự tạo sản phẩm TI để dùng).
- **Tạo thông tin về tài nguyên cần bảo vệ**:
    
    - Cần thiết để hiểu rõ môi trường cần bảo vệ.
    - Bao gồm lịch sử, thực trạng và xác định mô hình tài nguyên mạng.
    - Công cụ hỗ trợ: PRADS (Passive Real-time Asset Detection System).
- **Tạo thông tin về mối đe dọa bảo mật**:
    
    - TI tập trung vào các bộ phận có thể gây hại, thu thập dữ liệu hỗ trợ ra quyết định.
    - **Nghiên cứu về các máy trạm không tin cậy**:
        - Nguồn dữ liệu nội bộ: Máy không tin cậy từng liên lạc máy tin cậy không? Bản chất kết nối? Từng liên lạc máy tin cậy khác trên mạng không?.
        - Thông tin mã nguồn mở: Thu thập từ các nguồn công khai, xem danh tiếng địa chỉ IP và tên miền.
    - **Nghiên cứu về các tệp tin không tin cậy**:
        - Thông tin về tệp tin dùng xây dựng TI chiến thuật.
        - Có thể trích xuất tệp tin đáng nghi trong thời gian thực (ví dụ: dùng Zeek).
        - Sử dụng Wireshark nếu truy cập toàn bộ dữ liệu.
        - Sử dụng các trang web phân tích mã độc trực tuyến (ví dụ: Cuckoo sandbox, Malwr sandbox).

### 3. Quy trình phân tích

- **Các phương pháp phân tích**:
    
    - **Điều tra quan hệ (Relational Analysis)**:
        - Tốt trong tình huống phức tạp, nhiều máy tính tham gia, theo dõi lượng lớn thực thể và mối quan hệ.
        - **Các bước**:
            - **Bước 1**: Điều tra các đối tượng chính và thực hiện điều tra sơ bộ về các cảnh báo (ví dụ: từ IDS). Kiểm tra luật/cơ chế gây cảnh báo, xác định dương tính giả, thu thập thông tin đối tượng chính (IP tin cậy, nguy hiểm).
            - **Bước 2**: Điều tra mối quan hệ chính và tương tác hiện tại. Hỏi về lịch sử liên lạc, cổng, giao thức, dịch vụ liên quan. Điều tra kỹ lưỡng các kết nối gắn với cảnh báo ban đầu, lấy dữ liệu từ nhiều nguồn.
            - **Bước 3**: Điều tra các đối tượng thứ cấp và mối quan hệ. (Ví dụ: máy cần bảo vệ giao tiếp máy nguy hại khác, phân tích tệp độc hại cho IP liên lạc nghi vấn).
            - **Bước 4**: Điều tra bổ sung về quan hệ của các đối tượng. Lặp lại khi cần (mức ba, bốn), đánh giá đầy đủ từng mức trước khi chuyển sang mức kế tiếp. Kết thúc, mô tả mối quan hệ và hoạt động độc hại.
    - **Chẩn đoán khác biệt (Differential Diagnosis)**:
        - Làm việc tốt trong tình huống ít máy tính liên quan, gắn với vài dấu hiệu khác biệt.
        - Phân loại cảnh báo, điều tra nguồn dữ liệu để kiểm tra liên quan, xem có vi phạm an ninh không.
        - **Các bước**:
            - **Bước 1**: Xác định và liệt kê các dấu hiệu.
            - **Bước 2**: Xem xét và đánh giá chẩn đoán phổ biến nhất đầu tiên.
            - **Bước 3**: Liệt kê tất cả chẩn đoán có thể cho các dấu hiệu đã biết.
            - **Bước 4**: Đánh giá mức ưu tiên trong danh sách ứng viên theo mức độ nghiêm trọng.
            - **Bước 5**: Loại bỏ các điều kiện ứng viên, bắt đầu với cái nghiêm trọng nhất.
- **Các quy chuẩn thực tiễn cho phân tích**:
    
    - Luôn đặt ra các giả định.
    - Cần lưu ý về dữ liệu.
    - Nên làm việc theo nhóm.
    - Không bao giờ đánh động tin tặc.
    - Gói tin vốn dĩ là vô hại.
    - Wireshark chỉ là một công cụ phân tích.
    - Cần thực hiện phân loại sự kiện rõ ràng.
    - Quy tắc 10.

### 4. Truy tìm các mối đe dọa (Threat Hunting)

- Là hoạt động **chủ động đào sâu tìm kiếm các mối đe dọa mạng đang rình rập** mà không bị phát hiện.
- Dựa trên những thông tin nhận biết hiện có.
- **Lợi ích**: Tối đa hóa chi phí bảo mật, phát hiện sai lệch so với hoạt động bình thường, phát hiện lỗi, phát hiện sớm kẻ tấn công, kiểm soát thiệt hại hiệu quả, giảm thời gian dừng hệ thống.
- Có thể xác định đường cơ sở cho lưu lượng dữ liệu mạng (tốc độ, trang web thường dùng, mẫu luồng dữ liệu).
- Tận dụng sự hiểu biết về hoạt động bình thường của người dùng.
- **Các điểm cần chú ý khi truy tìm**:
    - Từ chối của tường lửa ngoại vi.
    - Các liên lạc ra ngoài thuộc danh sách cần theo dõi.
    - Giao tiếp với thiết bị bất thường.
    - Lưu lượng truy cập bị Web Proxy chặn.
- Có thể ánh xạ với khung làm việc MITRE ATT&CK.
