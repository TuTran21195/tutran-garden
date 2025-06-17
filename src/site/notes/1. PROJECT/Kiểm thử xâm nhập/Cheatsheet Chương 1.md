---
{"dg-publish":true,"permalink":"/1-project/kiem-thu-xam-nhap/cheatsheet-chuong-1/","title":"KTXN - Cheatsheet chương 1","tags":["tutran-garden","cheatsheet"],"created":"2025-05-30T01:05:51.000+07:00"}
---



# Cheetsheet - Prompt 1
Cheatsheet Chương 1: Khái niệm và Vai trò của Kiểm thử Xâm nhập, Kỹ thuật và Công cụ trong kiểm thử xâm nhập:

## **1.1 Khái niệm và Vai trò của Kiểm thử Xâm nhập**

- **Tổng quan về An toàn thông tin**
    - Mức độ bảo mật của hệ thống được xác định bởi khả năng của ba thành phần: Chức năng, Bảo mật, Tiện ích (Mô hình tam giác).
    - Các thách thức cần quan tâm bao gồm: Gia tăng tội phạm mạng tinh vi, Rò rỉ dữ liệu, An ninh di động, Nguồn nhân lực an ninh mạng, Khai thác lỗ hổng, Bảo vệ cơ sở hạ tầng quan trọng, Cân bằng công và tư, Tiếp cận nhận dạng chiến thuật và chu trình.
    - Danh sách các nguy cơ an ninh: Trojans, đánh cắp thông tin, keylogger, Mạng ma, Botnet, Chợ đen, Thất thoát dữ liệu, Vi phạm an ninh, Tống tiền trên mạng, Mối đe dọa nội bộ, Di chuyển dữ liệu, Tổ chức tội phạm mạng, Lừa đảo, Lỗ hổng công nghệ mới, Virus mới, Gia công phần mềm, Gián điệp mạng, Mạng xã hội, Zero-Day, Gián đoạn kinh doanh, Mối đe dọa từ web 2.0, Công nghệ ảo hóa và điện toán đám mây.
- **Khái niệm tấn công mạng (hack)**
    - **Ảnh hưởng của tấn công mạng**: Gây thiệt hại lớn về kinh tế cho doanh nghiệp (ví dụ: 2,2 triệu $ mỗi năm theo nghiên cứu của Symantec), làm giảm danh tiếng, ăn cắp bí mật thông tin (tài chính, hợp đồng), sử dụng Botnet để khởi động tấn công DOS và tấn công web khác dẫn đến giảm doanh thu, có thể làm các công ty phá sản.
    - **Khái niệm hacker**: Là người thông minh có kỹ năng máy tính xuất sắc, có thể tạo ra hay khám phá phần mềm/phần cứng. Mục đích có thể là tìm hiểu kiến thức hoặc phá hoại bất hợp pháp. Mục đích xấu bao gồm đánh cắp dữ liệu kinh doanh, thông tin thẻ tín dụng, số bảo hiểm xã hội, mật khẩu email.
    - **Các loại hacker**: Mũ đen (Black hat), Mũ trắng (White hat), Khủng bố (suicide hacker), Mũ xám (Grey hat).
