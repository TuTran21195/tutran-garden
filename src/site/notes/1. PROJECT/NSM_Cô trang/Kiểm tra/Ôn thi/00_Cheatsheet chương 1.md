---
{"dg-publish":true,"permalink":"/1-project/nsm-co-trang/kiem-tra/on-thi/00-cheatsheet-chuong-1/","created":"2025-06-06T15:17:47.821+07:00"}
---



---

**CHEATSHEET CHƯƠNG 1: GIỚI THIỆU GIÁM SÁT AN TOÀN MẠNG (NSM)**

Mục tiêu chính của Chương 1 là giới thiệu về Khái niệm và Thuật ngữ, Các hệ thống liên quan, Hệ thống NSM, và Một số ứng dụng của NSM.

**1. Khái niệm và Thuật ngữ**

- **Giám sát An toàn Mạng (Network Security Monitoring - NSM)** là một cách hiệu quả để bảo vệ máy tính và dữ liệu khỏi tội phạm mạng.
    
- NSM bao gồm:
    
    - **Thu thập dữ liệu**
    - **Phát hiện xâm nhập**
    - **Phân tích dữ liệu an ninh mạng**
- NSM **KHÔNG PHẢI LÀ**:
    
    - Quản lý thiết bị
    - Quản lý sự kiện an ninh
    - Điều tra số cho mạng máy tính
    - Ngăn chặn xâm nhập
- NSM được phân loại theo các miền sau:
    
    - **Bảo vệ**: ngăn chặn xâm nhập và khai thác trái phép vào hệ thống.
    - **Dò tìm (phát hiện)**: phát hiện ra tấn công đang xảy ra hoặc đã xảy ra trước đây.
    - **Đáp ứng/Phản ứng**: phản ứng lại sau khi có một tấn công đã xảy ra.
    - **Duy trì**: quản lý con người, các tiến trình và công nghệ liên quan đến Bảo vệ mạng máy tính (CND - Computer Network Defense).
- **Các Thuật ngữ Quan trọng:**
    
    - **Tài sản (Asset)**: Bất cứ thứ gì có giá trị trong tổ chức nằm trong phạm vi mạng tin cậy, bao gồm máy tính, máy chủ, thiết bị mạng, dữ liệu, con người, quy trình, sở hữu trí tuệ và danh tiếng.
    - **Nguy cơ (Threat)**: Một bên có khả năng và ý định khai thác một lỗ hổng trong một tài sản.
        - **Nguy cơ có cấu trúc**: sử dụng chiến thuật và thủ tục hành chính, đã xác định rõ mục tiêu.
        - **Nguy cơ không có cấu trúc**: không có động cơ, kỹ năng, chiến lược hoặc kinh nghiệm.
    - **Lỗ hổng (Vulnerability)**: Một điểm yếu (phần mềm, phần cứng hoặc thủ tục) có thể giúp kẻ tấn công đạt được quyền truy cập trái phép vào tài sản. Con người cũng có thể là một lỗ hổng.
    - **Khai thác (Exploit)**: Phương pháp tấn công một lỗ hổng. Ví dụ: đoạn mã chứa payload hoặc kỹ thuật SQL injection.
    - **Rủi ro (Risk)**: Khả năng/xác suất một mối đe dọa khai thác một lỗ hổng. Việc xác định định lượng rủi ro là khó.
    - **Bất thường (Abnormality)**: Một sự kiện quan sát được trong hệ thống hoặc mạng được coi là khác thường. Ví dụ: hệ thống bị sập, gói tin bị thay đổi. Bất thường tạo ra cảnh báo từ các công cụ như IDS.
    - **Sự cố (Incident)**: Sự vi phạm hoặc nguy cơ sắp xảy ra liên quan đến các chính sách bảo mật. Một điều xấu đã hoặc đang xảy ra trên mạng tổ chức. Ví dụ: tấn công root, cài malware đơn giản, DoS, thực thi mã độc từ email giả mạo.

**2. Các Hệ thống Liên quan**

- **Hệ thống Phát hiện Xâm nhập (IDS)**: Một thành phần của NSM hiện đại.
    - Đặc điểm: Bảo vệ (phòng thủ) lỗ hổng, phát hiện trong tập dữ liệu quan trọng, phần lớn dựa trên chữ ký, cố gắng phân tích tự động.
- **Quản lý Sự kiện và Thông tin Bảo mật (SIEM - Security Information and Event Management)**:
    - Hệ thống có khả năng thu thập, tổng hợp, lọc, hợp nhất, lưu trữ, tìm kiếm, tương quan, thông báo, phản hồi, trực quan hóa, phân tích/điều tra các sự kiện an toàn thông tin.
    - SIEM là sản phẩm, cũng có thể coi như quy trình.
    - Các quy trình quanh SIEM chia thành 3 nhóm:
        - Cơ bản (hỗ trợ): Thu thập, đánh giá, cài đặt.
        - Tuân thủ: Xem xét báo cáo, phản ứng với không tuân thủ.
        - Giám sát và điều tra liên tục: Xử lý thông báo sự cố, lập hồ sơ hành vi, phân tích đánh giá, giảm khả năng tái xuất sự cố.
