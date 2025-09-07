---
{"dg-publish":true,"permalink":"/3-archieved/kiem-thu-xam-nhap/on-thi/cheatsheet-chuong-2/","title":"KTXN - Cheatsheet chương 2","tags":["cheatsheet","tutran-garden"],"created":"2025-05-30T01:05:51.000+07:00"}
---


# Cheetsheet - Prompt 1

**Chương 2: Một số dạng kiểm thử xâm nhập**
Nội dung chính bao gồm:
- Kỹ thuật Xã hội (Social Engineering)
- Kiểm thử Vật lý (Physical Penetration Testing)

---

## 1. Kỹ thuật Xã hội (Social Engineering)

- **Khái niệm:**
    
    - Kỹ thuật Xã hội là nghệ thuật thuyết phục mọi người tiết lộ thông tin bí mật.
    - Nó tấn công vào **yếu tố con người**.
    - Social Engineering phụ thuộc vào việc mọi người không biết hoặc **bất cẩn trong việc bảo vệ thông tin**.
    - Không có bất kỳ **bản vá lỗi nào đối với một con người ngu ngốc**.
- **Tại sao Social Engineering hiệu quả:**
    
    - **Không có phần mềm hay phần cứng nào chống lại** nó.
    - **Không có phương pháp chắc chắn** để đảm bảo an ninh hoàn toàn khỏi Social Engineering.
    - Ngay cả chính sách bảo mật mạnh cũng có thể có **liên kết yếu nhất là con người**.
    - Rất **khó để phát hiện** ra Social Engineering.
- **Các yếu tố làm doanh nghiệp dễ bị tấn công:**
    
    - Thiếu **đào tạo hiểu biết về an toàn thông tin** cho nhân viên.
    - Thiếu **chính sách an ninh**.
    - Nhiều đơn vị tổ chức.
    - **Dễ dàng truy cập thông tin**.
- **Dấu hiệu của một cuộc tấn công Social Engineering:**
    
    - Không cung cấp số gọi lại.
    - Yêu cầu phi chính thức.
    - Yêu cầu thẩm quyền và đe dọa nếu không cung cấp thông tin.
    - Cho thấy sự vội vàng và vô tình để lại tên.
    - Bất ngờ được khen tặng hoặc ca ngợi.
    - Khó chịu khi đặt câu hỏi.
- **Các giai đoạn trong một cuộc tấn công Social Engineering:**
    
    - **Nghiên cứu mục tiêu:** Tìm hiểu thông tin qua thùng rác (Dumpster diving), trang web, nhân sự, lịch trình....
    - **Lựa chọn nạn nhân:** Xác định nhân viên không hài lòng với chính sách công ty.
    - **Phát triển mối quan hệ:** Xây dựng quan hệ với nhân viên đã chọn.
    - **Khai thác mối quan hệ:** Thu thập thông tin tài khoản nhạy cảm, thông tin tài chính, công nghệ hiện tại.
- **Ảnh hưởng lên tổ chức khi bị tấn công:**
    
    - Mất sự riêng tư.
    - Tổn hại uy tín.
    - Mất mát về kinh tế.
    - Chính sách khủng bố.
    - Các vụ kiện và thủ tục.
    - Tạm thời hoặc vĩnh viễn đóng cửa.
- **Các phương pháp tấn công:**
    
    - **Online:** Tấn công qua Internet, thuyết phục nhân viên cung cấp thông tin từ nguồn ẩn danh.
    - **Telephone:** Yêu cầu thông tin qua điện thoại, thường giả mạo người dùng hợp pháp.
    - **Tiếp cận trực tiếp:** Lấy thông tin bằng cách hỏi trực tiếp đối tượng.
- **Những mục tiêu phổ biến:**
    
    - Nhân viên tiếp tân và hỗ trợ.
    - Người dùng và khách hàng.
    - Người bán hàng của doanh nghiệp.
    - Người quản trị hệ thống.
    - Giám đốc hỗ trợ kỹ thuật.
    - Nhân viên văn phòng (thu thập chính sách bảo mật, tài liệu nhạy cảm, cấu trúc mạng, mật khẩu).