- **Các giai đoạn tấn công mạng**
    - **1. Trinh sát (Reconnaissance)**
        - Giai đoạn chuẩn bị để thu thập thông tin về mục tiêu trước khi tấn công.
        - Mục đích: Tìm hiểu lượng lớn thông tin để tấn công dễ dàng hơn trong tương lai.
        - Phạm vi: khách hàng, nhân viên, hoạt động, mạng, hệ thống,....
        - Các loại:
            - **Thụ động**: Thu thập thông tin mà không tương tác trực tiếp (ví dụ: tìm hồ sơ công khai, bản tin).
            - **Chủ động**: Tương tác trực tiếp với mục tiêu (ví dụ: gọi điện để lấy thông tin kỹ thuật).
        - Thông tin thu thập trong giai đoạn trước tấn công (trinh sát): Thông tin cạnh tranh, đăng ký mạng, DNS và mail server, hoạt động hệ thống, người dùng, chứng nhận xác thực, kết nối tương tự, liên lạc, website, địa chỉ vật lý và logic, phạm vi sản phẩm/dịch vụ, và bất kỳ thông tin có giá trị nào khác.
    - **2. Quét (Scanning)**
        - Dựa trên thông tin trinh sát, kẻ tấn công quét mạng lưới thông tin của mục tiêu.
        - Bao gồm: trình quay số, máy quét cổng, lập bản đồ mạng, quét bao quát, quét lỗ hổng.
        - Khai thác thông tin như tên máy tính, địa chỉ IP, tài khoản người dùng để bắt đầu tấn công.
    - **3. Truy cập (Gaining Access)**
        - Kẻ tấn công giành được quyền truy cập vào hệ điều hành hoặc ứng dụng mạng.
        - Có thể truy cập ở cấp hệ điều hành, ứng dụng hoặc mạng.
        - Có thể nâng cấp quyền để truy cập toàn bộ hệ thống, đoạt quyền kiểm soát để khai thác thông tin.
        - Ví dụ kỹ thuật: bẻ mật khẩu, tràn bộ đệm, từ chối dịch vụ, đánh cắp tài khoản.
    - **4. Duy trì truy cập (Maintaining Access)**
        - Kẻ tấn công cố gắng giữ quyền sở hữu hệ thống đã chiếm được.
        - Sử dụng hệ thống này để bắt đầu các cuộc tấn công tiếp theo.
        - Giữ quyền sở hữu khỏi những kẻ tấn công khác bằng backdoors, rootkits, hoặc trojan.
        - Có thể thực hiện tất cả thao tác với dữ liệu của hệ thống sở hữu.
    - **5. Xóa dấu vết (Clearing Tracks)**
        - Kẻ tấn công xóa các bản ghi trên máy chủ, hệ thống, ứng dụng để tránh bị nghi ngờ.
        - Mục đích: che giấu hành vi tấn công, tiếp tục truy cập nạn nhân mà không bị phát hiện, xóa bằng chứng liên quan.
- **Các loại tấn công mạng**
    - **Tấn công vào hệ điều hành**: Tìm kiếm và khai thác lỗ hổng OS (tràn bộ đệm, lỗi OS chưa vá).
    - **Tấn công cấp ứng dụng**: Khai thác lỗi trong phần mềm ứng dụng do nhiều chức năng hoặc thiếu thử nghiệm.
    - **Tấn công vào cấu hình sai**: Khai thác hệ thống lỗi cấu hình (ví dụ: thay đổi quyền truy cập tệp).
    - **Tấn công gói tin nhỏ**: Khai thác lỗ hổng khi thay đổi các thiết lập mặc định.
- **Kiểm thử xâm nhập (Penetration Testing - Pentest)**
    - Là một phương pháp chủ động đánh giá an toàn mạng/hệ thống thông tin bằng cách **mô phỏng các cuộc tấn công từ nguồn độc hại**.
    - Phân tích tích cực các điểm yếu thiết kế, sai sót kỹ thuật, lỗ hổng.
    - Đánh giá mô hình bảo mật của tổ chức một cách tổng thể.
    - Khác với tấn công thực sự ở chỗ là một tấn công có mục đích chính đáng và **không ác ý**.
    - Cho thấy hậu quả tiềm tàng của một tấn công thực sự.
    - Nếu không thực hiện chuyên nghiệp có thể dẫn đến mất dịch vụ và gián đoạn kinh doanh.
    - **Vấn đề về kiểm thử xâm nhập mạng**: Không có mạng nào an toàn tuyệt đối.
    - **Vai trò/Sự cần thiết**:
        - Giúp đưa ra chiến lược phòng thủ theo chiều sâu.
        - Cho phép phòng chống các cuộc tấn công của hacker bằng cách dự đoán cách tấn công họ có thể dùng.
        - Xác định các mối đe dọa đối với tài sản thông tin của tổ chức.
        - Giảm chi phí bảo mật và đầu tư công nghệ tốt hơn bằng cách xác định/giải quyết lỗ hổng/điểm yếu.
        - Cung cấp sự đảm bảo - đánh giá kỹ lưỡng toàn diện an ninh (chính sách, thủ tục, thiết kế, thực hiện).
        - Đạt được và duy trì chứng nhận quy định ngành (BS7799, HIPAA…).
        - Thông qua thực hiện tốt bằng cách xác nhận quy định pháp luật và ngành.
        - Tập trung vào các lỗ hổng mức độ nghiêm trọng cao, nhấn mạnh vấn đề bảo mật ứng dụng.
        - Cung cấp phương pháp chuẩn bị toàn diện để ngăn chặn khai thác trái phép.
        - Đánh giá hiệu quả thiết bị an ninh mạng (firewall, router, web server).
        - Hỗ trợ khi thay đổi, nâng cấp cơ sở hạ tầng hiện có.
    - **Ưu điểm**: Là phần quan trọng của đánh giá nguy cơ, kiểm toán, quản trị hệ thống. Giúp nhận diện rủi ro, khắc phục hậu quả, giảm nguy cơ an toàn hệ thống.
    - **Hạn chế**: Doanh nghiệp thường chỉ thuê kiểm tra khi biết hệ thống có lỗi và chỉ kiểm tra một lần. Chỉ các tổ chức cần bảo vệ mạng mới có nhu cầu.
