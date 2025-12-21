---
{"dg-publish":true,"dg-permalink":"2025/stego/slide-script","permalink":"/2025/stego/slide-script/","title":"Script thuyết trình","created":"2025-12-21T19:52:06.640+07:00","updated":"2025-12-21T19:53:03.141+07:00"}
---




### Lý do chọn đề tài
Kính thưa Hội đồng,
Trong kỷ nguyên số hiện nay, kỹ thuật giấu tin (Steganography) đang phát triển rất nhanh. Bên cạnh lợi ích bảo vệ bản quyền, nó đang tạo ra một lo ngại lớn về an ninh khi bị kẻ xấu lợi dụng để giấu mã độc hoặc đánh cắp dữ liệu, dễ dàng qua mặt các hệ thống giám sát thông thường.

Trong các loại dữ liệu, **âm thanh** là môi trường cực kỳ thích hợp để giấu tin nhờ đặc điểm tín hiệu đa dạng và giới hạn thính giác của con người .

Tuy nhiên, việc phát hiện tin giấu trong âm thanh là một thách thức lớn. Các phương pháp truyền thống thường chỉ hiệu quả với các kỹ thuật đơn giản như LSB, và nó cũng gặp hạn chế nếu gặp các kỹ thuật mới.

Chính vì vậy, nhóm quyết định lựa chọn đề tài **'Nghiên cứu phát hiện giấu tin trong âm thanh dựa trên học máy'**. Chúng em tin rằng việc áp dụng Học máy để phân tích sâu các đặc trưng trong miền thời gian, tần số và cảm nhận sẽ giúp nâng cao đáng kể độ chính xác trong việc phát hiện, tạo tiền đề cho các giải pháp bảo mật hiệu quả hơn."

### Phân tích vấn đề và quy trình

Tuy nhiên, khi bắt tay vào phân tích đề tài để áp dụng học máy, chúng em đối mặt với một rào cản lớn: đó là sự **thiếu hụt dữ liệu chuẩn**. Các bộ dữ liệu công khai hiện có rất hạn chế hoặc không rõ ràng về thuật toán tạo ra.

Để mô hình học máy hoạt động chính xác, chúng em buộc phải tự tạo ra dữ liệu. Nhưng dữ liệu này không thể tạo bừa bãi. Một quy trình giấu tin hợp lệ trong thực tế đòi hỏi tin nhắn sau khi giấu **phải tách ra được** nguyên vẹn. Nếu chỉ giấu mà không tách được thì đó chỉ là nhiễu, không phải là Steganography.

Chính vì vậy, nhiệm vụ tiên quyết được đặt ra là phải **xây dựng thành công code mô phỏng quy trình giấu và tách tin** chuẩn xác cho các thuật toán.

Đồng thời, trong quá trình xây dựng công cụ này, em nhận thấy nền tảng thực hành an toàn thông tin **Labtainer vẫn chưa có các bài Lab về chủ đề giấu tin âm thanh**. Vì thế, em đã tích hợp quy trình này thành các bài Lab để phục vụ tốt hơn cho việc tham khảo các kỹ thuật giấu tin.

### Đối tượng nghiên cứu 
Từ phân tích trên, nhiệm vụ nghiên cứu của đề tài được phân chia cụ thể như sau:

**Em (Trà My) đảm nhận vai trò xây dựng nền tảng kỹ thuật.** Cụ thể, em nghiên cứu lý thuyết và viết mã nguồn mô phỏng cho 5 kỹ thuật: LSB, Phase Coding, Spread Spectrum, STSM và Echo Hiding. Em đảm bảo rằng thuật toán chạy đúng, tin giấu tách ra được và đạt chất lượng PSNR tiêu chuẩn. Từ mã nguồn này, em đóng gói thành 16 bài Lab trên Labtainer.

**Bạn Hưởng sẽ đảm nhận vai trò khai thác và ứng dụng.** Bạn sẽ sử dụng mã nguồn do em xây dựng để chạy sinh dữ liệu hàng loạt, và quyết định việc chia bộ dữ liệu train/test như thế nào cho mô hình và huấn luyện mô hình học máy.

### Sơ đồ tổng quát về mô phỏng
Đi vào phần triển khai kỹ thuật, em đã xây dựng một quy trình mô phỏng cho cả 5 thuật toán.

