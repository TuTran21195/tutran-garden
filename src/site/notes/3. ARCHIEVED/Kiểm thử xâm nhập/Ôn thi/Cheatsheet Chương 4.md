---
{"dg-publish":true,"permalink":"/3-archieved/kiem-thu-xam-nhap/on-thi/cheatsheet-chuong-4/","title":"KTXN - Cheatsheet chương 4","tags":["tutran-garden","cheatsheet"],"created":"2025-06-17T19:24:50.522+07:00"}
---



---

### Cheatsheet Chương 4: Phân tích mã nguồn

Chương này tập trung vào các kỹ thuật và phương pháp để **đánh giá, kiểm tra và phân tích mã nguồn** của phần mềm hoặc ứng dụng nhằm tìm ra **các lỗ hổng bảo mật** và các vấn đề khác.

#### 1. Các kỹ thuật phân tích mã nguồn

Phân tích mã nguồn có thể được thực hiện bằng hai kỹ thuật chính:

- **Phân tích thủ công**.
- **Phân tích tự động**.

#### 2. Phân tích mã nguồn thủ công

- **Định nghĩa**: Quá trình đọc và kiểm tra mã nguồn bằng tay để tìm lỗi lập trình, lỗ hổng bảo mật và các vấn đề khác. Thường được thực hiện bởi các chuyên gia bảo mật hoặc người có kinh nghiệm phát triển phần mềm.
- **Khi sử dụng**:
    - Ứng dụng được lập trình bằng ngôn ngữ không được hỗ trợ kiểm tra tự động.
    - Kiểm tra tất cả các khía cạnh của một chương trình.
    - Phân tích cấu trúc lập trình cực kỳ phức tạp để làm mẫu cho công cụ tự động.
- **Trọng tâm**: Dựa trên cách người dùng cung cấp dữ liệu được xử lý trong ứng dụng; hiểu cách dữ liệu được gửi đến và điều gì xảy ra với nó.
- **Hạn chế**:
    - **Tốn thời gian và công sức**, đặc biệt với các dự án lớn hoặc phức tạp.
    - **Giới hạn bởi khả năng của con người** trong việc phát hiện lỗi và lỗ hổng.
- **Ví dụ 1: Ứng dụng web (Kiểm thử xâm nhập)**
    - **Mục tiêu**: Phân tích mã nguồn để tìm lỗ hổng bảo mật hoặc điểm yếu.
    - **Các điểm cần tập trung**:
        1. **Tìm kiếm các lỗi bảo mật**: Đọc tất cả tệp mã nguồn để tìm lỗ hổng như **XSS, SQL Injection, tràn bộ đệm**.
        2. **Kiểm tra tính chính xác và hợp lệ của tham số đầu vào**: Xác định và kiểm tra các tham số đầu vào để đảm bảo ứng dụng hoạt động chính xác và tránh lỗi bảo mật.
        3. **Kiểm tra tính bảo mật của hệ thống**: Phân tích mã nguồn để tìm lỗ hổng liên quan đến hệ thống/máy chủ, đảm bảo an toàn và tránh tấn công.
        4. **Kiểm tra tính tương thích của ứng dụng**: Đọc mã nguồn để kiểm tra tương thích với các trình duyệt, hệ điều hành, thiết bị khác nhau.
        5. **Kiểm tra mã lược đồ**: Xác định phương thức truy cập cơ sở dữ liệu và kiểm tra mã lược đồ để đảm bảo tính bảo mật của CSDL.