- **Nghiên cứu lỗ hổng (Vulnerability Research/Assessment)**
    - **Định nghĩa**: Quá trình phát hiện lỗ hổng trong thiết kế để tấn công hoặc lợi dụng hệ điều hành và ứng dụng. Lỗ hổng thường phân loại theo mức độ nghiêm trọng (thấp, trung bình, cao) và phạm vi khai thác (cục bộ, từ xa).
    - **Mục đích**:
        - Xác định và sửa chữa lỗ hổng mạng.
        - Bảo vệ mạng khỏi tấn công.
        - Thu thập thông tin về virus.
        - Giải quyết vấn đề an ninh.
        - Tìm điểm yếu và cảnh báo quản trị viên trước khi bị tấn công.
        - Biết cách khôi phục thiết bị sau khi bị tấn công.
    - **Đánh giá lỗ hổng (Vulnerability Assessment)**: Quét mạng để tìm lỗ hổng. Công cụ quét giúp tìm thiết bị IP-enabled, liệt kê hệ thống, OS, ứng dụng, xác định sai sót cấu hình bảo mật phổ biến, kiểm tra hệ thống/mạng ảnh hưởng trực tiếp bởi tấn công thông thường.
    - **Hạn chế của đánh giá bảo mật (bao gồm đánh giá lỗ hổng)**: Phần mềm giới hạn khả năng phát hiện lỗ hổng tại một thời điểm. Phải cập nhật khi lỗ hổng mới được phát hiện hoặc phần mềm thay đổi. Phương pháp và phần mềm quét đa dạng ảnh hưởng đến kết quả.

## **1.2 Kỹ thuật Kiểm thử Xâm nhập**

- **Các mức đánh giá an ninh**: Kiểm tra an ninh, Đánh giá tính dễ bị tấn công (Vulnerability Assessment), Kiểm thử xâm nhập (Penetration Testing).
- **Tại sao phải kiểm thử xâm nhập**: Lặp lại mục đích/vai trò từ 1.1, thêm các điểm: Kiểm tra và xác nhận hiệu quả bảo vệ an ninh và kiểm soát. Tập trung lỗ hổng mức cao, nhấn mạnh vấn đề bảo mật ứng dụng cho nhóm phát triển/quản lý. Cung cấp phương pháp tiếp cận toàn diện các bước chuẩn bị. Đánh giá hiệu quả thiết bị an ninh mạng. Hỗ trợ thay đổi/nâng cấp cơ sở hạ tầng.
- **Đối với các tổ chức**: Cần tiến hành đánh giá rủi ro trước khi pentest để xác định mối đe dọa chính (truyền tải thất bại, mất giao dịch, mất thông tin bí mật). Xác định hệ thống đối mặt cộng đồng (website, email, truy cập từ xa) và dịch vụ quan trọng (Mail, DNS, firewall, password, FTP, IIS, web server).
- **Lưu ý khi thực hiện pentest**: Thiết lập tham số (mục tiêu, hạn chế, quy trình). Thuê chuyên gia lành nghề, giàu kinh nghiệm. Chọn bộ phần kiểm tra phù hợp (cân bằng chi phí/lợi ích). Phương pháp luận đi kèm lập kế hoạch và tài liệu. Ghi chép kết quả cẩn thận, dễ hiểu cho khách hàng. Nêu rõ rủi ro tiềm ẩn và tìm kiếm trong báo cáo.
- **ROI với kiểm thử xâm nhập**: Công ty chi cho pentest khi hiểu lợi ích. Pentest giúp xác định, hiểu, giải quyết lỗ hổng, tiết kiệm tiền (ROI). Chứng tỏ tỷ lệ hoàn vốn bằng kế hoạch kinh doanh (chi phí, lợi nhuận). Thử nghiệm ROI quan trọng cho thành công dịch vụ pentest.
- **Điểm khởi đầu kiểm thử**: Tổ chức cần thống nhất mức độ thông tin tiết lộ cho đội kiểm thử (quyết định điểm khởi đầu). Cung cấp thông tin bổ sung cho đội pentest tạo lợi thế thực tế. Mức độ khai thác lỗ hổng mà không làm gián đoạn dịch vụ quan trọng cần được xác định.
- **Địa điểm kiểm tra**: Từ xa hoặc tại chỗ.
    - **Từ xa**: Mô phỏng tấn công hacker từ bên ngoài. Có thể bỏ lỡ đánh giá bảo vệ nội bộ.
    - **Tại chỗ**: Tốn kém. Không mô phỏng chính xác tác động bên ngoài.