Điểm mấu chốt trong quy trình của em là bước **Kiểm chứng (Validation)**. Sau khi nhúng tin, hệ thống bắt buộc phải thực hiện giải mã ngược lại. Chỉ những file âm thanh nào cho phép tách ra thông điệp toàn vẹn mới được coi là dữ liệu hợp lệ (Valid Stego Audio). Điều này đảm bảo bộ dataset em chuyển cho bạn Hưởng là sạch và chính xác về mặt kỹ thuật, loại bỏ các trường hợp file bị lỗi hoặc tin bị vỡ.

### Minh họa 1 kỹ thuật (Echo Hiding)
Do thời gian có hạn, em xin phép lấy **Echo Hiding** làm ví dụ đại diện cho quá trình nghiên cứu.

Khác với LSB chỉ thay đổi bit, Echo Hiding nhúng tin bằng cách tạo ra các tiếng vọng nhân tạo cực ngắn. Em sử dụng hai độ trễ khác nhau để mã hóa bit 0 và bit 1. Thách thức ở đây là phải tinh chỉnh biên độ và độ trễ sao cho tiếng vọng hòa vào tín hiệu gốc, khiến tai người cảm thấy âm thanh tự nhiên nhưng máy tính vẫn phân biệt được.

Việc cài đặt thành công thuật toán này chứng minh tính đa dạng của bộ dữ liệu, không chỉ dừng lại ở các thay đổi đơn giản.

### Các bài lab (Hiện thực hóa quy trình mô phỏng trên Labtainer)

Sau khi nghiên cứu lý thuyết, bước đầu tiên của em là hiện thực hóa các thuật toán này thành mã nguồn chạy được và đảm bảo tính đúng đắn của quy trình giấu tin.

Để kiểm chứng điều này, em đã xây dựng và đóng gói thành công **16 bài Lab** trên nền tảng Labtainer, bao phủ toàn bộ 5 kỹ thuật từ đơn giản như LSB đến phức tạp như Echo Hiding hay Spread Spectrum.

Trong mỗi bài Lab, hệ thống bắt buộc người dùng không chỉ giấu tin mà còn phải thực hiện **tách tin thành công** từ file Stego. Điều này chứng minh thuật toán hoạt động chính xác, thông điệp được khôi phục nguyên vẹn, đảm bảo đây là quy trình Steganography chuẩn chứ không phải chỉ là làm nhiễu tín hiệu.

Tuy nhiên, code chạy đúng là chưa đủ. Để sinh được dữ liệu cho mô hình học máy, file âm thanh giả mạo phải có chất lượng thật tốt để 'đánh lừa' được tai người. Vì vậy, em chuyển sang bước tối ưu tham số.

### Cấu hình tham số (tinh chỉnh tham số)
Sau khi đã có bộ code hoạt động chính xác trên môi trường Lab, em tiến hành bước quan trọng tiếp theo là **tinh chỉnh tham số** để tối ưu hóa chất lượng âm thanh. Mục tiêu là file sau khi giấu phải nghe tự nhiên nhất để đánh lừa thính giác con người.

Vì trong quá trình làm thì thời lượng có hạn nên bọn em sẽ tập trung vào tinh chỉnh tham số cho 3 kỹ thuật chính để sinh dữ liệu hàng loạt dựa vào 3 kỹ thuật này.

Ví dụ, với kỹ thuật **Echo Hiding** (một trong những kỹ thuật chủ đạo để sinh dataset), em đã  thử nghiệm nhiều cặp giá trị độ trễ (Delay) và hệ số suy giảm (alpha) khác nhau.

Nếu độ trễ quá lớn, âm thanh sẽ bị vang như trong hang động, rất dễ lộ. Nếu quá nhỏ, máy sẽ không tách được tin. Sau quá trình cân chỉnh, em đã tìm ra bộ tham số như trên giúp thuật toán đạt độ bền vững (Robustness) tốt mà vẫn giữ được chất lượng tín hiệu.

### Kết quả đo đạc
Kết quả đo đạc cuối cùng cho thấy, với các bộ tham số đã chọn, các thuật toán đều đạt chỉ số PSNR ở mức cao. Cụ thể, kỹ thuật LSB đạt trung bình >40dB, và Echo Hiding và Phase coding đạt >30 dB.

