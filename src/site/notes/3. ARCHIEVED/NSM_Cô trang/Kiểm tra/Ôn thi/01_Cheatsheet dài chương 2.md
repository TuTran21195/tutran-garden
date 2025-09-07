---
{"dg-publish":true,"permalink":"/3-archieved/nsm-co-trang/kiem-tra/on-thi/01-cheatsheet-dai-chuong-2/","created":"2025-05-30T01:05:52.000+07:00"}
---


**CHEATSHEET: CHƯƠNG 2 - THU THẬP DỮ LIỆU TRONG NSM**

Chương 2 tập trung vào các vấn đề liên quan đến **thu thập dữ liệu trong chu trình NSM**. Nó giới thiệu về phương pháp thu thập dữ liệu, các thiết bị thu thập (bộ thu thập dữ liệu/cảm biến), và các loại dữ liệu NSM chính (dữ liệu phiên, dữ liệu bắt gói tin đầy đủ, dữ liệu kiểu chuỗi trong gói tin), cùng với các kỹ thuật quản lý và lưu trữ dữ liệu.

# **1. Phương pháp Thu thập Dữ liệu**

- Thu thập và phân tích dữ liệu là công việc **vô cùng quan trọng và tốn nhiều thời gian**.
    
- Nhiều tổ chức thường **không hiểu đầy đủ về dữ liệu** của họ và **thiếu cách tiếp cận có cấu trúc** để xác định các mối đe dọa.
    
- Hậu quả: thu thập dữ liệu tùy tiện dẫn đến **quá nhiều dữ liệu**, không đủ tài nguyên lưu trữ/xử lý, hoặc công cụ phân tích không hiệu quả.
    
- **ACF (Applied Collection Framework)**: Khung làm việc được xây dựng để **giảm sự phức tạp** của việc thu thập dữ liệu, giúp tổ chức đánh giá đc **các nguồn dữ liệu cần tập trung**. ACF giúp tổ chức đánh giá các nguồn dữ liệu cần tập trung. Nó gồm **bốn giai đoạn**.
    
    - **Giai đoạn 1: Xác định Nguy cơ**
        
        - Xác định các **mối đe dọa cụ thể** nhắm vào mục tiêu của tổ chức, không chỉ nguy cơ chung.
        - Trả lời câu hỏi: "**Tình trạng xấu nhất liên quan đến khả năng sống còn của tổ chức là gì?**". Cần làm việc với lãnh đạo cấp cao.
        - Nguy cơ thường tác động đến **Tính bảo mật, Tính toàn vẹn, Tính sẵn sàng** của tổ chức.
        - Nghiên cứu kỹ thuật/công nghệ cần để đối phó với nguy cơ.
        - Ví dụ: Mất tài sản trí tuệ dẫn đến các câu hỏi về dữ liệu thô, thiết bị xử lý/lưu trữ, quyền truy cập, đường dẫn mạng.
        - Xác định **các hệ thống có thể bị tấn công** gây tổn thất (ví dụ: máy chủ web, CSDL, máy chủ tệp tin).
    - **Giai đoạn 2: Định lượng Rủi ro**
        
        - **Ưu tiên** các mối đe dọa đã xác định.
        - Tính rủi ro: **Ảnh hưởng (I) × Xác suất (P) = Rủi ro (R)**.
        - I và P đo trên thang điểm 1-5 (1 ít nhất, 5 lớn nhất). Ảnh hưởng liên quan tài chính, phục hồi dữ liệu, thời gian hoạt động lại. Xác suất liên quan khả năng mối đe dọa xuất hiện, mức độ mạng bị tấn công, khả năng truy cập vật lý.
        - Rủi ro (R) đo trên thang 1-25. Phân loại: **Thấp (0-9), Trung bình (10-16), Cao (17-25)**.
        - Các con số mang tính chủ quan, thường dựa trên ủy ban hoặc bên thứ ba.
    - **Giai đoạn 3: Xác định Nguồn Dữ liệu**
        
        - Bắt đầu với mối đe dọa có **hệ số rủi ro cao nhất**.
        - Tìm **bằng chứng** về mối đe dọa trong dữ liệu.
        - Kiểm tra cả nguồn dữ liệu **dựa trên mạng** và **dựa trên máy chủ**.
        - Ví dụ: Tấn công máy chủ tệp tin -> kiểm tra cấu trúc máy chủ, vị trí, quyền truy cập, đường dẫn dữ liệu.
        - **Phân tích chi phí/lợi ích** của các nguồn dữ liệu (phần cứng, phần mềm, nhân công, lưu trữ). Nguồn dữ liệu quá lớn mà giá trị mang lại ít thì không tốt.
        - Xác định **số lượng dữ liệu và thời gian lưu trữ**.
    - **Giai đoạn 4: Chọn lọc Dữ liệu**
        
        - Sàng lọc để có **những nguồn dữ liệu chính, hữu ích**.
        - Dựa trên phân tích chi phí/lợi ích và tầm quan trọng của dữ liệu với mục tiêu tổ chức.
        - Xây dựng cơ sở hạ tầng thu thập dữ liệu **sau khi hoàn thành các giai đoạn ACF**.
        - Quá trình thu thập dữ liệu với NSM là **liên tục**, chiến lược cần được xem xét lại thường xuyên.