- **Các hình thức kiểm thử xâm nhập**:
    - **External Testing**: Kiểm thử bên ngoài, phân tích thông tin công khai, liệt kê mạng lưới, hoạt động phân tích an ninh thiết bị. Tập trung hạ tầng máy chủ, phần mềm cơ bản (web server, mail server, firewall, router...).
    - **Internal Testing**: Kiểm thử nội bộ, thực hiện từ các điểm truy cập mạng (đại diện phân đoạn logic, vật lý - ví dụ: lớp và DMZ trong mạng nội bộ, kết nối đối tác). Đánh giá an ninh nội bộ theo phương pháp tương tự bên ngoài nhưng cung cấp cái nhìn đầy đủ hơn.
- **Các mô hình kiểm thử xâm nhập (Phân loại theo mức độ thông tin)**:
    - **Black Box Pen-test (Hộp đen)**: Mô phỏng tấn công từ người không có thông tin về hệ thống. Chỉ gợi ý tên công ty. Cần thu thập thông tin và nghiên cứu nhiều. Mô phỏng quá trình của hacker thực sự. Tốn thời gian và chi phí.
    - **White Box Pen-test (Hộp trắng)**: Mô phỏng tấn công từ người có thông tin/kiến thức về hệ thống. Hiểu biết đầy đủ về cơ sở hạ tầng. Mô phỏng hoạt động của nhân viên công ty. Thông tin được cung cấp gồm: cơ sở hạ tầng, loại mạng, triển khai an ninh hiện tại (IP/firewall/IDS), chính sách công ty.
    - **Grey Box Pen-test (Hộp xám)**: Tester có thông tin hạn chế. Thường thực hiện đánh giá an ninh bên trong. Phương pháp bảo mật ứng dụng bằng cách kiểm tra lỗ hổng hacker có thể tìm và khai thác. Thường thực hiện khi kiểm thử hộp đen trên hệ thống bảo vệ tốt và cần thêm kinh nghiệm để xem xét kỹ lưỡng.
- **Các hình thức kiểm thử xâm nhập (Phân loại theo thông báo)**:
    - **Announced Testing (Có thông báo)**: Phối hợp toàn diện và kiến thức của nhân viên IT. Kiểm tra hạ tầng bảo mật hiện có lỗ hổng. Nhân viên an ninh tham gia kiểm toán.
    - **Unannounced Testing (Không thông báo)**: Không cần thông tin của nhân viên an ninh. Chỉ quản lý cấp cao được biết. Kiểm tra hạ tầng an ninh và phản ứng của nhân viên IT.
- **Các hình thức kiểm thử xâm nhập (Phân loại theo cách thực hiện)**:
    - **Kiểm thử tự động (Automated Testing)**: Tiết kiệm thời gian, chi phí. Không thể thay thế kinh nghiệm chuyên gia bảo mật. Có thể đưa ra kết quả đúng/sai. Công cụ cần cập nhật thường xuyên. Không tồn tại phạm vi kiểm tra cho bất kỳ thành phần kiến trúc nào.
    - **Kiểm thử thủ công (Manual Testing)**: Lựa chọn tốt nhất để hưởng lợi từ kinh nghiệm chuyên gia an ninh. Mục đích chuyên gia: đánh giá tình trạng bảo mật từ góc độ kẻ tấn công. Đòi hỏi quy hoạch, thiết kế kiểm tra, lập kế hoạch, tìm tài liệu hướng dẫn để nắm bắt kết quả.