- **Các kiểu Social Engineering:**
    
    - **Human-based:** Thu thập thông tin nhạy cảm bằng cách khai thác sự tin tưởng, sợ hãi và sự giúp đỡ.
        - **Mạo danh (Impersonation):** Giả mạo thành người hoặc vật nào đó (người dùng chính thống, người có thẩm quyền, khách hàng VIP, nhân viên hỗ trợ kỹ thuật).
        - **Eavesdropping:** Nghe lén (không được đề cập chi tiết trong nguồn).
        - **Shoulder Surfing:** Nhìn trộm qua vai để lấy thông tin (không được đề cập chi tiết trong nguồn).
        - **Dumpster Diving:** Tìm kiếm thông tin trong thùng rác.
        - **Piggybacking:** Người không có thẩm quyền đi theo người có thẩm quyền để vào khu vực giới hạn, thường với sự cho phép của người có thẩm quyền (VD: quên thẻ ID).
        - **Tailgating:** Người không có thẩm quyền đi theo sát người có thẩm quyền để vào khu vực giới hạn (VD: dùng ID giả và theo sát).
    - **Computer-based:** Sử dụng máy tính hoặc phần mềm để lấy thông tin.
        - **Pop-Ups:** Cửa sổ bật lên lừa đảo, chuyển hướng đến trang web giả mạo yêu cầu thông tin cá nhân hoặc tải phần mềm độc hại.
        - **Phishing:** Email giả mạo từ trang web hợp pháp, cố gắng lấy thông tin cá nhân hoặc tài khoản người dùng. Email hoặc Pop-up chuyển hướng đến trang web giả mạo bắt chước trang web thật.
        - **Social Engineering sử dụng SMS (Smishing):** Tin nhắn SMS giả mạo yêu cầu cung cấp thông tin nhạy cảm (VD: trường hợp Tracy với ngân hàng XIM).
- **Tấn công Insider (Nội bộ):**
    
    - **Spying:** Đối thủ cài người vào làm việc trong tổ chức mục tiêu.
    - **Revenge:** Người bất mãn trong công ty gây tổn hại.
    - **60% các cuộc tấn công xảy ra phía sau tường lửa**.
    - Tấn công nội bộ dễ khởi động và khó phòng chống.
    - Nhân viên bất mãn có thể cung cấp bí mật công ty cho đối thủ.
- **Social Engineering thông qua mạo danh trên các mạng xã hội:**
    
    - Mạo danh (Impersonation) là bắt chước hành vi của người khác.
    - Sử dụng mã độc để thu thập thông tin bí mật từ mạng xã hội và tạo tài khoản giả.
    - Kẻ tấn công sử dụng hồ sơ giả để tạo mạng lưới bạn bè lớn, trích xuất thông tin cho Social Engineering.
    - Thông tin thu thập có thể dùng cho các hình thức Social Engineering khác (VD: Chi tiết về tổ chức, nghề nghiệp, địa chỉ liên lạc, cá nhân).
    - Ví dụ: Tấn công trên **Facebook** tạo nhóm giả mạo nhân viên để lấy thông tin cá nhân (ngày sinh, trường lớp, quê quán, hôn nhân...) để truy cập tòa nhà công ty.
- **Rủi ro của mạng xã hội với mạng công ty:**
    
    - Cơ sở dữ liệu khổng lồ, nhiều người truy cập, tăng nguy cơ khai thác thông tin (Ăn cắp dữ liệu).
    - Nhân viên vô tình gửi dữ liệu nhạy cảm lên mạng xã hội nếu không có chính sách mạnh mẽ (Không cố ý làm rò rỉ thông tin).
    - Thông tin trên mạng xã hội dùng cho thăm dò sơ bộ trong tấn công mục tiêu (Tấn công mục tiêu).
    - Mạng xã hội có thể có sai sót/lỗi, dẫn đến lỗ hổng trong mạng công ty (Lỗ hổng hệ thống mạng).