- **Trung tâm Điều hành An ninh (SOC - Security Operations Center)**:
    - Nhóm bảo mật thông tin tập trung làm việc để giảm thiểu rủi ro.
    - Chịu trách nhiệm theo dõi và phân tích bảo mật bằng công nghệ và quy trình để phát hiện, ngăn chặn, phân tích và giảm thiểu sự cố.
    - Công thức: **SOC = “nền tảng SIEM + quy trình SIEM + nhân sự”**.
    - Các công cụ cần cho SOC: **EDR, NDR, XDR, MDR**.

**3. Hệ thống NSM**

- **Giới thiệu NSM**:
    
    - NSM xuất phát từ tư duy phòng thủ, ủng hộ bởi các tổ chức coi trọng bảo mật cao (ví dụ: quân đội).
    - Các hoạt động và mục tiêu có thể là: Phá hủy, Phá vỡ, Làm suy giảm, Từ chối, Đánh lừa, Khai thác, Gây ảnh hưởng, **Bảo vệ, Phát hiện, Khôi phục, Ứng phó**.
- **Các Đặc tính của NSM** (khác biệt với phát hiện xâm nhập truyền thống):
    
    - **Phòng chống đến cùng cho dù thất bại**: Chấp nhận tài sản có thể bị tổn hại, do đó tập trung thêm vào phát hiện và phản ứng, không chỉ dựa vào phòng thủ.
    - **Tập trung vào tập dữ liệu**: Chỉ cung cấp dữ liệu cần thiết cho chuyên gia phân tích để đưa ra quyết định nhanh và an toàn hơn.
    - **Tiến trình theo chu trình**: Quá trình phát hiện và ứng phó với xâm nhập cần có tính chu trình, khác với mô hình tuyến tính cũ.
    - **Phòng thủ theo nguy cơ (Threat-based defense)**: Tập trung vào "ai" và "tại sao" (kẻ tấn công, động cơ) thay vì "làm thế nào" (lỗ hổng). Khó khăn do cần tầm nhìn sâu rộng và khả năng thu thập thông tin tình báo về kẻ tấn công.
- **So sánh Phòng thủ theo Lỗ hổng Bảo mật và Phòng thủ theo Nguy cơ**:
    
    - **Phòng thủ theo Lỗ hổng Bảo mật**:
        - Tương đương xây bức tường gạch (vững chắc, bảo vệ nhiều mục tiêu).
        - Vấn đề: Gạch hỏng theo thời gian, cần khắc phục liên tục.
        - Dựa vào kỹ thuật phòng chống.
        - Tập trung vào phát hiện xâm nhập.
        - Giả thiết có thể biết được tất cả các nguy cơ.
        - Phân tích mỗi tấn công trong ngữ cảnh đơn giản.
        - Phụ thuộc nhiều vào phát hiện dựa trên chữ ký.
        - Ít khả năng phát hiện ra các nguy cơ chưa biết.
        - Tiến trình tuyến tính.
    - **Phòng thủ theo Nguy cơ**:
        - Tương đương dùng thủ môn bảo vệ (có thể thất bại ban đầu, tích lũy kinh nghiệm, thay đổi chiến thuật).
        - Ưu điểm: Học, thích nghi, và phát triển.
        - Biết rằng việc phòng chống cuối cùng sẽ thất bại.
        - Tập trung vào tập dữ liệu.
        - Biết rằng các nguy cơ sẽ sử dụng các công cụ, chiến thuật và thủ tục khác nhau.
        - Kết hợp thông minh từ mọi tấn công.
        - Sử dụng toàn bộ dữ liệu nguồn.
        - Rất có khả năng phát hiện ra các hoạt động tấn công ngoài những dấu hiệu đã biết.
        - Tiến trình theo chu trình.