Mức PSNR này đảm bảo rằng các file âm thanh được sinh ra (Stego Audio) có chất lượng cao, rất khó phân biệt bằng tai thường. Đây chính là cơ sở tin cậy để nhóm tiến hành sinh hàng nghìn mẫu dữ liệu huấn luyện cho mô hình học máy mà không sợ bị sai lệch do nhiễu lạ.

---
Với quy trình mô phỏng và bộ tham số sau khi tinh chỉnh mà em vừa trình bày, nhóm đã có đủ cơ sở để sinh bộ dữ liệu chuẩn. Sau đây, xin mời bạn Hưởng trình bày cách chúng em sử dụng dữ liệu này để huấn luyện mô hình phát hiện giấu tin.


# Một số câu hỏi vấn đáp
Với tư cách là một người đóng vai "Hội đồng phản biện" (thường bao gồm các thầy cô khó tính và rất soi tiểu tiết), tôi sẽ đặt ra các câu hỏi xoay quanh 3 trụ cột chính trong phần việc của bạn: **Độ hiểu sâu về thuật toán**, **Chất lượng dữ liệu sinh ra**, và **Giá trị thực tiễn của sản phẩm (Labtainer)**.

Dưới đây là các câu hỏi tiềm năng và gợi ý cách trả lời "ghi điểm":

### Nhóm 1: Câu hỏi về Kỹ thuật & Thuật toán (Kiểm tra kiến thức nền)

**Câu 1: "Tại sao em lại chọn nghiên cứu tận 5 thuật toán? Trong số này, thuật toán nào giấu tin 'bền' nhất (Robustness) và thuật toán nào có dung lượng giấu (Capacity) cao nhất?"**

- **Mục đích:** Kiểm tra xem bạn có hiểu bản chất của từng cái không hay chỉ chạy code cho có số lượng.
    
- **Gợi ý trả lời:**
    
    - _Dung lượng:_ LSB thường có dung lượng cao nhất (vì có thể thay thế nhiều bit).
        
    - _Độ bền:_ Spread Spectrum hoặc Echo Hiding thường bền hơn trước các tấn công như nén hay cộng nhiễu so với LSB.
        
    - _Lý do chọn 5 cái:_ Để tạo ra tập dữ liệu đa dạng (Diversity) cho mô hình học máy học được nhiều đặc trưng tấn công khác nhau, tránh việc mô hình bị "học vẹt" (overfitting) vào một kiểu giấu tin duy nhất.
        

**Câu 2: "Em nói PSNR cao (trên 40dB) là tốt. Nhưng PSNR cao chỉ đảm bảo tai người không nghe thấy. Vậy nếu tôi nén file MP3 hoặc lọc nhiễu thì tin giấu còn tách ra được không?"**

- **Mục đích:** "Xoáy" vào điểm yếu của Steganography. Trong báo cáo bạn có nhắc đến thử nghiệm tấn công nén/nhiễu.
    
- **Gợi ý trả lời:** "Thưa thầy, đúng là PSNR chỉ phản ánh độ trong suốt (Imperceptibility). Trong đồ án này, em tập trung chính vào việc tạo ra dataset 'sạch' (không có nhiễu) để huấn luyện mô hình phát hiện. Tuy nhiên, em cũng đã thử nghiệm (có bài Lab) về tấn công nén/nhiễu. Với LSB thì nén sẽ mất tin, nhưng với Echo Hiding thì khả năng tồn tại tốt hơn. Đây cũng là lý do em làm nhiều thuật toán để so sánh sự đánh đổi giữa _Chất lượng âm thanh_ và _Độ bền vững_."
    

**Câu 3: "Cơ chế Echo Hiding hoạt động thế nào? Làm sao để tạo tiếng vọng mà người nghe không thấy khó chịu?"**

- **Mục đích:** Kiểm tra kiến thức sâu về thuật toán bạn chọn làm điểm nhấn (Deep dive).
    
- **Gợi ý trả lời:** Giải thích ngắn gọn về độ trễ (delay) rất nhỏ (vài mili giây) và hệ số suy giảm (decay). Nếu delay < 2ms, tai người sẽ gộp âm gốc và âm vọng làm một, chỉ thấy âm thanh ấm hơn chứ không thấy tiếng vang rời rạc.
    

---