- **Ăn cắp danh tính (Identity Theft):**
    
    - Xảy ra khi ai đó lấy tên và thông tin cá nhân khác của bạn cho mục đích gian lận.
    - Không gian ảo làm việc ăn cắp Identity dễ dàng hơn.
    - Mất số an ninh xã hội hoặc bằng lái xe có thể nguy hiểm.
    - **Ví dụ quy trình ăn cắp danh tính:** Lấy cắp hóa đơn (Dumpster Diving/Email/Trộm tại chỗ) -> Giả mất bằng lái xe tại sở GTVT dùng hóa đơn lấy cắp làm bằng chứng, thay đổi địa chỉ -> Đến ngân hàng mở thẻ tín dụng mới bằng tên và địa chỉ lấy cắp.
    - Đây là vấn đề nghiêm trọng, số vụ vi phạm tăng lên.
- **Biện pháp đối phó với Social Engineering:**
    
    - **Chính sách:** Chính sách và thủ tục tốt cần được giảng dạy và trang bị cho nhân viên. Nhân viên cần ký tuyên bố thừa nhận hiểu chính sách.
        - **Chính sách về mật khẩu:** Thay đổi định kỳ, tránh mật khẩu dễ đoán, khóa tài khoản khi đăng nhập thất bại, mật khẩu phải có độ dài và phức tạp.
        - **Chính sách an ninh vật lý:** Phát thẻ ID/đồng phục, hộ tống khách mời, hạn chế khu vực truy cập, tiêu hủy/băm nhỏ tài liệu, tuyển dụng nhân viên an ninh.
    - **Đào tạo:** Chương trình đào tạo hiệu quả bao gồm chính sách bảo mật và phương pháp nâng cao nhận thức về Social Engineering.
    - **Nguyên tắc hoạt động:** Đảm bảo an ninh thông tin nhạy cảm và ủy quyền sử dụng tài nguyên.
    - **Phân loại thông tin:** Phân loại thông tin (tối mật, độc quyền, nội bộ, công cộng).
    - **Đặc quyền truy cập:** Quản trị viên, người dùng tài khoản phải được ủy quyền phù hợp.
    - **Kiểm tra nhân viên và xử lý đình chỉ đúng đắn:** Kiểm tra lý lịch và có quy trình xử lý phù hợp cho nhân viên bị thôi việc hoặc có tiềm tàng hình sự.
    - **Tần suất phản hồi thích hợp:** Cần có phản ứng thích hợp cho những trường hợp cố gắng sử dụng Social Engineering.
    - **Xác thực hai yếu tố:** Sử dụng cho các dịch vụ mạng có nguy cơ cao (VPN, Modem Pool) thay vì mật khẩu cố định.
    - **Phòng thủ Anti-Virus/Anti-Phishing:** Sử dụng nhiều lớp phòng chống (người dùng cuối, mail gateway) để giảm tấn công Social Engineering.
    - **Thay đổi công tác quản lý:** Thay đổi quy trình quản lý tài liệu để bảo mật hơn.
    - **Phát hiện Email giả mạo:** Chứa liên kết đến trang web giả, có vẻ đến từ tổ chức hợp pháp, giống người quen, yêu cầu gọi điện cung cấp thông tin, bao gồm logo và thông tin lấy từ trang web hợp pháp.
    - **Biện pháp đối phó việc đánh cắp Identity:** Xé nhỏ tài liệu cá nhân, giữ hòm thư an toàn, kiểm tra báo cáo thẻ tín dụng thường xuyên, không đưa thông tin cá nhân qua điện thoại, bảo vệ thông tin công khai....
- **Kiểm thử Social Engineering:**
    
    - **Mục tiêu:** Kiểm tra yếu tố con người trong chuỗi bảo mật.
    - Thường dùng để **nâng cao nhận thức bảo mật** giữa nhân viên.
    - Người kiểm thử cần cẩn thận, chuyên nghiệp do liên quan vấn đề pháp lý, quyền riêng tư.
    - **Kỹ năng cần có:** Kỹ năng làm việc tốt giữa các cá nhân, giao tiếp tốt, trò chuyện thân thiện tự nhiên, sáng tạo.

---