- **Kỹ thuật kiểm thử xâm nhập phổ biến**:
    - **Nghiên cứu bị động**: Thu thập thông tin cấu hình hệ thống.
    - **Giám sát mã nguồn mở**: Đảm bảo bí mật và tính toàn vẹn dữ liệu.
    - **Lập bản đồ mạng**: Nắm được cấu hình mạng đang kiểm thử. Sử dụng dữ liệu DNS và địa chỉ IP. Liệt kê thông tin máy chủ công khai (quét port, giao thức, cổng TCP/UDP), hình dung sơ đồ mạng, thu thập dữ liệu website, xác định subnet được lọc.
    - **Giả mạo (Spoofing)**: Sử dụng máy tính giả vờ là máy khách. Dùng trong kiểm thử nội bộ và bên ngoài.
    - **Network Sniffing**: Lấy dữ liệu khi truyền qua mạng.
    - **Trojan tấn công**: Mã độc/chương trình gửi qua mạng (file đính kèm email, tin nhắn chat).
    - **Tấn công vét cạn (Brute Force)**: Phương pháp bẻ khóa phổ biến nhất.
    - **Quét lỗ hổng (Vulnerability Scanning)**: Kiểm tra toàn diện các vùng hạ tầng mạng. (Xem thêm phần Nghiên cứu lỗ hổng).
    - **Phân tích tình huống (Situation Analysis)**: Giai đoạn cuối, đánh giá rủi ro lỗ hổng chính xác hơn.
- **Các giai đoạn của kiểm thử xâm nhập**:
    - **Giai đoạn trước khi tấn công**: Đề cập chế độ tấn công và mục tiêu. Do thám (trinh sát thụ động/chủ động) là giai đoạn này. Thu thập càng nhiều thông tin càng tốt. (Lặp lại nội dung Trinh sát từ 1.1).
    - **Giai đoạn tấn công**: Bao gồm Xâm nhập vùng ngoài, Thu thập mục tiêu, Thực thi tấn công, Đặc quyền được nâng cao.
        - **Kiểm thử vòng ngoài**: Đánh giá báo cáo lỗi, quản lý lỗi (thăm dò ICMP). Kiểm thử ACL (giả mạo câu trả lời). Xác định ngưỡng DoS (kết nối liên tục TCP/UDP). Đánh giá quy tắc lọc giao thức (thử các giao thức SSH, FTP, Telnet). Đánh giá khả năng IDS (gửi mã độc hại, quét mục tiêu). Kiểm thử phản ứng hệ thống an ninh vòng ngoài web server (sử dụng phương thức HTTP POST, DELETE, COPY).
        - **Liệt kê các thiết bị**: Tập hợp thiết bị mạng và thông tin liên quan. Sau khi lập bản đồ mạng và xác định tài sản, bước tiếp theo là lập bản kê thiết bị. Kiểm tra vật lý bổ sung để đảm bảo liệt kê chính xác.
        - **Thu thập mục tiêu**: Tập hợp hoạt động tester với máy đối tượng nghi ngờ, sử dụng quét lỗ hổng và đánh giá an ninh. Bao gồm tấn công thăm dò (dùng kết quả quét mạng), chạy quét lỗ hổng, đánh giá hệ thống đáng tin cậy (cố gắng truy cập tài nguyên bằng thông tin hợp pháp).
        - **Kỹ thuật leo thang đặc quyền (Privilege Escalation)**: Khi giành được mục tiêu, tester cố gắng khai thác hệ thống và truy cập tài nguyên bảo vệ. Hoạt động: lợi dụng chính sách bảo mật kém, email/code web không an toàn để thu thập thông tin leo thang đặc quyền. Sử dụng brute force (admin finder, password crackers), Trojans, phân tích giao thức. Sử dụng thông tin thu thập qua kỹ thuật giao tiếp để truy cập trái phép tài nguyên đặc quyền.
        - **Thực thi, cấy ghép và xem lại**:
            - Kiểm soát hệ thống: Tester thỏa hiệp hệ thống bằng cách thực hiện code bất kỳ.
            - Thâm nhập vào hệ thống: Mục tiêu là tìm mức độ lỗi của hệ thống an ninh.
            - Thực hiện khai thác: Thực hiện khai thác bằng công cụ sẵn có hoặc thủ công, sử dụng lỗ hổng đã xác định.
    - **Giai đoạn sau tấn công**: Quan trọng để khôi phục hệ thống. Hoạt động: Loại bỏ file đã tải lên. Làm sạch mục đăng ký, loại bỏ lỗ hổng. Loại bỏ công cụ và khai thác. Khôi phục mạng bằng cách loại bỏ chia sẻ/kết nối. Phân tích kết quả và trình bày cho tổ chức.
