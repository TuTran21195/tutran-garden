---
{"dg-publish":true,"dg-path":"1. PROJECT/Audio Steganography/Phase-Coding/Phase coding - Cách chia đoạn âm thanh.md","dg-permalink":"2025/stego/phase-coding-sub","permalink":"/2025/stego/phase-coding-sub/","title":"Phase coding - Cách chia đoạn âm thanh","tags":["do-an","lecture_notes"],"created":"2025-09-12T15:44:18.534+07:00","updated":"2025-09-13T18:02:35.469+07:00"}
---


# Information
<div style="display: flex; justify-content: center; gap: 10px; margin-top: 10px;">
  <form action="https://github.com/TuTran21195/steg-labs">
    <button type="submit" style="padding: 10px; background: #24292e; color: white; border-radius: 5px; border: none;">Github Labs Repository</button>
  </form>
  <form action="https://tutran21195.github.io/steg-labs">
    <button type="submit" style="padding: 10px; background: #007bff; color: white; border-radius: 5px; border: none;">This Labs tutorial</button>
  </form>
</div>


### Giải Thích Chi Tiết Về Việc Chia Đoạn Và Dung Lượng Vector Pha Trong Phase Coding

Dựa trên lý thuyết phase coding trong giấu tin âm thanh (steganography), tôi sẽ giải thích rõ ràng hai điểm bạn đang thắc mắc, dựa trên cách phương pháp hoạt động tiêu chuẩn và các biến thể (từ các nguồn như bài viết trên Medium và arXiv về phase coding). Tôi sẽ giữ dễ hiểu, tránh toán phức tạp, và liên hệ trực tiếp với mô tả bạn cung cấp. Lưu ý rằng mô tả của bạn dường như dựa trên phiên bản tiêu chuẩn, nơi chỉ giấu tin trong đoạn đầu tiên, nhưng một số cải tiến có thể giấu ở nhiều đoạn (tôi sẽ phân biệt rõ).

#### 1. **Hiểu Về Việc "Chia Dữ Liệu Âm Thanh Gốc Có Chiều Dài N Thành Nhiều Đoạn Có Chiều Dài Bằng Với Thông Tin Cần Giấu"**
   - **Ý nghĩa của câu này:** Câu mô tả này có thể hơi mơ hồ (có lẽ do dịch thuật), nhưng trong phase coding tiêu chuẩn, nó không có nghĩa là chiều dài mỗi đoạn **bằng đúng** số bit cần giấu (ví dụ 8 bit = 8 mẫu). Thay vào đó:
     - "Thông tin cần giấu" thường ám chỉ **độ dài của thông điệp bí mật** (secret message), tính bằng bit (ví dụ 8 bit cho một byte đơn giản).
     - ==Âm thanh gốc (dài N mẫu) được chia thành **nhiều đoạn (segments)**, và **chiều dài của mỗi đoạn (gọi là S mẫu)** được chọn sao cho phù hợp với độ dài thông điệp bí mật==. Cụ thể:
       - S thường là một số lớn (ví dụ 512, 1024, hoặc lớn hơn), là lũy thừa của 2 để DFT tính nhanh (FFT).
       - ==S được chọn để **vector pha của đoạn đầu tiên đủ lớn để chứa toàn bộ thông điệp bí mật**== (sẽ giải thích ở phần 2).
     - **Số lượng đoạn (K):** K = N / S (hoặc N được cắt để vừa). Thường cần ít nhất 2 đoạn (đoạn đầu để giấu tin, các đoạn sau để điều chỉnh pha giữ liên tục). Nếu N nhỏ, có thể padding (thêm dữ liệu) để đủ đoạn.
   - **Đảm bảo chiều dài vector pha của mỗi đoạn:**
     - Sau khi chia, mỗi đoạn dài S mẫu → DFT của đoạn đó cho ra vector phức X[k] với **S phần tử** (k=0 đến S-1).
     - Vì tín hiệu âm thanh là thực (real-valued), vector pha chỉ có **khoảng S/2 + 1 phần tử độc lập** (do đối xứng: pha ở k và S-k là liên hợp).
     - Ví dụ: Nếu S=1024, vector pha có khoảng 513 phần tử độc lập.
     - **Đảm bảo:** Người triển khai **chọn S đủ lớn** dựa trên số bit cần giấu. Không phải tự động "đảm bảo", mà là thiết kế hệ thống: Nếu số bit lớn, tăng S (hoặc dùng nhiều bin pha hơn). Nếu S quá nhỏ, không giấu được hết bit → lỗi hoặc cắt message. Trong thực tế, S thường fixed (như 1024), và dung lượng giấu tin bị giới hạn bởi S/2.
     - Trong một số cải tiến (như ), S được tính động: S ≈ 2 * 2^{log2(2 * msg_len)}, nơi msg_len là số bit, để đảm bảo mỗi đoạn đủ chứa một phần bit (nhưng trong tiêu chuẩn, chỉ đoạn đầu).

   - **Ví dụ minh họa:** Giả sử âm thanh gốc N=10000 mẫu, thông điệp bí mật 8 bit. Chọn S=1024 (vì 1024/2=512 >8, đủ chứa). Chia thành K=9 đoạn (9*1024≈9216, cắt bớt phần dư). Mỗi đoạn có vector pha dài ~512.