### Nhóm 2: Câu hỏi về Dữ liệu & Quy trình (Kiểm tra tính logic)

**Câu 4: "Em đảm bảo tính 'Valid' (hợp lệ) của dữ liệu đưa cho bạn Hưởng huấn luyện như thế nào? Lỡ em chỉ cộng nhiễu lung tung rồi bảo đó là giấu tin thì sao?"**

- **Mục đích:** Câu này cực kỳ quan trọng vì bạn là người cung cấp "nguyên liệu".
    
- **Gợi ý trả lời:** (Dùng chính luận điểm bạn vừa chuẩn bị) "Thưa thầy, quy trình mô phỏng của em có bước **Validation**. Mọi file sau khi giấu đều được đưa qua bộ giải mã (Decoder). Chỉ những file nào tách ngược lại được thông điệp gốc chính xác 100% (hoặc tỷ lệ lỗi bit BER = 0) mới được xuất vào dataset. Điều này đảm bảo dữ liệu là Steganography thực thụ."
    

**Câu 5: "Tham số của các thuật toán (ví dụ bit nào trong LSB, độ trễ bao nhiêu trong Echo) em chọn cố định hay ngẫu nhiên khi sinh dữ liệu?"**

- **Mục đích:** Xem xét độ phong phú của dataset.
    
- **Gợi ý trả lời:** "Em sử dụng cả hai. Một phần giữ cố định để kiểm chứng lý thuyết, một phần em random các tham số trong ngưỡng cho phép (ví dụ random độ trễ trong khoảng an toàn) để tăng tính tổng quát cho bộ dữ liệu, giúp mô hình học máy của bạn Hưởng thông minh hơn."
    

---

### Nhóm 3: Câu hỏi về Sản phẩm & Đóng góp (Labtainer)

**Câu 6: "Tại sao lại mất công làm tới 19 bài Lab trên Labtainer? Nó có thực sự cần thiết cho đồ án này không?"**

- **Mục đích:** Hỏi về giá trị gia tăng của đồ án.
    
- **Gợi ý trả lời:** "Thưa thầy, Labtainer là nền tảng thực hành ATTT phổ biến nhưng đang thiếu module về Steganography âm thanh. 19 bài Lab này không chỉ là sản phẩm phụ, mà là minh chứng cho việc em đã chuẩn hóa được quy trình. Nó giúp sinh viên khóa sau có thể tái hiện lại các tấn công này một cách trực quan thay vì chỉ đọc lý thuyết suông."
    

**Câu 7: "Khó khăn lớn nhất khi em cài đặt các thuật toán này là gì?"**

- **Mục đích:** Đánh giá công sức thực tế (Implementation effort).
    
- **Gợi ý trả lời:** "Khó khăn lớn nhất là cân bằng giữa **PSNR** và **Khả năng tách tin**. Ví dụ với Echo Hiding, chỉnh cho âm thanh hay thì lại không tách được tin, chỉnh cho tách được tin thì âm thanh lại bị vang quá. Em đã phải thử nghiệm rất nhiều bộ tham số (trial & error) để tìm ra điểm cân bằng tối ưu."
    

---

### Mẹo nhỏ khi trả lời vấn đáp (Pro Tips):

1. **Nếu gặp câu không biết:** Đừng chém gió. Hãy nói: _"Dạ vấn đề này em chưa đi sâu nghiên cứu trong phạm vi đồ án, nhưng theo suy luận của em dựa trên lý thuyết A/B thì..."_ hoặc _"Em xin ghi nhận góp ý này để phát triển hướng nghiên cứu tiếp theo ạ."_
    
2. **Đừng tranh cãi gay gắt:** Nếu thầy cô bảo "Cái này sai rồi", hãy bình tĩnh: _"Dạ, em đã thực nghiệm theo tài liệu [X] và ra kết quả như vậy, có thể do điều kiện thử nghiệm khác nhau. Em sẽ kiểm tra lại kỹ hơn ạ."_
    
3. **Bảo vệ đồng đội:** Nếu thầy hỏi bạn về Machine Learning (phần của Hưởng) quá sâu, hãy trả lời cơ bản và khéo léo chuyển: _"Về chi tiết tham số model, bạn Hưởng sẽ nắm rõ hơn, nhưng theo em hiểu thì..."_