- **Ví dụ 2: Chương trình C (Tìm lỗi và điểm yếu)**
    - **Mục tiêu**: Phân tích mã nguồn để tìm lỗi và điểm yếu.
    - **Các bước**:
        1. **Chạy chương trình và xem kết quả đầu ra**: Để biết chương trình hoạt động đúng hay sai, xem thông báo lỗi nếu có.
        2. **Đọc và hiểu mã nguồn**: Hiểu cấu trúc và hoạt động của chương trình (biến, hàm, lệnh điều kiện, vòng lặp).
        3. **Kiểm tra tính hợp lệ của tham số đầu vào**: Đảm bảo chương trình không bị tấn công qua tham số không hợp lệ, kiểm tra việc kiểm tra giá trị nhập vào.
        4. **Kiểm tra tính bảo mật của chương trình**: Xác định lỗ hổng như **buffer overflow, format string vulnerability, race condition**. Kiểm tra việc sử dụng các hàm bảo mật (ví dụ: `strcpy_s`, `strncat_s`, `strcat_s`).
        5. **Kiểm tra tính tương thích của chương trình**: Với các phiên bản HĐH và trình biên dịch khác nhau, xác định các hàm bị loại bỏ hoặc thay đổi.

#### 3. Phân tích mã nguồn tự động

- **Định nghĩa**: Sử dụng các công cụ phân tích mã nguồn để tìm lỗi lập trình, lỗ hổng bảo mật và các vấn đề khác. Công cụ có thể phân tích **tĩnh** hoặc **động**.
- **Công cụ ví dụ**:
    - **Yasca (Yet Another Source Code Analyzer)**: Công cụ mã nguồn mở viết bằng Python, chạy trên Windows, Linux, macOS. Phát hiện lỗ hổng và vấn đề trong mã nguồn ứng dụng web và phần mềm (C/C++, Java, JSP, PHP, Perl, Python).
    - **Plugin**: Sử dụng plugin để phát hiện lỗi bảo mật như SQL injection, XSS và các lỗ hổng khác. Cũng phát hiện vi phạm quy tắc lập trình, kiểm tra chuẩn mã nguồn, phân tích khai thác mã nguồn.
- **Ưu điểm**:
    - **Tốc độ nhanh hơn và chính xác hơn**.
    - **Khả năng phát hiện lỗi và lỗ hổng nhiều hơn và chi tiết hơn**.
    - **Giảm thiểu sự phụ thuộc vào khả năng con người**.
- **Hạn chế**:
    - **Không thể phát hiện tất cả các lỗi và lỗ hổng**.
    - Có thể xảy ra **lỗi phát hiện sai (false positive)** hoặc **báo động giả**.
    - Cần **đầu tư chi phí** để sử dụng các công cụ.

#### 4. Phân tích mã chương trình đã dịch (Mã đối tượng)

- **Định nghĩa**: Quá trình phân tích và hiểu cấu trúc, chức năng của chương trình đã được biên dịch thành mã máy (assembly code) hoặc mã đối tượng (object code).
- **Mục đích**: Hiểu cách hoạt động, tìm lỗi/vấn đề bảo mật, tối ưu hóa mã, đảo mã, tái sử dụng mã, tìm kiếm mã độc.
- **Hai loại**:
    - **Phân tích mã thông dịch (Interpreted code)**.
    - **Phân tích mã biên dịch (Compiled code)**.

##### 4.1. Phân tích mã thông dịch

- **Định nghĩa**: Phương pháp chuyển đổi mã nguồn thành mã thực thi ngay lập tức khi chương trình đang chạy, bởi một **trình thông dịch (interpreter)**. Mã nguồn và mã thực thi là khác nhau.
- **Ví dụ**: Java, Python.
    - **Java**: Trình thông dịch là **Java Virtual Machine (JVM)**. Bytecode Java dễ dịch ngược vì:
        - Các tệp lớp được biên dịch chứa lượng lớn thông tin mô tả.
        - Mô hình lập trình cho JVM khá đơn giản, tập lệnh ít.
    - Điều này cũng đúng với các tệp Python (.pyc).
- **Ví dụ**: Dịch ngược `PasswordChecker.class` bằng JReversePro.

##### 4.2. Phân tích mã biên dịch

- **Định nghĩa**: Phương pháp chuyển đổi toàn bộ mã nguồn thành mã thực thi **trước khi chương trình chạy**, bởi một **trình biên dịch (compiler)**. Mã nguồn và mã thực thi đều có thể được lưu trữ trên đĩa cứng hoặc bộ nhớ.
- **Ví dụ**: C, C++.
- **Công cụ**: **IDA Pro (Interactive Disassembler Professional)**.