- **Ví dụ tình huống (Cửa hàng bán lẻ)**
    
    - Nguy cơ: Đánh cắp thông tin thẻ tín dụng (bảo mật), Gián đoạn dịch vụ TMĐT (sẵn sàng), Thay đổi thông tin trên web (toàn vẹn).
    - Xác định nguồn dữ liệu: Cảm biến nội mạng (FPC, Session, Packet String, NIDS dựa trên chữ ký/bất thường), Nhật ký máy chủ (web, CSDL, thư điện tử, ứng dụng điều khiển miền), Nhật ký bảo mật/HĐH.
    - Sơ đồ mạng được cập nhật với vị trí cảm biến.
    - Dữ liệu được chọn lọc dựa trên các nguy cơ cụ thể (ví dụ: luật NIDS tập trung tấn công CSDL, nhật ký tạo/sửa đổi tài khoản).

# **2. Bộ Thu thập Dữ liệu (Cảm biến)**

- Bộ thu thập dữ liệu kết hợp phần cứng và phần mềm để **tạo và thu thập dữ liệu** cho phát hiện/phân tích.
- **Chuyên gia phân tích** cần **thông thạo dữ liệu** họ có: nguồn, nơi lấy, cách thu thập, lý do và những gì có thể làm. Chuyên gia giỏi có thể làm dữ liệu xấu thành hữu ích.
- Chuyên gia cần truy cập bản sao dữ liệu để phân tích, **không tương tác trực tiếp với dữ liệu thô** trên bộ thu thập để tránh làm sai lệch. Bộ thu thập là tài sản quan trọng cần bảo vệ.
- **Phần cứng:** Nên là cấp độ **máy chủ**. Tài nguyên (bộ nhớ, lưu trữ, giao diện mạng) phụ thuộc vào loại/lượng dữ liệu.
    - **Bộ nhớ lớn** cần thiết, nên mua loại có thể bổ sung.
    - **Lưu trữ:** Khó quy hoạch, cần đánh giá lại thường xuyên. Ước tính nhu cầu lưu trữ bằng cách thu thập dữ liệu tạm thời vào thời điểm cao điểm/thấp điểm (ví dụ: 24 giờ weekday/weekend). Xác định thời gian lưu trữ tối thiểu/lý tưởng. Cần thêm không gian cho HĐH, công cụ (10-25%), phát triển sau này (10-25%).
    - **Giao diện mạng (NIC):** Thành phần quan trọng nhất, chịu trách nhiệm thu thập dữ liệu.
- **Vị trí đặt cảm biến:** Không có phương pháp thử và sai duy nhất, cần thực hành tốt nhất. Nhóm bảo mật nên tham gia sớm vào thiết kế mạng.
    - Tạo **sơ đồ mạng hiển thị vị trí cảm biến** và tài sản được bảo vệ để chuyên gia phân tích tham khảo. Sơ đồ nên khái quát logic cấp cao và các thiết bị ảnh hưởng lưu lượng.
- **Bảo mật bộ thu thập dữ liệu:** Cảm biến là mục tiêu giá trị cho kẻ tấn công.
    - **Cập nhật** HĐH và phần mềm thường xuyên.
    - **Bảo mật/làm cứng** HĐH.
    - **Tối thiểu hóa cài đặt phần mềm**, chỉ cài đặt cần thiết cho thu thập/phát hiện/phân tích. Vô hiệu hóa/gỡ bỏ dịch vụ không cần thiết.
    - **Phân đoạn VLAN** (giao diện quản trị và giao diện giám sát riêng biệt). Giao diện quản trị chỉ cho người quản trị truy cập.
    - Cài đặt **HIDS** (Host-based IDS) trên bộ thu thập (ví dụ: OSSEC, AIDE) để phát hiện thay đổi trên máy chủ.
    - Sử dụng **xác thực hai yếu tố/đa yếu tố** khi truy cập bộ thu thập.
    - Xác định **máy chủ được phép giao tiếp** với bộ thu thập và dùng luật Snort để phát hiện giao tiếp trái phép.