# 📋 CONTEXT SUMMARY: ĐỒ ÁN TỐT NGHIỆP - AUDIO STEGANOGRAPHY


**1. Thông tin chung**

- **Tên đề tài:** Nghiên cứu phát hiện giấu tin trong âm thanh dựa trên học máy.
    
- **Thành viên:**
    
    - **Tôi (User - Người đang chat):** Đoàn Thị Trà My (B21DCAT134).
        
    - **Đồng đội:** Nguyễn Mạnh Hưởng (B21DCAT102).
        
- **Vấn đề giải quyết:** Các phương pháp phát hiện truyền thống kém hiệu quả; áp dụng Học máy (Machine Learning) nhưng gặp khó khăn do thiếu bộ dữ liệu chuẩn (dataset) và thiếu môi trường thực hành tấn công.
    

**2. Phân công nhiệm vụ (Scope of Work)**

- **Nhiệm vụ của TÔI (Phần Simulation & Education):**
    
    - **Vai trò:** Xây dựng "Engine" (công cụ lõi) để mô phỏng tấn công và tạo cơ sở dữ liệu.
        
    - **Kỹ thuật nghiên cứu (5 loại):** LSB, Phase Coding, Spread Spectrum, STSM, Echo Hiding.
        
    - **Công việc cụ thể:**
        
        - Viết code mô phỏng quy trình Giấu tin (Embed) và Tách tin (Extract) cho 5 thuật toán trên.
            
        - Đảm bảo tính đúng đắn: Tin giấu phải tách ngược lại được (Reversible).
            
        - Đánh giá chất lượng: Đo đạc PSNR, MSE để đảm bảo tính ẩn mật (Imperceptibility).
            
        - **Sản phẩm đặc biệt:** Xây dựng **19 bài Lab** thực hành trên nền tảng **Labtainer** (do nền tảng này chưa có module về giấu tin âm thanh).
            
    - _Lưu ý:_ Tôi **KHÔNG** thực hiện việc sinh dữ liệu hàng loạt (batch generation) hay chia tập dữ liệu train/test. Tôi chỉ cung cấp source code chuẩn để bạn Hưởng làm việc đó.
        
- **Nhiệm vụ của ĐỒNG ĐỘI (Phần Machine Learning):**
    
    - Sử dụng code của tôi để sinh dataset quy mô lớn (Batch generation) với 3 kỹ thuật chính (LSB, Echo Hiding, Phase).
        
    - Trích xuất đặc trưng (Feature Extraction): Time, Frequency, Perceptual domains.
        
    - Huấn luyện mô hình: Sử dụng thuật toán **Random Forest**.
        
    - Mục tiêu: Phân loại nhị phân (Có giấu tin vs Không giấu tin).
        

**3. Trạng thái hiện tại & Định hướng thuyết trình**
- **Tiến độ:** Đã hoàn thành code mô phỏng, đã xong 19 bài Lab, dataset đã sinh xong, đang hoàn thiện Slide thuyết trình (thời lượng ~8 phút cho phần của tôi).
    
- **Luồng thuyết trình (Storytelling Flow) đã chốt:**
    
    1. **Lý do chọn đề tài:** An ninh mạng + Sự bất lực của cách cũ -> Chọn Học máy.
        
    2. **Lý do phải mô phỏng (The Why):** Học máy cần dữ liệu -> Dữ liệu thực tế thiếu -> Cần tự xây dựng công cụ mô phỏng chuẩn (Giấu được & Tách được).
        
    3. **Sản phẩm 1 (Tính đúng đắn):** Giới thiệu 19 bài Lab trên Labtainer (Minh chứng cho việc quy trình đã được chuẩn hóa và đóng gói cho giáo dục).
        
    4. **Sản phẩm 2 (Tính hiệu quả):** Tinh chỉnh tham số (ví dụ Echo Hiding) -> Đạt PSNR cao -> Đủ điều kiện sinh Dataset sạch.
        
    5. **Chuyển giao:** Từ công cụ và chỉ số PSNR này -> Chuyển sang phần Học máy của Hưởng.
---

**Cách sử dụng:** Lần sau bạn chỉ cần nhắn: _"Chào Gemini, đây là context đồ án của tôi, hãy đọc nó và chúng ta tiếp tục chỉnh sửa slide đoạn [X]..."_ và dán đoạn văn bản trên vào.