##### 4.3. So sánh Mã thông dịch và Mã biên dịch

|Đặc điểm|Mã thông dịch|Mã biên dịch|
|:--|:--|:--|
|**Ưu điểm**|- Có thể thực thi nhanh hơn (không cần biên dịch toàn bộ trước)|- Thực thi nhanh hơn trong quá trình chạy (đã được biên dịch toàn bộ)|
||- Cho phép cập nhật mã nguồn và kiểm tra lỗi dễ dàng hơn|- Đảm bảo **tính bảo mật cao hơn** (mã nguồn đã được dịch thành mã thực thi)|
|**Nhược điểm**|- Có thể chậm hơn mã biên dịch trong quá trình thực thi và yêu cầu trình thông dịch|- Có thể yêu cầu nhiều tài nguyên hơn và cần **biên dịch lại** nếu có thay đổi mã nguồn|
||- **Không đảm bảo được tính bảo mật cao** (mã nguồn được dịch thực thi ngay lập tức)||

#### 5. Kỹ thuật Fuzzing

- **Định nghĩa**: Kỹ thuật phát hiện lỗi phần mềm bằng cách **tự động hoặc bán tự động** sử dụng phương pháp lặp lại thao tác **sinh dữ liệu** sau đó chuyển cho hệ thống xử lý.
- **Cách hoạt động**: Cung cấp dữ liệu đầu vào cho chương trình, theo dõi và ghi lại các lỗi, kết quả trả về.
- **Mục đích**: Tìm ra các lỗi bảo mật như **buffer overflow, lỗi xác thực** và các lỗ hổng khác.
- **Dữ liệu đầu vào**: Thường là **ngẫu nhiên, không hợp lệ hoặc không mong đợi** (giá trị vượt biên, giá trị đặc biệt ảnh hưởng xử lý/hiển thị).
- **Phân loại**: Là một trong những kỹ thuật **kiểm thử hộp đen (black box testing)**, không đòi hỏi quyền truy nhập mã nguồn.
- **Fuzzer**: Các chương trình và framework dùng để tạo hoặc thực hiện fuzzing.
- **Ưu điểm**:
    - **Rất hiệu quả trong tìm kiếm những lỗi nghiêm trọng** nhất về bảo mật hoặc khiếm khuyết.
    - Cải thiện vấn đề an ninh khi kiểm tra phần mềm.
    - Các lỗi tìm thấy thường là những lỗi mà tin tặc hay sử dụng (làm dừng chương trình, rò rỉ bộ nhớ, ngoại lệ chưa kiểm soát).
    - Tìm ra được những lỗi không được tìm thấy khi kiểm thử bị hạn chế về thời gian và nguồn lực.
- **Nhược điểm**:
    - **Không thể cung cấp đầy đủ về lỗi bảo mật tổng thể**.
    - **Kém hiệu quả hơn với các lỗi không gây ra sự cố treo phần mềm** (như virus, trojan).
    - Không cung cấp nhiều kiến thức về hoạt động nội bộ của phần mềm.
    - Với chương trình có đầu vào phức tạp, đòi hỏi tốn thời gian hơn để tạo ra một fuzzer đủ thông minh.

##### 5.1. Các bước thực hiện kỹ thuật Fuzzing

