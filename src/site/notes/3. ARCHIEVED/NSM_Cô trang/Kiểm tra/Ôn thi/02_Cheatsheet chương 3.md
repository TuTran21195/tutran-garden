---
{"dg-publish":true,"permalink":"/3-archieved/nsm-co-trang/kiem-tra/on-thi/02-cheatsheet-chuong-3/","created":"2025-05-30T01:05:52.000+07:00"}
---



**Chương 3: Phát hiện xâm nhập (Intrusion Detection)**

Chương này tập trung vào bước **Phát hiện xâm nhập** trong chu trình NSM (Network Security Monitoring). **Phát hiện xâm nhập** là một chức năng của phần mềm thực hiện phân tích dữ liệu thu thập được để tạo ra dữ liệu cảnh báo.

# **1. Kỹ thuật phát hiện xâm nhập**

- Có hai cơ chế phát hiện xâm nhập chính:
    - **Dựa trên chữ ký (Signature-Based)**:
        - Hình thức lâu đời nhất.
        - Duyệt dữ liệu để tìm các kết quả khớp với các **mẫu đã biết (signatures)**.
        - Mẫu được chia thành các mẩu nhỏ, độc lập với nền tảng hoạt động, gọi là **dấu hiệu tấn công (Indicators of Compromise - IOC)**.
        - Mẫu được mô tả bằng ngôn ngữ cụ thể trong nền tảng của cơ chế phát hiện.
    - **Dựa trên bất thường (Anomaly-Based)**:
        - Là hình thức mới hơn, phổ biến với công cụ **Zeek.**
        - Dựa vào quan sát sự cố mạng và nhận biết **lưu lượng bất thường** thông qua chẩn đoán và thống kê.
        - Có khả năng nhận ra các **mẫu tấn công khác biệt** với hành vi mạng thông thường.
        - Đây là cơ chế phát hiện tốt nhưng khó thực hiện. Zeek là một cơ chế phát hiện bất thường và thực hiện phát hiện bất thường dựa trên thống kê.
		- Một tập con mới phát triển là **Phát hiện dựa trên Honeypot**.

# **2. Dấu hiệu xâm nhập và chữ ký (IOCs and Signatures)**

- **Dấu hiệu xâm nhập (IOC - Indicators of Compromise)**: Một mẫu thông tin được tìm thấy trên máy tính hoặc mạng, mô tả khách quan một xâm nhập.
    - IOC cho **mạng**: Ví dụ như địa chỉ IP độc hại, tên miền độc hại, mẫu lưu lượng bất thường.
    - IOC cho **máy tính**: Ví dụ như tài khoản người dùng, đường dẫn thư mục, tên tiến trình, tên tệp tin, khóa đăng ký.
- Khi một IOC được triển khai trong một ngôn ngữ hoặc định dạng cụ thể (ví dụ: luật Snort, tệp Bro/Zeek), nó sẽ trở thành một phần của một **chữ ký (signature)**. Một chữ ký có thể chứa một hoặc nhiều IOC.
- **IOC tĩnh (Static IOC)**: IOC mà giá trị được định nghĩa rõ ràng.
    - **IOC đơn vị (Unit IOC - ký hiệu là A)**: Cụ thể, nhỏ, không thể chia nhỏ hơn nhưng vẫn có ý nghĩa trong tình huống xâm nhập (ví dụ: địa chỉ IP, tên miền, chuỗi băm tệp tin).
    - **IOC được tính toán (Calculated IOC)**: Giá trị được tính toán từ các giá trị khác.
    - **IOC hành vi (Behavioral IOC)**: Mô tả một chuỗi các sự kiện mà một cuộc tấn công có thể tạo ra. Bao gồm nhiều IOC đơn vị và biến.
- **Biến IOC (IOC Variables)**: Dấu hiệu chưa biết giá trị, dựa trên một cuộc tấn công lý thuyết. Hữu ích trong các giải pháp như Bro/Zeek.
- **Quản lý dấu hiệu tấn công và chữ ký**: Cần có khả năng tạo, quản lý, phân phối IOC và chữ ký một cách hiệu quả. Nên dễ dàng tiếp cận và dễ dàng tìm kiếm.
- **Khung làm việc (Frameworks)**: Thiếu một khung làm việc chung cho việc tạo, quản lý, phân phối IOC và chữ ký là một vấn đề lớn. **STIX** (Structured Threat Information eXpression) là một kiến trúc mã nguồn mở dựa trên cấu trúc độc lập và các mối liên quan, sử dụng ngôn ngữ CybOX.