## 2. Kiểm thử Vật lý (Physical Penetration Testing)

- **Khái niệm:**
    
    - Xâm nhập vật lý là phương pháp tội phạm mạng **truy nhập vào cơ sở hạ tầng mạng dữ liệu từ phía trong** của công ty.
    - Một khi vào được bên trong, cơ hội tấn công là rất nhiều.
    - Kiểm thử xâm nhập vật lý giúp đánh giá chính xác **hiệu quả của chính sách kiểm soát an toàn vật lý**.
- **Tại sao xâm nhập vật lý nguy hiểm:**
    
    - Tất cả biện pháp bảo mật kỹ thuật số (tường lửa, IDS...) **vô dụng** khi xâm nhập vật lý thành công.
    - Các tổ chức **chưa quan tâm đúng mức** đến kiểm thử vật lý.
- **Phân biệt các team (trong bối cảnh kiểm thử bảo mật tích hợp):**
    
    - **Red Team:**
        - Tập trung **kiểm tra khả năng thâm nhập** và mức độ bảo mật của hệ thống.
        - Giúp phát hiện, ngăn chặn, loại bỏ điểm yếu bằng cách tấn công lỗ hổng.
        - Sử dụng tất cả kỹ thuật thâm nhập mạng và dữ liệu.
    - **Blue Team:**
        - **Bảo vệ an ninh mạng** cho tổ chức, phát hiện lỗ hổng.
        - Có trách nhiệm tăng cường phòng thủ, xử lý nhanh lỗ hổng khi bị tấn công.
- **Phương pháp thực hiện kiểm thử vật lý:**
    
    - **Các bước thực hiện:**
        1. Xác định mục tiêu và phạm vi.
        2. Thu thập thông tin.
        3. Phân tích sơ bộ.
        4. Trinh sát (bị động và chủ động).
        5. Đánh giá tình hình.
        6. Lên kế hoạch và phân tích.
        7. Luyện tập.
        8. Thực hiện tấn công.
    - **Lên kế hoạch và đánh giá:**
        - **Thu thập thông tin:** Tìm hiểu tổ chức mục tiêu, tài sản, nơi cất giấu.
        - **Trinh sát bị động:** Tìm hiểu địa điểm mục tiêu, địa hình xung quanh, đường lái xe, cửa, lỗ hổng, đường thoát.
        - **Trinh sát chủ động:** Giám sát nhân viên/bảo vệ, tìm hiểu đồng phục/huy hiệu, vị trí thang máy, khu vực mù camera/cảm biến, dạo quanh khu vực công cộng, xác định phòng họp, mạng không dây, bản đồ khẩn cấp.
        - **Đánh giá tình hình:** Đánh giá cơ hội trò chuyện với nhân viên, thu thập thông tin về nhân viên.
    - **Thực hiện tấn công:**
        - **Vượt qua kiểm soát truy cập:** Bẻ khóa (Lock Picking), Tailgating, Key pad, Biometric, Thẻ (Contactless, Smartcard, Magnetic), Lối truy cập vật lý không được kiểm soát (Cửa sổ, Nhà để xe).
        - **Vượt qua cảm biến và báo động:** Cảm biến chuyển động (PIR, Quang điện, Siêu âm), Cảm biến từ tính, Chống nhiễu cho hệ thống liên lạc.
        - **Vượt qua hệ thống giám sát**.
        - **Sử dụng tấn công Social Engineering** để có quyền truy cập vật lý.
        - **Khai thác và truy cập mạng công ty (áp dụng Red Team):** Cửa hậu vật lý (PwnPlg, Raspberry...), Thiết bị bên ngoài (Keylogger, Network Sniffer...), Truy cập máy tính không bảo vệ (Kon-Boot...), Chặn cuộc gọi (Điện thoại, VoIP), Thiết bị phần cứng.
        - **Lấy thông tin bí mật**.
- **Tổng kết:**
    
    - Kiểm thử vật lý đòi hỏi sự **sáng tạo và tư duy**.
    - Cách tiếp cận của **Red Team** là giải pháp để tiến hành đánh giá bảo mật tích hợp toàn diện.