- **Fuzzing khi biết giao thức**:
    - **Bước 1: Xác định mục tiêu**: Các mục tiêu có nguy cơ rủi ro cao (lỗi lập trình như SQL Injection, cấu hình hệ thống không an toàn), ứng dụng nhận dữ liệu qua mạng, xử lý thông tin có giá trị hoặc cá nhân.
    - **Bước 2: Xác định đầu vào**: Các lớp đầu vào ứng với fuzzer phổ biến (đối số dòng lệnh, biến môi trường, ứng dụng Web, định dạng file, giao thức mạng, đối tượng Memory COM, IPC).
		- Đối số dòng lệnh
		- Biến môi trường: ShareFuzz
		- Ứng dụng Web: WebFuzz
		- Các định dạng file: FileFuzz
		- Giao thức mạng: SPIKE
		- Đối tượng Memory COM: COMRaider
		- Liên lạc liên tiến trình - IPC
    - **Bước 3: Tạo dữ liệu**: Tạo dữ liệu thử nghiệm ở các mức độ đảm bảo thỏa mãn điều kiện ứng dụng đầu vào (dạng file nhị phân, văn bản được sử dụng lặp lại). Hiệu quả fuzzing phụ thuộc vào độ bao phủ không gian đầu vào và chất lượng dữ liệu kiểm thử.
    - **Bước 4: Thực hiện test sử dụng dữ liệu fuzz**: Đối tượng tiếp cận bao gồm kiểu số, ký tự, siêu dữ liệu, chuỗi nhị phân, định dạng file, giao thức mạng. Cách tiếp cận chung là sinh tập dữ liệu giá trị nguy hiểm, chèn mã thực thi, phân tích hoạt động chương trình khi thực thi.
    - **Bước 5: Giám sát dữ liệu fuzz**: Định nghĩa các lỗi được phát hiện, có sự hiểu biết rõ về hoạt động xử lý, tích hợp vào sự kiện phân loại lỗi tự động.
    - **Bước 6: Xác định khả năng khai thác**: Fuzzer gửi danh sách lỗi cho đội ngũ phát triển sau khi xác định được.
- **Fuzzing khi chưa biết rõ giao thức**:
    - **Thách thức**: Tạo fuzzer cho các giao thức mở là vấn đề lớn, có thể dẫn đến tình huống không mong muốn (treo phần mềm, lỗi nghiêm trọng) nếu không hiểu rõ cấu trúc giao thức.
    - **Giải pháp**: Sử dụng kỹ thuật **dịch ngược** (reverse engineering) hoặc các công cụ **giám sát mạng** như **Wireshark** để nắm bắt lưu lượng đến/đi và cô lập dữ liệu lớp ứng dụng.

#### 6. Phương pháp khai thác khi tìm ra lỗ hổng

- Sau khi tìm ra vấn đề, có thể sử dụng **phân tích tĩnh, phân tích động hoặc kết hợp cả hai**.
- **Phân tích tĩnh**: Xác định cách tiếp cận mã nguồn có lỗ hổng khi chương trình đang thực hiện.
- **Phân tích động**: Thử nghiệm chống lại một chương trình đang chạy để xác nhận phân tích tĩnh.
- **Fuzzer**: Dữ liệu fuzzer cần được chia thành các phần cần thiết cho việc trích đường dẫn mã nguồn.

##### 6.1. Kết hợp phân tích tĩnh và phân tích động

- **Phân tích tĩnh**:
    - **Định nghĩa**: Phân tích mã nguồn phần mềm **mà không cần thực thi chương trình**.
    - **Mục đích**: Tìm lỗ hổng bảo mật, kiểm tra tính đúng đắn của mã nguồn, đưa ra biện pháp khắc phục.
    - **Công cụ**: Trình biên dịch, trình phân tích cú pháp, trình phân tích tĩnh.
    - **Hạn chế**: Chỉ giúp tìm ra các lỗ hổng có thể được phát hiện trong mã nguồn.
- **Phân tích động**:
    - **Định nghĩa**: Phân tích phần mềm bằng cách **thực thi chương trình** để tìm lỗ hổng bảo mật.
    - **Mục đích**: Tìm lỗ hổng mà **không cần mã nguồn** của phần mềm.
    - **Công cụ**: Trình chụp màn hình, trình gỡ lỗi (debugger), trình kiểm tra dữ liệu đầu vào.
    - **Hạn chế**: Chỉ giúp tìm ra các lỗ hổng có thể được phát hiện trong quá trình thực thi chương trình.

##### 6.2. Xem xét khả năng khai thác