#### 2. **Tại Sao Vector Pha Của Đoạn Đầu Tiên Đủ Dài Để Chứa 8 Bit (Hoặc Nhiều Hơn), Và Lý Do Chỉ Giấu Ở Đoạn Đầu**
   - **Cách giấu nhiều bit (không chỉ 1 bit):** Trong mô tả của bạn, nó nói "bit cần giấu" (singular), nhưng thực tế phase coding giấu **nhiều bit** bằng cách:
     - Chuyển thông điệp bí mật thành chuỗi bit (ví dụ 8 bit = "01001100").
     - Với đoạn đầu tiên: Sau DFT, vector pha \(\phi_1[\omega_k]\) có nhiều phần tử (k=1 đến ~S/2, bỏ k=0 vì DC thường không dùng).
     - **Mỗi bit giấu vào một phần tử pha:** Ví dụ, cho bit 0: đặt \(\phi_{new}[\omega_k] = \pi/2\); bit 1: \(-\pi/2\) (như mô tả của bạn). Hoặc biến thể: bit 0 = 0, bit 1 = \pi.
     - Vậy, để giấu 8 bit, cần ít nhất 8 phần tử pha độc lập → S/2 >=8 (S>=16, nhưng thường lớn hơn để tránh méo và dùng bin thấp tần để giấu).
     - **Đảm bảo đủ dài:** Bằng cách chọn S lớn hơn số bit (thường S >> số bit). Nếu số bit > dung lượng pha, không giấu được → cần tăng S hoặc cắt message. Dung lượng điển hình: Với S=1024, giấu hàng trăm bit, nhưng thực tế giới hạn ở 20-50 bit/đoạn để âm thanh không thay đổi nhiều (tai người nhạy với pha ở tần số thấp).
     - Trong cải tiến (), giấu ở nhiều đoạn (chia bit đều cho n đoạn), nhưng trong tiêu chuẩn (, ), chỉ giấu ở đoạn đầu để giảm distortion (thay đổi pha nhiều đoạn dễ gây nhiễu nghe được).

   - **Lý do chỉ giấu ở đoạn đầu tiên (như mô tả của bạn):**
     - Để **tối thiểu hóa thay đổi âm thanh:** Chỉ thay pha tuyệt đối ở đoạn đầu, rồi điều chỉnh pha các đoạn sau để giữ độ lệch pha (\(\Delta\phi\)) → tín hiệu mượt mà, ít méo.
     - **Dễ trích xuất:** Khi giải mã, chỉ cần DFT đoạn đầu, đọc pha ở các bin đã giấu để lấy bit (so sánh pha với \(\pi/2\) hay \(-\pi/2\)).
     - **Tránh nhiễu lan rộng:** Nếu giấu ở nhiều đoạn, thay đổi pha độc lập có thể phá hủy liên tục giữa đoạn, gây artifact (nhiễu nghe được). Giới hạn ở đoạn đầu giúp kiểm soát tốt hơn ( nhấn mạnh minimize audible distortions).
     - Nếu cần giấu nhiều bit hơn, tăng S (làm vector pha dài hơn) thay vì giấu ở nhiều đoạn.

#### 3. **Tóm Tắt Và Lưu Ý Thực Tế**
   - Để giấu 8 bit: Chọn S >=16 (nhưng thường 512+ để chất lượng tốt), vector pha đủ chứa (8 phần tử pha cho 8 bit).
   - Việc chia đoạn không "tự động đảm bảo", mà do thiết kế: Bạn (người code) chọn S dựa trên số bit. Nếu S nhỏ, dung lượng giấu tin thấp → cần âm thanh dài hơn hoặc message ngắn hơn.
   - Ưu điểm: Ít ảnh hưởng âm thanh vì pha ít nhạy cảm.
   - Nhược điểm: Dung lượng giấu thấp (so với LSB), dễ bị phát hiện nếu tấn công phân tích pha.
   - Nếu triển khai code (ví dụ Python với numpy/scipy), có thể dùng FFT để DFT/IDFT, và chọn S = 2**ceil(log2(2*num_bits)) như trong cải tiến.

Nếu bạn cần ví dụ code minh họa hoặc làm rõ thêm (như cách trích xuất tin), cứ hỏi nhé!