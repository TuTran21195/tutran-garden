---
{"dg-publish":true,"permalink":"/1-project/kiem-thu-xam-nhap/cheatsheet-chuong-5/","title":"KTXN - Cheatsheet chương 5","tags":["tutran-garden","cheatsheet"],"created":"2025-06-17T20:20:19.798+07:00"}
---



---
## CHEATSHEET KIỂM THỬ XÂM NHẬP: CHƯƠNG 5 - KHAI THÁC HỆ THỐNG ĐÃ XÂM NHẬP VÀ KẾT THÚC KIỂM THỬ

Chương này tập trung vào việc mô tả các quy tắc khai thác một hệ thống sau khi đã xâm nhập, các bước thực hiện việc khai thác, bao gồm thu thập và phân tích dữ liệu, duy trì truy nhập, xâm nhập sâu vào hạ tầng thông tin và cách khôi phục lại trạng thái ban đầu của máy tính đã xâm nhập, đồng thời yêu cầu kiểm thử viên cần phải biết báo cáo chi tiết về các hoạt động của mình.

### 1. Các Quy Tắc Thực Hiện

- **Đánh giá mục tiêu** của ca kiểm thử xâm nhập và **quyết định những hành động cần thực hiện** để chứng minh sự tồn tại của các lỗ hổng khai thác trong hệ thống.
- **Xác định những thứ có thể sửa đổi** trong môi trường để thực hiện kiểm thử bảo mật, ví dụ như thêm hoặc xóa tài khoản, thay đổi tệp nhật ký hoặc khởi chạy các cuộc tấn công nội bộ.
- **Xem xét thêm "khóa vạn năng"** trong quá trình kiểm thử bảo mật. Khi thực hiện kiểm thử trên một mạng lớn, việc thêm "khóa vạn năng" vào các hệ thống quan trọng sẽ cho phép người kiểm thử bỏ qua các hạn chế hoặc thay đổi và bắt chước hành động điển hình của kẻ tấn công.
    - **Lưu ý**: Việc sử dụng "khóa vạn năng" có thể gây ra các vấn đề về an ninh và **cần được sử dụng cẩn thận**.
- **Thu thập và lưu trữ dữ liệu bởi nhóm kiểm thử**:
    - **Bảo quản dữ liệu** thu thập từ tài sản của khách hàng là **rất quan trọng**.
    - **Thiết lập các quy tắc cơ bản** trước khi thử nghiệm để quản lý mật khẩu, báo cáo, sự tham gia của bên thứ ba.
    - **Cần có sự đồng thuận trước với khách hàng** về cách dữ liệu này sẽ được chuyển, lưu trữ và làm sạch.
    - **Thiết lập các quy trình để xử lý các sự cố bảo mật** và đưa ra thông tin về kẻ tấn công đã có trong mạng.
- **Bảo mật thông tin cá nhân**:
    - **Cần đảm bảo thông tin cá nhân của nhân viên được bảo mật** trong quá trình kiểm thử.
    - Trong trường hợp thông tin được lưu trữ trên hệ thống không thuộc về khách hàng, **cần phải xác định rõ khách hàng có cho phép kiểm thử xem hay không và có thể sao chép và lưu trữ dữ liệu đó hay không**.
    - Ngoài ra, **cần phải kiểm tra kỹ hợp đồng và tư vấn với các chuyên gia pháp luật**.

### 2. Thu Thập Và Phân Tích Dữ Liệu

Khi hệ thống bị xâm nhập cần phải:

- **Liệt kê đầy đủ các thiết bị, quản lý thông tin và các manh mối có giá trị** một cách nhanh chóng, hiệu quả.
- **Thu thập thông tin và liệt kê các dịch vụ đã cài đặt, cấu hình mạng và lịch sử truy nhập**.
- **Tạo ra một danh sách các lệnh và thủ tục sẽ sử dụng** trong việc kiểm thử giúp các giai đoạn sau dễ dàng hơn, đặc biệt là giai đoạn báo cáo.
- **Việc hiểu các tệp và cài đặt quan trọng** cũng như cách thu thập và xem xét chúng là rất quan trọng, đặc biệt khi làm việc với các hệ thống dựa trên Windows.