- **Khả năng khai thác**: Phụ thuộc vào nhiều yếu tố (tương tác với phần mềm, độ phức tạp của lỗ hổng, khả năng kiểm soát luồng dữ liệu, khả năng tràn bộ đệm). Nếu cao, có thể khai thác để kiểm tra tính bảo mật.
- **Gỡ lỗi cho khai thác**: Sau khi xác định, cần tiến hành gỡ lỗi để tìm nguyên nhân và biện pháp khắc phục. Sử dụng bộ gỡ lỗi (debugger) cung cấp cái nhìn rõ ràng về cách dữ liệu đầu vào gây lỗi dừng.
- **Phân tích ban đầu**: Xác định vị trí và nguyên nhân lỗi. Trả lời câu hỏi: tại sao chương trình bị lỗi dừng đột ngột và ở vị trí nào.
- **Chỉ dẫn phân tích con trỏ**: Nếu con trỏ lệnh (**eip** trên x86) trỏ đến mã hợp lệ, lệnh trước đó là nguyên nhân. Phân tích lệnh và thanh ghi để tìm nguyên nhân. Nếu eip trỏ đến vị trí bất kỳ, xác định liệu có thể chèn mã vào vị trí đó hoặc kiểm soát eip để chuyển hướng đến dữ liệu người dùng cung cấp.
- **Phân tích thanh ghi**: Xem xét các thanh ghi để hiểu thông tin quan trọng được lưu trữ và cách chúng được sử dụng trong thực thi chương trình (giá trị, địa chỉ bộ nhớ).
- **Nâng cao độ tin cậy của khai thác**: Tìm hiểu nội dung thanh ghi để tìm địa chỉ của **shellcode** và thực hiện bước nhảy gián tiếp vào shellcode. Các kỹ thuật: sử dụng tràn bộ đệm để tìm `jmp esp` hoặc `call esp`; sử dụng `getopcode` hoặc `msfpescan` để tìm lệnh `jmp` hoặc `call` trong mã máy Linux/Windows.

##### 6.3. Tạo payload để khai thác

- **Nghiên cứu xây dựng payload**: Quá trình tạo ra một **đầu vào chính xác để khai thác lỗ hổng**, có thể là mã độc được chèn vào các trường hoặc bộ đệm để thực hiện hành động xâm nhập.
- **Các yếu tố tạo payload**:
    - **Các phần tử giao thức**: Để đưa ứng dụng có lỗ hổng theo đường dẫn chính xác.
    - **Padding, NOP hoặc các phần tử khác**: Để thay đổi bộ đệm, tạo sự khác biệt giữa các đầu vào.
    - **Khai thác việc kích hoạt dữ liệu**: Ví dụ địa chỉ trả về hay địa chỉ ghi. Để khai thác lỗ hổng và thực hiện xâm nhập.
    - **Các mã thực thi (Payload/shellcode)**: Để thực hiện hành động xâm nhập.
- **Tầm quan trọng**: Việc tạo payload đúng cách rất quan trọng để thành công trong tấn công. Nếu sai, công cụ khai thác sẽ không hoạt động chính xác.
- **Các vấn đề gây kết quả sai**:
    - Thành phần giao thức sai.
    - Địa chỉ trả về không khớp.
    - Dữ liệu điều khiển heap sai.
    - Đặt nhầm vị trí shellcode.
    - Dữ liệu đầu vào chứa ký tự đặc biệt làm sai vị trí trong bộ nhớ.
    - Chương trình đích thực hiện chuyển đổi bộ đệm khiến shellcode bị sửa đổi.
- **Các phần tử giao thức payload**: Cần biết đầy đủ các giao thức dẫn tới phần chứa lỗ hổng và tạo payload để chèn vào bộ nhớ.
- **Các vấn đề liên quan tới bộ đệm**: Liên quan đến **khai thác tràn bộ đệm**. Khi tràn, thông tin điều khiển bị thay đổi, người khai thác có thể nắm quyền điều khiển. Sắp xếp lại ngăn xếp bằng cách đặt các biến không phải mảng giữa các bộ đệm trên ngăn xếp và địa chỉ trả về có thể gây khó khăn. Cần cân nhắc số biến được sử dụng và khi nào chương trình có thể dừng bất thường nếu có giá trị bị thay đổi.