# **3. Phát hiện xâm nhập dựa trên danh tiếng (Reputation-Based)**

- Sử dụng **danh sách công khai (public lists)** của các IOC đơn vị (thường là địa chỉ IP, tên miền) có danh tiếng xấu (danh sách đen).
- Các danh sách này được đưa vào cơ chế phát hiện để cảnh báo khi một máy tính được bảo vệ giao tiếp với thiết bị bên ngoài có danh tiếng xấu.
- Có thể sử dụng **danh sách danh tiếng tùy chỉnh (custom lists)**.

# **4. Phát hiện xâm nhập dựa trên chữ ký với Snort và Suricata**

- Snort và Suricata là các công cụ phổ biến sử dụng phát hiện dựa trên chữ ký.
- **Cấu trúc luật (Rule Structure)**: Gồm 2 phần chính:
    - **Tiêu đề luật (Rule Header)**: Mô tả "ai" (các máy tính, cổng, giao thức, hướng lưu lượng).
        - Hành động (Action): Quy định hành động khi luật khớp (ví dụ: alert, log).
        - Giao thức (Protocol): TCP, UDP, ICMP, IP.
        - Địa chỉ nguồn/đích và Cổng nguồn/đích.
        - Hướng lưu lượng (Flow Direction): `->` (một chiều), `<>` (hai chiều).
    - **Các tùy chọn của luật (Rule Options)**: Mô tả "cái gì" (nội dung cần tìm kiếm trong gói tin). Đặt trong ngoặc đơn `()`. Mỗi tùy chọn có dạng `<Option>:<giá trị tùy chọn>;` hoặc `<Option>;`.
- **Tinh chỉnh luật (Rule Tuning)**:
    - **Lọc sự kiện (Event Filtering)**: Giảm số lượng cảnh báo.
    - Các phương pháp khác: Loại bỏ lưu lượng không mong muốn, nhắm tới lỗ hổng, ghép cặp cho PCRE và so sánh nội dung, so sánh mẫu nhanh, kiểm tra luật thủ công.
- **Công cụ** liên quan: Sguil, Barnyard2.

# **5. Phát hiện xâm nhập dựa trên bất thường với dữ liệu thống kê (Anomaly-Based with Statistical Data)**

- Sử dụng **dữ liệu thống kê (statistical data)**.
    - **Danh sách thống kê (Statistical Lists)**: Ví dụ đơn giản là danh sách các máy tính liên lạc nhiều nhất.
    - Công cụ **SiLK** (System for Internet-Level Knowledge) và các công cụ đi kèm như **rwstats** (tạo danh sách sắp xếp theo kích thước lưu lượng) và **rwcount** (tổng kết dữ liệu theo khoảng thời gian) được sử dụng để tạo ra số liệu thống kê từ dữ liệu phiên.
    - Có thể sử dụng rwstats để **khám phá dịch vụ (service discovery)** và xác định các máy chủ quan trọng.
- **Hiển thị thống kê (Statistical Display)**: Cung cấp cái nhìn sâu sắc và hữu ích.
    - Giúp phát hiện bất thường (lưu lượng lớn hơn đáng kể so với bình thường).
    - Hữu ích cho phát hiện rò rỉ dữ liệu, máy chủ nội bộ bị sử dụng để phục vụ malware, tấn công DoS nội mạng.
    - Giúp thu hẹp khoảng thời gian điều tra.
    - Các công cụ hiển thị: **Gnuplot** (vẽ đồ thị từ kết quả SiLK), **Afterglow** (tạo đồ thị liên kết).

Đây là những điểm cốt lõi của Chương 3. Chú trọng vào việc hiểu bản chất của từng kỹ thuật (dựa trên chữ ký vs dựa trên bất thường), các thành phần của chúng (IOCs, chữ ký, cấu trúc luật), và cách các công cụ hỗ trợ việc phát hiện.

Chúc bạn ôn tập tốt và làm bài kiểm tra đạt kết quả cao!