**Các Tệp Và Thư Mục Quan Trọng Trong Windows**:

- **Tệp tin log (.log)** trong thư mục `%WINDIR%\system32\CCM\logs\` và các thư mục con của nó: Chứa thông tin liên quan đến quá trình cài đặt và quản lý phần mềm. Bao gồm thông tin về tải xuống, cài đặt gói phần mềm, cập nhật, sự kiện và lỗi. Ví dụ: `AppDiscovery.log` (tìm kiếm ứng dụng), `UpdatesDeployment.log` (triển khai cập nhật). Được sử dụng bởi các chuyên gia quản trị hệ thống để giám sát, phân tích và sửa chữa lỗi.
- **Tệp tin AppEvent.Evt**: Chứa các thông tin về các sự kiện liên quan đến ứng dụng trên hệ thống Windows (lỗi, cảnh báo, thông tin). Được sử dụng bởi Event Viewer để hiển thị các sự kiện khởi động, sử dụng và kết thúc ứng dụng. Chứa chi tiết về thời điểm, tên ứng dụng, mã lỗi. **Lưu ý**: Chỉ chứa các sự kiện gần đây nhất và sẽ bị ghi đè khi đạt giới hạn. Cần sao lưu thường xuyên nếu muốn lưu trữ lâu dài.
- **Tệp tin boot.ini**: Chứa thông tin về cấu hình khởi động của hệ thống Windows, bao gồm các tùy chọn khởi động, các hệ điều hành đã cài đặt và các tùy chọn khác như chế độ khởi động an toàn, thời gian chờ đợi.
- **Tệp tin default.sav**: Chứa bản sao lưu của registry mặc định của hệ thống Windows, bao gồm các giá trị và cấu trúc khóa registry cần thiết cho việc khởi động và hoạt động của hệ thống. Được lưu trữ trong thư mục `\Windows\system32\config\`. Được sử dụng để phục hồi registry mặc định trong trường hợp hệ thống gặp sự cố (ví dụ: System Restore, SFC).
- **Tệp tin hosts**: Tệp cấu hình trên hệ thống Windows được sử dụng để ánh xạ địa chỉ IP với các tên miền. Thường được dùng để giải quyết tên miền trong mạng cục bộ hoặc **chặn truy cập vào các trang web** bằng cách ánh xạ tên miền đó đến địa chỉ IP không hợp lệ hoặc địa chỉ IP localhost (127.0.0.1). Lưu trữ trong thư mục `%WINDIR%\System32\drivers\etc\`.
- **Các tệp tin index.dat của trình duyệt Internet Explorer và các vị trí khác**: Lưu trữ các thông tin về lịch sử duyệt web, các trang web đã truy cập và các tệp tin đã được tải xuống. Có thể được sử dụng bởi các ứng dụng khác (ví dụ: email). **Lưu ý**: Chứa các thông tin nhạy cảm về các hoạt động của người dùng và có thể được sử dụng để theo dõi/giám sát, do đó cần được xử lý và bảo vệ cẩn thận.
- **Tệp tin NetSetup.log**: Chứa các thông tin log về quá trình cài đặt mạng trên hệ thống Windows, bao gồm việc cài đặt và cấu hình các kết nối mạng. Dùng để xác định và khắc phục các vấn đề liên quan đến cài đặt mạng.
- **Tệp tin ntuser.dat**: Chứa registry của người dùng cụ thể trên hệ thống Windows. Bao gồm các cài đặt cá nhân như cấu hình desktop, tùy chọn hiển thị, màu sắc, âm lượng, các ứng dụng đã cài đặt và các tùy chọn cá nhân khác. Tải vào registry khi người dùng đăng nhập. Lưu trữ trong thư mục `%USERPROFILE%` và chỉ truy cập được bởi người dùng đó hoặc quản trị viên. Có thể sao lưu và khôi phục.
- **Tệp tin pagefile.sys**: Chứa định tuyến trang (paging file) của hệ thống trên ổ đĩa cứng. Là kỹ thuật tăng hiệu suất bằng cách lưu trữ dữ liệu tạm thời trên ổ đĩa cứng khi RAM đầy. Được tạo tự động bởi hệ thống và có kích thước tùy thuộc vào cấu hình. Lưu trữ trong thư mục gốc của ổ đĩa hệ thống (thường là ổ C:) và **không nên được xóa hoặc chỉnh sửa** bởi người dùng. Việc này có thể gây ra các vấn đề liên quan đến bộ nhớ và hiệu suất.
- **Tệp tin SAM (Security Accounts Manager)**: Chứa các thông tin tài khoản bảo mật của người dùng trên hệ thống Windows, bao gồm mật khẩu và chính sách bảo mật. Thường được lưu trữ trong thư mục `%WINDIR%\system32\config`. Có thể khôi phục từ tệp sao lưu trong `%WINDIR%\repair\sam`, nhưng có thể mất thông tin mới hơn.
- **Tệp tin SecEvent.Evt**: Chứa các thông tin sự kiện bảo mật trên hệ thống Windows, như đăng nhập/đăng xuất người dùng, quản lý tài khoản, quản lý nhóm và các sự kiện bảo mật khác. Chỉ có thể được truy cập bởi các quản trị viên hệ thống hoặc người dùng có đặc quyền truy cập.
- **Tệp tin security.sav**: Là một tệp lưu trữ dữ liệu bảo mật của hệ thống. Chứa thông tin về các tài khoản người dùng, quyền truy cập và các thiết lập bảo mật khác. Là một phần của cơ chế bảo mật của hệ điều hành Windows và **không nên được chỉnh sửa hoặc xóa bỏ** bởi người dùng, vì có thể gây ra các vấn đề bảo mật hoặc làm hỏng hệ thống.
- **Tệp tin software.sav**: Chứa các thông tin cấu hình của hệ thống và các ứng dụng đã được cài đặt, bao gồm: thiết lập hệ thống, các ứng dụng đã cài đặt, các thiết lập ứng dụng, và lịch sử cập nhật/bảo trì. Là một phần quan trọng của hệ thống Windows và **không nên bị xóa bỏ hoặc chỉnh sửa**.
- **Tệp tin system trong thư mục `%WINDIR%\repair`**: Là tệp lưu trữ dữ liệu phục hồi của hệ thống, chứa bản sao của tệp hệ thống "system" được tạo ra khi cài đặt Windows. Bao gồm: thiết lập hệ thống, trình điều khiển thiết bị/phần cứng, tùy chọn cấu hình hệ thống.
- **Tệp tin system.sav trong thư mục `%WINDIR%\system32\config`**: Là một tệp lưu trữ dữ liệu hệ thống. Chứa thông tin về cấu hình của hệ thống, bao gồm các cài đặt phần cứng và phần mềm, thiết lập bảo mật và các thiết lập khác.
- **Tệp win.ini trong thư mục `%WINDIR%`**: Là một tệp văn bản được sử dụng để lưu trữ các thông số cấu hình của hệ thống và các ứng dụng. Chứa: thiết lập hệ thống, các ứng dụng đã cài đặt, các thiết lập ứng dụng. **Lưu ý**: Từ sau Windows 95, các cài đặt hệ thống được lưu trên các tệp khác nên tệp `win.ini` không còn được sử dụng rộng rãi.

**Công Cụ Armitage**:

- Có thể sử dụng công cụ Armitage cài trên Kali Linux trong cùng mạng để quét mạng (ví dụ: Nmap).
- **Tương tác với hệ thống bị xâm nhập**: Trong Armitage, nhấp chuột phải vào hệ thống bị xâm nhập và chọn `Meterpreter 3 | Interact | Meterpreter Shell`. Gõ `sysinfo` tại dấu nhắc để lấy thông tin hệ thống.
- Các lệnh ví dụ: `dir C:\ /s /b | find /i “important”`, `reg export HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall tmp.txt`.

### 3. Duy Trì Truy Nhập

- Sau khi tiếp cận được với hệ thống mục tiêu, **có thể lựa chọn sử dụng hệ thống bị tấn công để làm bước đệm cho các cuộc tấn công khác**.
- Nếu không muốn bị phát hiện, cần phải **đảm bảo bí mật**, biện pháp phổ biến là thông qua việc **cài đặt cơ sở hạ tầng ẩn** để tiếp tục truy nhập được lại hệ thống mà không bị kiểm soát. Ví dụ sử dụng **backdoor, Trojan, rootkit**.

**Backdoor và Trojan**:

- Công cụ đơn giản để thiết lập truy nhập vào hệ thống đã bị vi phạm.
- Trong các hệ thống Windows, phần lớn các trojan tiến hành tự cài đặt và chạy dưới dạng dịch vụ trên hệ thống cục bộ, có quyền quản trị.
- Có thể sử dụng trojan để tìm ra hay nghe trộm mật khẩu, thông tin, và bất kỳ thông tin nhạy cảm khác được lưu trữ trên hệ thống.

**Rootkit**:

- Có khả năng **ẩn giấu khỏi hệ thống máy tính**.
- Thường được tải về với sự trợ giúp của trojan (được cài trên hệ thống với mức truy nhập là người dùng thông thường). Sau đó, rootkit sẽ cố gắng đánh cắp mật khẩu và các thông tin đăng nhập tương tự khác để có quyền truy nhập cấp quản trị viên. Quá trình này được gọi là **leo thang đặc quyền**.
- Khác với các mã độc khác, các rootkit có xu hướng **lẩn trốn trong hệ thống mục tiêu, dần dần và từ từ làm suy yếu**.
- **Rootkit nguy hiểm hơn nhiều vì**:
    - Chúng có khả năng **ngụy trang sự hiện diện** khi thêm mã vào các phần của nhân của hệ điều hành.
    - **Khởi chạy sớm hơn** so với hệ điều hành.
    - Có thể **phá vỡ mật mã và tạo ra các kênh bí mật** để truy nhập không bị giới hạn vào hệ thống bị xâm nhập.
    - Để loại bỏ rootkit và root-level rootkit **thường rất khó**.
    - Rootkit nằm trong bộ nhớ nhân **thường không để lại dấu vết trên đĩa cứng**.
    - Ngoài ra, chúng có thể sửa đổi các tập tin, các phần của đĩa, và thậm chí thay đổi nhân để có thể chống lại việc khởi động lại.
- Rootkit cài đặt ở mức nhân có đủ quyền của quản trị viên với đầy đủ khả năng truy nhập vào các hệ thống, ở mức hệ điều hành.
- **Để phòng tránh rootkit**:
    - Cần phải chọn những chương trình được xây dựng nhằm mục đích loại bỏ rootkit như Malwarebytes Anti-rootkit, GMER, Sophos Anti-Rootkit, TDSSKiller, ….
    - Ngoài ra có thể làm sạch hoàn toàn máy tính bằng cách sao lưu các tập tin quan trọng nhất và cài đặt lại hệ điều hành hoàn toàn. **Tuy nhiên cách này không hiệu quả với rootkit ở BIOS**.

**Truyền Tải Dữ Liệu Trái Phép (Data Exfiltration)**:

- Là quá trình thực hiện truyền tải dữ liệu trái phép từ hệ thống máy tính hoặc máy chủ tới một hệ thống hoặc thiết bị bên ngoài.
- Có thể được thực hiện bằng tay (tương tự như lệnh 'copy-paste') hoặc tự động lây lan qua các phần mềm độc hại trên mạng.
- Ngoài thực hiện bằng kênh trực tiếp như: loại giao thức web khác nhau, các giao thức đường hầm, email hoặc truyền tệp, thì việc **sử dụng các phương tiện vật lý như USB cũng rất phổ biến**.
- **Mục tiêu đánh cắp**: Các thông tin cá nhân, thông tin nhận dạng thông tin sức khoẻ cá nhân, tài sản trí tuệ và dữ liệu.
- **Một số dấu hiệu đáng chú ý của quá trình đánh cắp dữ liệu**: Hoạt động trên cổng trái phép, hoạt động email với khối lượng lớn đến miền không phải của công ty, máy chủ gửi email quá nhiều, truy vấn DNS quá nhiều, tải dữ liệu lên các trang web không phải của công ty.
- Do đó, người kiểm thử trong quá trình thực hiện duy trì truy nhập cần chú ý **đảm bảo không lộ rõ các dấu hiệu này** để tránh việc bị phát hiện sớm.

### 4. Xâm Nhập Sâu Vào Hạ Tầng Thông Tin

- Trước khi xâm nhập sâu vào hạ tầng thông tin, cần **tìm kiếm thông tin về mạng và các kết nối đến các máy tính**.
- (Các nguồn cũng minh họa bằng hình ảnh cho thấy việc phân tích mạng và tìm kiếm mục tiêu sâu hơn).

### 5. Khôi Phục Lại Trạng Thái Ban Đầu Của Các Máy Tính

- Nhiệm vụ này **rất quan trọng** trong việc tránh phát hiện và thiết lập lại mạng như ban đầu sau khi thử nghiệm hoàn tất.
- Việc **bỏ qua một máy chủ đã bị xâm nhập sẽ rất nguy hiểm** do người khác có thể lợi dụng để khai thác.
- **Cần ghi chép tỉ mỉ và lưu giữ hồ sơ chính xác** về không chỉ những gì đã làm trong khi kiểm tra mà còn cả những điều đã được thực hiện có thể vẫn tồn tại sau khi thử nghiệm.
- **Cần có một danh sách kiểm tra** cho tất cả các hành động phải hoàn tác.
- Trong quá trình thực hiện kiểm thử, **nên làm dần từng bước và thực hiện dọn dẹp khôi phục ngay khi có thể**.
- **Hiểu rõ nơi các tệp log được lưu trữ, nội dung của chúng và cách chúng được theo dõi**.
- **Tìm hiểu về các tệp log khác nhau** cho các hệ điều hành được sử dụng rộng rãi nhất như các bản phân phối Linux phổ biến và máy chủ Windows.
- Ngoài ra, các quản trị viên khi xem lại log sẽ tìm kiếm các dấu vết bất thường. Do đó, để tránh bị phát hiện lưu lượng truy nhập và hành động bất thường, **cần hợp nhất với lưu lượng truy nhập của những người dùng trung bình**.

### 6. Thu Thập Dữ Liệu Và Báo Cáo

- **Mọi bước của thử nghiệm xâm nhập phải được ghi lại vào tài liệu một cách thích hợp**.
- Điều này không chỉ cho phép **các kết quả chính xác và có thể lặp lại** mà còn cho phép ai đó kiểm tra lại công việc và đảm bảo không có gì bị bỏ sót trong quá trình thử nghiệm.
- Khi thử nghiệm xâm nhập ngày càng phổ biến, các nhóm thử nghiệm ngày càng trở nên phân khúc và chuyên biệt hơn.
- Có thể sử dụng **công cụ Dradis cho việc cộng tác** và đồng bộ thông tin thu thập được.

**Cấu Trúc Báo Cáo**:

- **Trang bìa** phải bao gồm:
    - Logo công ty.
    - Tiêu đề và mô tả của thử nghiệm đã thực hiện.
    - Nhắc nhở bảo mật.
    - Ngày và thời gian thử nghiệm.

---

Hy vọng cheatsheet này sẽ giúp bạn hệ thống hóa kiến thức và ôn tập hiệu quả cho bài kiểm tra của mình! Chúc bạn đạt kết quả tốt!