- Đánh giá nhu cầu lưu trữ cho bộ thu thập dữ liệu:
	- 

# **3. Các loại Dữ liệu NSM**

- **Dữ liệu Phiên (Session Data):**
    
    - **Bản tóm tắt** thông tin liên lạc giữa hai thiết bị mạng (còn gọi là hội thoại, luồng lưu lượng).
    - **Linh hoạt và hữu ích nhất**, kích thước nhỏ hơn FPC nên lưu trữ được **lâu hơn** cho phân tích lịch sử. Không chi tiết bằng FPC.
    - Cần 2 thành phần: **Bộ sinh luồng** (tạo luồng) và **Bộ thu thập luồng** (nhận và lưu trữ).
    - Sinh luồng từ dữ liệu FPC **không được khuyến khích** (dễ mất dữ liệu).
    - Nên **bắt trực tiếp dữ liệu trên liên kết** (phần mềm hoặc phần cứng).
    - Công cụ phần mềm sinh luồng ví dụ: Fprobe, YAF.
    - Công cụ **SiLK** (ví dụ: rwfilter, rwstats, rwcount) được dùng để phân tích dữ liệu phiên. rwstats/rwcount hữu ích để tạo thống kê lưu lượng, hiểu môi trường, phản ứng sự cố, tìm kiếm dữ liệu.
    - Lưu trữ: Tốn ít không gian hơn FPC, có thể lưu trữ theo chu **kỳ quý** hoặc **năm**.
- **Dữ liệu Gói tin đầy đủ (Full Packet Capture - FPC):**
    
    - Dữ liệu **gói tin thô**.
    - Luôn là loại dữ liệu **lớn nhất** trên mỗi đơn vị thời gian.
    - Có thể **tạo ra gần như tất cả các loại dữ liệu chính khác từ FPC**.
    - **Thông lượng** (tỷ lệ lưu lượng mạng qua giao diện) là lưu ý quan trọng khi triển khai. Cần đảm bảo cảm biến có đủ tài nguyên.
    - **Lưu trữ tốn nhiều không gian nhất**.
    - **Chiến lược lưu trữ:** Dựa trên **thời gian** (ví dụ: giữ 24 giờ) hoặc dựa trên **kích thước** (ví dụ: giữ 10TB). Dựa trên kích thước đơn giản và an toàn hơn do lưu lượng mạng có thể có "gai" (peak) khó đoán.
    - Công cụ bắt gói tin: tcpdump.
- **Dữ liệu Kiểu chuỗi trong Gói tin (Packet String Data - PSTR):**
    
    - Các **chuỗi con** (substring) được trích xuất từ các gói tin.
    - Thường bắt nguồn từ dữ liệu FPC.
    - Không gian lưu trữ **biến đổi rất lớn** tùy thuộc vào những chuỗi nào được thu thập. Nên tập trung thu thập dữ liệu tầng ứng dụng cần thiết từ các giao thức văn bản rõ.
    - Thời gian lưu trữ cần xem xét (có thể **vài giờ hoặc vài ngày như FPC**).
    - URLsnaft
- **Dữ liệu Thống kê (Statistical Data):**
    
    - Dữ liệu được tổ chức, phân tích, giải thích và biểu diễn từ các loại dữ liệu khác.
    - Ví dụ là kết quả phân tích từ các công cụ như rwstats và rwcount trên dữ liệu phiên.
- **Dữ liệu Cảnh báo (Alert Data):**
    
    - Được tạo ra bởi các công cụ phát hiện như hệ thống phát hiện xâm nhập trái phép (IDS) hoặc ứng dụng theo dõi nhật ký (log).
    - Chuyên gia phân tích sử dụng cảnh báo để điều tra và xác định sự cố.
    - rất nhỏ, đôi khi chỉ là...

Hy vọng cheatsheet này giúp bạn dễ dàng nắm bắt các kiến thức chính của Chương 2 và ôn tập hiệu quả! Chúc bạn thi tốt!


>[!note] cần xem lại đáp án:
>83, 136. 144. 146 148 152 156 |||||||||||||| 229 228 226 220 219 216