- **Kết quả của kiểm thử xâm nhập**: Báo cáo pentest chi tiết sự cố, phạm vi hoạt động. Bao gồm mục tiêu, quan sát, hoạt động thực hiện, báo cáo sự cố. Nhóm nghiên cứu đề nghị biện pháp khắc phục.
- **Lộ trình kiểm thử xâm nhập**: (Sơ đồ trong nguồn hiển thị các bước hoặc khía cạnh của quá trình).
- **Đánh giá bảo mật ứng dụng**: Ứng dụng yếu có thể tiếp cận thông tin quan trọng. Đánh giá an ninh ứng dụng thiết kế để xác định/đánh giá mối đe dọa. Giúp hệ thống chống lại người dùng xấu cố gắng truy cập/sửa đổi/phá hủy dữ liệu/dịch vụ.
    - **Kiểm thử ứng dụng Web**: Xác nhận đầu vào (OS, kịch bản, DB, LDAP injection, XSS). Cải thiện đầu ra (phân tích ký tự đặc biệt, xác minh lỗi). Điều khiển truy cập (quyền truy cập admin, thao tác trường mẫu, truy vấn URL, thay đổi giá trị phía client, tấn công cookie). Lỗi tràn bộ đệm (tấn công tràn ngăn xếp, khối xếp, chuỗi định dạng). Kiểm thử thành phần (kiểm soát an ninh máy chủ ứng dụng web). Từ chối dịch vụ (khả năng ngăn chặn DoS). Kiểm thử dữ liệu và lỗi (lưu trữ dữ liệu cache, qua HTML). Kiểm tra bảo mật (giao thức an toàn, mã hóa, cơ chế trao đổi khóa, chiều dài khóa, thuật toán). Quản lý phiên (thời gian hiệu lực/chiều dài/hết hạn thẻ phiên, sự hiện diện trong lịch sử/cache, ID phiên ngẫu nhiên). Xác nhận cấu hình (khai thác tài nguyên bằng HTTP method, kiểm tra phiên bản nội dung, lỗ hổng đã biết, khả năng tiếp cận giao diện máy chủ/thành phần).
- **Đánh giá an ninh mạng**: Quét môi trường mạng xác định lỗ hổng, cải thiện chính sách bảo mật. Phát hiện lỗi an ninh mạng dẫn đến dữ liệu/thiết bị bị khai thác/phá hủy. Đảm bảo thực hiện an ninh cung cấp bảo vệ cần thiết. Thực hiện bởi nhóm tìm cách đột nhập vào mạng/máy chủ.
    - **Đánh giá wireless/Remote Access**: Giải quyết rủi ro bảo mật với thiết bị di động (Bluetooth, IEEE 802.11).
    - **Kiểm thử mạng không dây**: Kiểm tra SSID mặc định của điểm truy cập. Kiểm thử xác thực để hạn chế truy cập trái phép. Giấy chứng nhận truy cập chỉ cấp cho máy khách đăng ký địa chỉ MAC.
    - **Kiểm thử mạng – thiết bị lọc gói tin**: Đảm bảo lưu lượng hợp pháp qua thiết bị lọc. Kiểm thử Proxy Server đánh giá khả năng lọc gói tin không mong muốn. Kiểm thử cài đặt mặc định tường lửa (ID/mật khẩu mặc định đã thay đổi). Thực hiện kiểm thử khác đánh giá khả năng bị tấn công từ đăng nhập từ xa.
    - **Mô phỏng từ chối dịch vụ (DoS)**: Mô phỏng tấn công DoS (nguồn cường độ lớn). Có thể dùng phần cứng hoặc trang web trực tuyến. Kiểm tra hiệu quả thiết bị anti-DoS.
