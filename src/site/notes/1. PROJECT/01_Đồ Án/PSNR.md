---
{"dg-publish":true,"permalink":"/1-project/01-do-an/psnr/","title":"PSNR","created":"2025-12-21T20:32:37.006+07:00","updated":"2025-12-21T20:33:00.279+07:00"}
---




### 1. PSNR là gì? (Định nghĩa đơn giản để thuyết trình)

- **Tên đầy đủ:** **Peak Signal-to-Noise Ratio** (Tỷ số tín hiệu trên nhiễu cực đại).
    
- **Ý nghĩa:** Nó là thước đo sự **giống nhau** giữa file âm thanh gốc (Cover Audio) và file âm thanh đã giấu tin (Stego Audio).
    
    - **PSNR càng CAO** $\rightarrow$ Nhiễu càng ít $\rightarrow$ File giấu tin nghe càng giống file gốc (Chất lượng tốt).
        
    - **PSNR càng THẤP** $\rightarrow$ Nhiễu càng nhiều $\rightarrow$ Âm thanh bị rè, méo tiếng (Chất lượng kém, dễ bị phát hiện).
        

Công thức (để hiểu bản chất):

$$PSNR = 10 \cdot \log_{10}\left(\frac{MAX^2}{MSE}\right)$$

(Trong đó MSE là sai số trung bình bình phương - tức là sự khác biệt giữa các mẫu âm thanh).

---

### 2. Con số PSNR bao nhiêu là hợp lý?

Trong giấu tin âm thanh (Audio Steganography), đây là các mốc tham chiếu chuẩn:

- **Dưới 20 dB:** **Tệ.** Âm thanh bị méo rõ rệt, nghe thấy tiếng "xè xè" hoặc nhiễu lạ. (Không đạt yêu cầu).
    
- **20 dB - 30 dB:** **Trung bình/Khá.** Có thể nghe thấy nhiễu nền nhỏ nếu đeo tai nghe xịn hoặc nghe trong phòng yên tĩnh.
    
- **30 dB - 40 dB:** **Tốt.** Tai người bình thường gần như không thể phân biệt được sự khác nhau.
    
- **Trên 40 dB:** **Xuất sắc (Tuyệt đối).** Hoàn toàn không thể phân biệt bằng thính giác.
    

> **Áp dụng vào đồ án của bạn:**
> 
> - **LSB:** Thường cho PSNR rất cao (**50 dB - 70 dB**) vì nó chỉ thay đổi bit cuối cùng, sự thay đổi biên độ cực nhỏ.
>     
> - **Echo Hiding:** Thường thấp hơn LSB một chút (**35 dB - 45 dB**) vì nó tạo ra tiếng vọng thật sự. Tuy nhiên, mức này vẫn được coi là đạt chuẩn vì não người có xu hướng bỏ qua tiếng vọng nhỏ (hiệu ứng tiền định).
>     
> - **Kết luận cho slide:** Bạn nên tự tin nói: _"Các thuật toán mô phỏng đều đạt PSNR > 35 dB (hoặc con số cụ thể bạn đo được), đảm bảo tính ẩn mật (Imperceptibility) cao."_
>     

---

### 3. Sự đánh đổi (Trade-off) - "Tam giác bất khả thi"

Đây là kiến thức **"ăn tiền"** khi trả lời vấn đáp. Trong Steganography, có 3 yếu tố luôn mâu thuẫn với nhau, bạn không thể có cả 3 cái cùng lúc tốt nhất:

1. **Dung lượng giấu (Capacity):** Giấu được bao nhiêu tin? (Payload).
    
2. **Tính ẩn mật (Imperceptibility/PSNR):** Nghe có hay không? (Chính là PSNR).
    
3. **Độ bền vững (Robustness):** Có chống lại được nén MP3, lọc nhiễu không?
    

**Quy luật đánh đổi (Trade-off) hoạt động như sau:**

- **Muốn PSNR cao (Nghe hay) $\rightarrow$ Phải giảm Dung lượng hoặc giảm Độ bền.**
    
    - _Ví dụ:_ LSB có PSNR rất cao, dung lượng lớn, nhưng Độ bền cực kém (nén file cái là mất tin luôn).
        
- **Muốn Độ bền cao (Chống tấn công tốt) $\rightarrow$ Phải giảm PSNR.**
    
    - _Ví dụ:_ Muốn tin giấu tồn tại được khi nén MP3 (như Echo Hiding hoặc Spread Spectrum), bạn phải thay đổi tín hiệu mạnh hơn $\rightarrow$ Làm cho âm thanh gốc bị biến đổi nhiều hơn $\rightarrow$ PSNR thấp đi.
        
- **Muốn Dung lượng lớn (Giấu nhiều tin) $\rightarrow$ PSNR sẽ giảm.**
    
    - _Ví dụ:_ Thay vì dùng 1 bit LSB, bạn dùng 3 bit LSB để giấu nhiều hơn $\rightarrow$ Nhiễu nhiều hơn $\rightarrow$ PSNR tụt dốc.