- **Chu trình Giám sát An toàn Mạng**:
    
    - **Bước 1: Thu thập dữ liệu**:
        - Bước bắt đầu, quan trọng nhất.
        - Sự kết hợp cả phần cứng và phần mềm.
        - Tạo, sắp xếp và lưu trữ dữ liệu cho phát hiện xâm nhập và phân tích.
        - Định hình khả năng phát hiện và phân tích hiệu quả.
        - Các loại dữ liệu: Dữ liệu nội dung đầy đủ, Dữ liệu phiên, Dữ liệu thống kê, Dữ liệu kiểu chuỗi trong gói tin, Dữ liệu cảnh báo.
        - Cần nhiều lao động nhất.
        - Cần nỗ lực của lãnh đạo, đội an ninh, nhóm mạng, nhóm quản trị hệ thống.
        - Nhiệm vụ: Xác định điểm yếu, nguy cơ, nguồn dữ liệu liên quan, tinh chế nguồn dữ liệu, cấu hình cổng SPAN, xây dựng lưu trữ SAN, cấu hình phần cứng/phần mềm thu thập.
    - **Bước 2: Phát hiện xâm nhập**:
        - Kiểm tra dữ liệu thu thập và tạo cảnh báo dựa trên sự kiện bất thường.
        - Thực hiện qua chữ ký, sự bất thường, hoặc phát hiện dựa trên thống kê.
        - Kết quả là dữ liệu cảnh báo.
        - Thường là chức năng phần mềm: Snort IDS, Bro IDS (NIDS), OSSEC, AIDE, McAfee HIPS (HIDS).
        - SIEM có thể sử dụng dữ liệu mạng và máy chủ để phát hiện dựa trên sự kiện liên quan.
    - **Bước 3: Phân tích dữ liệu**:
        - Diễn giải và xem xét dữ liệu cảnh báo.
        - Cần thu thập dữ liệu bổ sung từ các nguồn khác.
        - Gồm: Phân tích gói tin, Phân tích mạng, Phân tích máy chủ, Phân tích phần mềm độc hại.
        - Phần tốn thời gian nhất.
        - Sự kiện có thể được nâng lên thành sự cố và bắt đầu ứng phó.
        - Kết thúc chu trình bằng các bài học kinh nghiệm và hình thành chiến lược thu thập dữ liệu cho tương lai.
- **Thách thức đối với hệ thống NSM**:
    
    - Khó khăn trong chuẩn hóa thuật ngữ và phương pháp do lĩnh vực mới.
    - Nguồn nhân lực không đủ đáp ứng yêu cầu (kinh nghiệm, kiến thức).
    - Chi phí thiết lập và duy trì (phần cứng cho dữ liệu lớn, lao động phân tích, hỗ trợ hạ tầng).
- **Nhân sự cho hệ thống NSM**:
    
    - Thành phần quan trọng nhất.
    - An toàn hệ thống phụ thuộc khả năng làm việc hiệu quả của chuyên gia phân tích.
    - Vai trò của chuyên gia phân tích: diễn giải dữ liệu cảnh báo, phân tích, xem xét sự liên quan, xác định sự cố thật, điều tra thêm. Có thể tham gia ứng phó sự cố, phân tích máy tính/malware.
    - Yêu cầu: Thường xuyên cập nhật công cụ, chiến thuật, thủ tục mới của đối phương.
- **Kỹ năng cần thiết cho Chuyên gia Phân tích NSM**:
    
    - Phòng thủ theo nguy cơ, NSM, và chu trình NSM.
    - Chồng giao thức TCP/IP.
    - Các giao thức tầng ứng dụng.
    - Phân tích gói tin.
    - Kiến trúc Windows và Linux.
    - Phân tích dữ liệu cơ bản (BASH, Grep, SED, AWK,…).
    - Cách sử dụng IDS (Snort, Suricata,…).
    - Dấu hiệu tấn công và hiệu chỉnh chữ ký IDS.
    - Mã nguồn mở.
    - Phương pháp chẩn đoán phân tích cơ bản.
    - Phân tích phần mềm mã độc cơ bản.
- **Phân loại Chuyên gia Phân tích**:
    
    - **Cấp 1 (L1)**: Không có khả năng giải quyết vấn đề chuyên môn đặc biệt. Dành phần lớn thời gian xem xét cảnh báo IDS và phân tích dựa trên đó. Làm việc dựa trên kinh nghiệm, phần lớn chuyên gia là L1.
    - **Cấp 2 (L2)**: Người cố vấn cho L1. Hỗ trợ hình thành tiến trình phát hiện (tạo chữ ký, nghiên cứu OSINT). Rà soát dữ liệu thủ công từ nhiều nguồn để tìm sự kiện tiềm năng.
    - **Cấp 3 (L3)**: Chuyên gia cấp cao nhất. Tư vấn cho L1/L2, phát triển đào tạo, hướng dẫn điều tra phức tạp. Chịu trách nhiệm phát triển và tăng cường khả năng thu thập/phân tích dữ liệu. Tạo/phát triển công cụ mới, đánh giá công cụ hiện có.

**4. Một số Ứng dụng của NSM**

- Các trường hợp cần theo dõi giám sát liên tục trong thực tế:
    1. Giám sát thực thể đặc quyền.
    2. Xác thực thất bại do vét cạn (brute force).
    3. Xác thực bất thường.
    4. Phiên bất thường.
    5. Bất thường về tài khoản.
    6. Các chỉ số lọc dữ liệu (data exfiltration).
    7. Chữ ký khớp với kết quả quét lỗ hổng bảo mật đã biết.
    8. Bất kỳ lỗi dịch vụ nào xuất hiện quá nhiều.
    9. Chỉ báo mối đe dọa từ bên trong.
    10. Các điều kiện lỗi của dữ liệu nhật ký bảo mật.