#### 7. Các phương pháp phòng ngừa khai thác lỗ hổng

- **Xem xét tiêu chuẩn đánh giá rủi ro**:
    - Dịch vụ có thực sự cần thiết không? Nếu không, tắt nó đi.
    - Dịch vụ có thể được tiếp cận công khai không? Nếu không, dùng tường lửa bảo vệ.
    - Tất cả các tùy chọn không an toàn đã được tắt chưa? Nếu không, cần thay đổi.
- **Port knocking**:
    - Áp dụng để **giới hạn người dùng** bảo vệ dịch vụ mạng.
    - Sử dụng một **chuỗi cổng để đóng/mở truy nhập** đến dịch vụ mạng, người dùng phải trải qua trình tự gõ cần thiết để kết nối.
    - **Hạn chế**: Không phải cơ chế bảo vệ thích hợp cho dịch vụ truy nhập công cộng. **Không giải quyết các lỗ hổng mà chỉ gây khó khăn hơn khi tiếp cận**.
- **Di chuyển**:
    - **Phương pháp di chuyển đến một hệ điều hành mới hoặc ứng dụng mới** có thể cải thiện an ninh bằng cách chống lại lỗ hổng.
    - Cần xem xét tính năng bảo mật và khả năng chống lại khai thác của HĐH/ứng dụng mới.
    - **Thách thức**: Thiếu lựa chọn thay thế, di chuyển dữ liệu, tác động đến người dùng. Cần đánh giá kỹ lưỡng.
- **Tạo bản vá (Patching)**:
    - **Cách duy nhất để bảo vệ ứng dụng và tránh khoảng thời gian dài đối mặt với lỗ hổng**.
    - Nếu không có quyền truy cập mã nguồn, cách đơn giản nhất là chờ nhà cung cấp cấp bản vá (có thể mất thời gian).
    - Nếu mã nguồn là mở, có thể tự vá các lỗ hổng.
    - **Vá mã nguồn mở**:
        - Dễ dàng sửa lỗi hơn so với mã nguồn nhị phân, người dùng có thể đóng góp.
        - Phải đảm bảo không gây ra lỗ hổng mới và hiểu rõ kiến trúc hệ thống.
        - Sử dụng công cụ **diff** và **patch** để tạo và áp dụng bản vá.
    - **Vá nhị phân**:
        - Khi không thể truy nhập mã nguồn gốc (ví dụ: lỗ hổng không còn được nhà cung cấp hỗ trợ, nhà cung cấp không/chậm đưa ra bản vá).
        - Bất kỳ thay đổi nào với đoạn mã nhị phân đã biên dịch cần đảm bảo hoạt động của chương trình được sửa chữa và cấu trúc tệp tin nhị phân không bị hỏng.
        - Có thể sử dụng phương pháp đặt các vị trí lệnh mới (lỗ) trong không gian ảo của chương trình nhị phân để bỏ qua mã của lỗ hổng.
        - Lưu ý vấn đề phân phối khi bản vá nhị phân được tạo và thử nghiệm thành công.


---
# In layman's term
## Kỹ thuật fuzzing



Hãy tưởng tượng bạn có một chiếc máy bán hàng tự động mới toanh, và bạn muốn biết liệu nó có bị hỏng nếu ai đó đưa vào những thứ kỳ lạ, không đúng quy cách hay không. Kỹ thuật Fuzzing cũng hoạt động theo một cách tương tự như vậy đấy.

Dưới đây là các điểm chính về Fuzzing:

- **Fuzzing là gì?**
    
    - Nói một cách đơn giản, **Fuzzing là một cách để tìm lỗi trong phần mềm** bằng cách **tự động hoặc bán tự động tạo ra và đưa thật nhiều dữ liệu "linh tinh", "bất thường" hoặc "không hợp lệ"** vào một chương trình máy tính.
    - Sau đó, người ta sẽ **theo dõi xem chương trình đó phản ứng thế nào** – liệu nó có bị lỗi, bị treo, hay hoạt động sai lệch không.
    - Những dữ liệu "linh tinh" này có thể là: các giá trị số quá lớn/nhỏ, các ký tự ngẫu nhiên, các chuỗi dữ liệu không mong đợi, hoặc các định dạng file bị hỏng.
- **Tại sao lại dùng Fuzzing?**
    
    - Mục tiêu chính là **tìm ra các lỗ hổng bảo mật** (những điểm yếu trong phần mềm) mà có thể khiến chương trình bị tấn công hoặc hoạt động không đúng.
    - Ví dụ, nó có thể giúp tìm ra các lỗi như:
        - **Buffer overflow (tràn bộ đệm):** Giống như bạn đổ quá nhiều nước vào một cái cốc nhỏ, làm nước tràn ra ngoài và làm hỏng mọi thứ xung quanh.
        - Các lỗi liên quan đến xác thực (ví dụ, chương trình chấp nhận mật khẩu sai).
        - Các lỗi làm chương trình bị dừng đột ngột (crash).
- **Đặc điểm chính của Fuzzing**:
    
    - Đây là một kỹ thuật **"kiểm thử hộp đen"**. Điều này có nghĩa là bạn **không cần phải xem mã nguồn** (tức là "công thức" tạo ra chương trình) để thực hiện Fuzzing. Bạn chỉ cần biết cách tương tác với chương trình mà thôi.
    - Các công cụ hoặc chương trình dùng để thực hiện Fuzzing được gọi là **Fuzzer**.
- **Ưu điểm (Lợi ích)**:
    
    - **Rất hiệu quả trong việc tìm ra các lỗi bảo mật nghiêm trọng**.
    - Nhiều lỗi được tìm thấy bằng Fuzzing thường là những lỗi mà kẻ tấn công (hacker) hay lợi dụng, ví dụ như làm chương trình bị treo hoặc rò rỉ thông tin.
    - Có thể tìm thấy những lỗi mà các phương pháp kiểm thử khác khó phát hiện.
- **Nhược điểm (Hạn chế)**:
    
    - **Không thể tìm ra tất cả các loại lỗi bảo mật**. Ví dụ, nó kém hiệu quả với các lỗi không gây ra sự cố treo phần mềm (như virus hay trojan).
    - Nó không cung cấp nhiều thông tin chi tiết về hoạt động bên trong của phần mềm.
    - Với những chương trình có đầu vào rất phức tạp, việc tạo ra một fuzzer thông minh để kiểm tra có thể tốn nhiều thời gian.
- **Cách thức thực hiện (một cách đơn giản)**:
    
    - **Xác định mục tiêu:** Chọn phần mềm hoặc tính năng muốn kiểm tra.
    - **Xác định đầu vào:** Tìm hiểu xem chương trình nhận những loại dữ liệu nào (ví dụ: dữ liệu từ bàn phím, từ file, qua mạng).
    - **Tạo dữ liệu:** Tự động tạo ra một lượng lớn dữ liệu "linh tinh" như đã nói ở trên.
    - **Thực hiện kiểm tra:** Đưa các dữ liệu "linh tinh" này vào chương trình.
    - **Giám sát:** Theo dõi chặt chẽ chương trình xem nó có bị lỗi, treo, hay có thông báo bất thường nào không.
    - **Xác định khả năng khai thác:** Nếu tìm thấy lỗi, phân tích xem lỗi đó có thể bị kẻ xấu lợi dụng để tấn công hay không.

Tóm lại, **Fuzzing giống như việc bạn cố tình "phá hoại" một chương trình bằng cách đưa vào những thứ "điên rồ" để xem nó có "sập" không, và nếu có, "sập" vì lý do gì, để từ đó chúng ta vá lại "lỗ hổng" đó**.