- **Dịch vụ kiểm thử xâm nhập**: Xác nhận hạ tầng mạng được kiểm thử bởi bên thứ ba có thẩm quyền. Tổ chức yêu cầu đánh giá yếu tố an ninh cụ thể và gợi ý biện pháp khắc phục.
    - **Bảo lãnh phát hành pentest (Underwriting)**: Đảm bảo trách nhiệm nghề nghiệp, hoàn tiền nếu không đúng thỏa thuận, chịu trách nhiệm kết quả, dịch vụ không chuyên nghiệp. Còn gọi là bảo hiểm trách nhiệm nghề nghiệp E&O.
    - **Điều khoản cam kết**: Tổ chức có thể phạt pentester vi phạm lỗi quy định rõ. Nêu rõ điều khoản tham chiếu cơ quan tương tác tổ chức. Xác định mã hành vi, thủ tục.
    - **Quy mô dự án**: Xác định phạm vi (có mục tiêu hay toàn diện). Đánh giá toàn diện phát hiện nhiều lỗ hổng nhất trong toàn bộ tổ chức. Kiểm thử có mục tiêu tìm lỗ hổng trong hệ thống cụ thể.
    - **Cấp độ thỏa thuận dịch vụ Pentest (SLA)**: Hợp đồng chi tiết về dịch vụ người đảm nhận cung cấp. Xác định mức tối thiểu hành động tester và hành động khi sự cố/rối loạn nghiêm trọng. Thực hiện bởi chuyên gia, bao gồm biện pháp khắc phục/hình phạt.
    - **Tư vấn kiểm thử xâm nhập**: Thuê chuyên gia đủ điều kiện đánh giá chất lượng pentest. Pentest mạng công ty kiểm tra nhiều máy chủ (OS khác nhau), kiến trúc mạng, chính sách/thủ tục. Kỹ năng pentest đòi hỏi nhiều năm kinh nghiệm (phát triển, quản lý hệ thống, tư vấn). Mỗi khu vực mạng phải kiểm thử chuyên sâu.

## **1.3 Các Công cụ**

- **Các môi trường phổ biến cho thực hành kiểm thử xâm nhập**: Kali Linux, Metasploit Framework.
- **Kali Linux**: Bản phân phối Linux dựa trên Debian, mã nguồn mở, miễn phí. Phát triển cho mục đích kiểm tra xâm nhập chuyên nghiệp.
    - **Ưu điểm**: Hơn 600 công cụ pentest cài sẵn. Mã nguồn mở, tùy chỉnh cao, miễn phí. Hỗ trợ nhiều ngôn ngữ, nhiều thiết bị không dây (bộ vi xử lý ARM). Môi trường phát triển an toàn. Cây Git mã nguồn mở. Tuân thủ FHS. GPG bảo mật gói và kho lưu trữ đã ký. Có khả năng khởi động bằng CD/DVD hoặc USB.
    - **Nhược điểm**: (Không nêu rõ nhược điểm trong nguồn 1.3).
    - **Yêu cầu phần cứng tối thiểu**: Bộ xử lý Intel Core i3 hoặc AMD E1.
    - **Thông số kỹ thuật đề xuất**: Dung lượng ổ cứng 50 GB (ưu tiên SSD), ít nhất 2GB RAM.
    - **Một số công cụ hỗ trợ trên Kali Linux**: Aircrack-ng, Autopsy, Armitage, Burp suite, BeEF,....
- **Metasploit Framework (MSF)**: Nền tảng để viết, thử nghiệm và sử dụng mã khai thác. Người dùng chính là chuyên gia pentest, phát triển shellcode, nghiên cứu lỗ hổng.
    - Không chỉ là môi trường phát triển khai thác mà còn là nền tảng để khởi chạy khai thác trên ứng dụng thực tế. Có thể gây thiệt hại nếu không sử dụng chuyên nghiệp.
    - Công cụ nguồn mở, đơn giản hóa việc khởi động tấn công nguy hiểm. Thu hút hacker và script kiddies.
    - Lưu trữ cơ sở dữ liệu lỗ hổng đã công bố, cung cấp công cụ khai thác lỗ hổng.
    - Sử dụng để tạo payload kiểm thử hệ thống.
    - Xây dựng từ ngôn ngữ Perl, thành phần viết bằng C, assembly, Python.
    - Cài đặt được trên Windows, Linux, Mac OS; phổ biến nhất là Linux (Kali Linux cài sẵn Metasploit).
    - Hỗ trợ nhiều giao diện: Msfconsole (dòng lệnh), Armitage (đồ họa), giao diện Web.
    - **Môi trường làm việc**:
        - Môi trường toàn cục: Chứa biến toàn cục, có tất cả mô-đun khai thác.
        - Môi trường tạm thời: Chỉ biến vào mô-đun khai thác đang nạp, không ảnh hưởng mô-đun khác.
    - **Các bước sử dụng Metasploit cơ bản**:
        1. Chọn mô-đun khai thác (exploit): Chọn chương trình/dịch vụ có lỗi Metasploit hỗ trợ khai thác.
        2. Kiểm tra tùy chọn (lệnh `check`), chọn mục tiêu (hệ điều hành).
        3. Chọn payload (đoạn mã chạy trên hệ thống nạn nhân).
        4. Thực thi khai thác (lệnh `exploit`). Payload cung cấp thông tin hệ thống đã khai thác.
- **Payload**: Là một phần của mã độc.
    - Thường được viết bằng Hợp ngữ (Assembly).
    - Phụ thuộc vào nền tảng và hệ điều hành.
    - Các loại payload thực hiện nhiệm vụ khác nhau (ví dụ: exec, download_exec, upload_exec, adduser).
    - Loại payload phổ biến nhất để khai thác lỗ hổng là **mã shell (shellcode)**. Cung cấp cho kẻ tấn công một shell tương tác để kiểm soát hoàn toàn hệ thống từ xa. Thuật ngữ kế thừa từ Unix (`/bin/sh`), đối với Windows là comment prompt (`cmd.exe`).
    - **Các loại shell payload**:
        - **Bind Shells**: Tạo một socket, liên kết cổng, sinh ra shell khi kết nối.
        - **Reverse Shells**: Tạo kết nối đến IP và cổng xác định trước, chuyển shell tới kẻ tấn công.

---
Dưới đây là mô tả ngắn gọn về mục đích của các công cụ kiểm thử xâm nhập (pentesting) được liệt kê:

1. **Aircrack-ng**: Phân tích và bẻ khóa mật khẩu Wi-Fi (WEP, WPA/WPA2).
2. **Autopsy**: Phân tích pháp y số, khôi phục dữ liệu và điều tra thiết bị lưu trữ.
3. **Armitage**: Giao diện đồ họa cho Metasploit, quản lý và tự động hóa tấn công.
4. **Burp Suite**: Kiểm tra bảo mật ứng dụng web, phát hiện lỗ hổng như XSS, SQLi.
5. **BeEF**: Khai thác lỗ hổng trình duyệt web, tập trung vào tấn công phía client.
6. **Cisco Global Exploiter**: Tấn công và kiểm tra lỗ hổng trên thiết bị Cisco.
7. **Ettercap**: Tấn công man-in-the-middle, nghe lén và thao túng lưu lượng mạng.
8. **Hashcat**: Bẻ khóa mật khẩu bằng cách tấn công brute-force hoặc dictionary.
9. **John the Ripper**: Công cụ bẻ khóa mật khẩu, hỗ trợ nhiều định dạng hash.
10. **Kismet**: Phát hiện và phân tích mạng không dây, giám sát lưu lượng Wi-Fi.
11. **Lynis**: Kiểm tra bảo mật hệ thống Linux/Unix, đánh giá cấu hình và lỗ hổng.
12. **Maltego**: Thu thập và phân tích dữ liệu OSINT, lập bản đồ mối quan hệ.
13. **Metasploit Framework**: Khai thác lỗ hổng, phát triển và thực thi payload.
14. **Nmap**: Quét mạng, phát hiện host, dịch vụ và hệ điều hành.
15. **Nikto**: Quét máy chủ web để tìm lỗ hổng và cấu hình sai.
16. **OWASP ZAP**: Kiểm tra bảo mật ứng dụng web, phát hiện lỗ hổng tự động.
17. **Social Engineering Tools**: Hỗ trợ tấn công kỹ thuật xã hội, như phishing, giả mạo.
18. **Sqlmap**: Tự động hóa tấn công SQL injection, khai thác lỗ hổng cơ sở dữ liệu.
19. **Wireshark**: Phân tích gói tin mạng, giám sát và kiểm tra lưu lượng.
20. **WPScan**: Quét lỗ hổng trên website WordPress, kiểm tra plugin và theme.
21. **Nessus**: Quét lỗ hổng toàn diện trên hệ thống, mạng và ứng dụng.
22. **Zenmap**: Giao diện đồ họa cho Nmap, hỗ trợ quét và phân tích mạng.
23. **Hydra**: Tấn công brute-force mật khẩu cho nhiều giao thức (SSH, FTP, v.v.).
24. **Reverse Engineering Toolkit**: Phân tích mã nguồn, tháo gỡ và kiểm tra phần mềm.
25. **Foremost**: Khôi phục dữ liệu từ thiết bị lưu trữ, tập trung vào pháp y số.
26. **Volatility**: Phân tích bộ nhớ RAM để điều tra và pháp y số.
27. **VulnHub**: Cung cấp máy ảo để thực hành kiểm thử xâm nhập và học bảo mật.

Các công cụ này hỗ trợ các giai đoạn khác nhau trong kiểm thử xâm nhập, từ thu thập thông tin, quét lỗ hổng, khai thác, đến phân tích sau khai thác.