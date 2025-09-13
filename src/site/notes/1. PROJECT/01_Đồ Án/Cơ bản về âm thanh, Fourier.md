---
{"dg-publish":true,"dg-path":"1. PROJECT/Audio Steganography/Phase-Coding/Cơ bản về âm thanh, Fourier.md","dg-permalink":"2025/stego/audio-fourier-dft","permalink":"/2025/stego/audio-fourier-dft/","title":"Cơ bản về âm thanh, Fourier","tags":["do-an","lecture_notes"],"created":"2025-09-12T15:10:24.783+07:00","updated":"2025-09-13T16:10:45.997+07:00"}
---



### Ví dụ đơn giản về đoạn âm thanh và DFT

Giả sử một đoạn âm thanh ngắn (rất ngắn để minh họa, chỉ 8 mẫu) là sóng sin thuần ở tần số **440 Hz** (nốt A tiêu chuẩn), lấy mẫu ở tần số **8000 Hz** (fs, phổ biến cho âm thanh thoại).

#### Tín hiệu âm thanh (miền thời gian)
- **Công thức**: $( x[n] = \sin(2\pi f n / fs))$, với \( $n = 0$ \) đến \( $N-1$ \) $(N=8), f=440 Hz, fs=8000 Hz$.
- ==**Đầu vào (giá trị biên độ theo mẫu thời gian)**:==  
  ==[0.00, 0.34, 0.64, 0.86, 0.98, 0.99, 0.88, 0.66]==  
  (Đây là biên độ dao động từ 0 đến gần 1, giống như sóng âm tăng dần rồi giảm, đại diện cho một phần chu kỳ âm thanh.)

#### Biến đổi DFT
- **Công thức**: $\( X[k] = \sum_{n=0}^{N-1} x[n] \cdot e^{-j 2\pi k n / N} \)$, cho k=0 đến N-1.  
  (Tính tổng có trọng số phức để phân tích thành các tần số $k * fs / N$: 0Hz, 1000Hz, 2000Hz, ..., 7000Hz.)
- ==**Đầu ra (miền tần số, dạng phức)**:==  
==[5.34 + 0j, -1.58 + 0.56j, -0.53 + 0.20j, -0.38 + 0.08j, -0.35 + 0j, -0.38 - 0.08j, -0.53 - 0.20j, -1.58 - 0.56j]==
- ==**Biên độ (|X[k]|, năng lượng tần số)**:== [5.34, 1.68, 0.57, 0.39, 0.35, 0.39, 0.57, 1.68]  
  (Năng lượng cao nhất ở DC (0Hz) do offset, và lan ra các bin gần 440Hz như 1000Hz vì N nhỏ, gây "leakage". Trong thực tế, dùng N lớn hơn để chính xác.)
- ==**Pha (góc pha ở độ)**:== [0°, 161°, 160°, 168°, 180°, -168°, -160°, -161°]  
  (Thể hiện độ lệch pha của từng tần số; đối xứng vì tín hiệu thực.)

Kết quả DFT cho thấy âm thanh này chủ yếu có tần số thấp (gần 440Hz), với biên độ cao ở bin gần nhất và pha cho biết "giai đoạn" sóng. Trong giấu tin, bạn có thể chỉnh pha ở các bin để nhúng thông tin mà không thay đổi âm thanh nghe được nhiều.

---
### Giải Thích Chi Tiết Về DFT (Discrete Fourier Transform)

Tôi sẽ giải thích DFT một cách tường tận, bắt đầu từ cơ bản nhất, vì bạn nói chưa có nhiều kiến thức về âm thanh. Tôi sẽ tránh dùng quá nhiều toán học phức tạp, mà tập trung vào khái niệm, ví dụ, và liên hệ với âm thanh. DFT là một công cụ toán học dùng để phân tích tín hiệu (như âm thanh) từ **miền thời gian** (theo thời gian) sang **miền tần số** (theo tần số). Trong kỹ thuật giấu tin (steganography) trong âm thanh, DFT rất quan trọng vì nó cho phép bạn chỉnh sửa pha (phase) ở miền tần số mà không làm thay đổi âm thanh nghe được nhiều.

#### 1. **Cơ Bản Về Âm Thanh Và Tín Hiệu Rời Rạc**
   - **Âm thanh là gì?** Âm thanh là sóng dao động không khí, được thu bởi micro và lưu trữ dưới dạng số (digital audio). Ví dụ, một nốt nhạc đơn giản như "La" (440 Hz) là sóng sin lặp lại 440 lần/giây.
   - **Tín hiệu rời rạc:** ==Máy tính không lưu sóng liên tục, mà "lấy mẫu" (sampling) âm thanh ở các khoảng thời gian đều đặn==. 
     - **fs (tần số lấy mẫu):** Số mẫu/giây, ví dụ 8000 Hz (cho âm thanh thoại), 44100 Hz (cho nhạc chất lượng cao). Theo định lý Nyquist, fs phải gấp đôi tần số cao nhất để tránh mất thông tin.
     - **x[n]:** Đây là đầu vào của DFT – một chuỗi số đại diện biên độ âm thanh tại các điểm thời gian rời rạc. n là chỉ số mẫu (n=0,1,2,...). Ví dụ: x[0]=0.0, x[1]=0.34,... như trong ví dụ trước.
     - **N:** Số lượng mẫu trong đoạn tín hiệu bạn phân tích (kích thước của DFT). N càng lớn, phân tích càng chính xác, nhưng tính toán càng nặng. Trong ví dụ trước, N=8 (một đoạn rất ngắn để minh họa; thực tế dùng N=1024 hoặc hơn).

#### 2. **DFT Là Gì Và Tại Sao Dùng Nó?**
   - DFT biến đổi chuỗi x[n] (miền thời gian) thành X[k] (miền tần số). Nó phân tích tín hiệu thành các "thành phần tần số" – giống như phân tích một bản nhạc thành các nốt riêng lẻ.
   - **Lý do dùng trong âm thanh:** Âm thanh phức tạp là tổng của nhiều sóng sin/cos ở các tần số khác nhau. DFT giúp "tách" ra để xem tần số nào mạnh (biên độ cao), và "giai đoạn" của chúng (pha). Trong giấu tin, bạn có thể chỉnh pha để nhúng dữ liệu bí mật mà không thay đổi biên độ (âm lượng).

#### 3. **Công Thức Và Cách Tính DFT (Giải Thích Đơn Giản)**
   - **Công thức cơ bản:**  
     \( $X[k] = \sum_{n=0}^{N-1} x[n] \cdot e^{-j 2\pi k n / N}$ \)  
     - **Hiểu đơn giản:** Đây là tổng của x[n] nhân với một "hàm sóng phức" ($e^{-j...} = cos(θ) - j sin(θ)$, với $θ = 2π k n / N$). Mỗi k đại diện một tần số cụ thể.
     - **Quá trình tính:** Máy tính lặp qua từng k (từ 0 đến N-1), nhân mỗi x[n] với giá trị phức tương ứng, rồi cộng lại. Kết quả X[k] là số phức: phần thực (real) và ảo (imaginary).
     - **Không cần tính tay:** Trong thực tế, dùng thư viện như FFT (Fast Fourier Transform, phiên bản nhanh của DFT) trong Python/MATLAB.

   - **Ví dụ minh họa với N=4 (từ ví dụ đầu tiên của chúng ta):**  
     Đầu vào: x = [0, 1, 0, -1] (một sóng đơn giản).  
     Đối với k=1: Tính tổng x[n] * (cos - j sin ở góc tương ứng). Kết quả: 0 - 2j.  
     Lặp cho các k khác → Đầu ra X = [0, -2j, 0, 2j].

#### 4. **Đầu Ra Của DFT Và Các Khái Niệm Quan Trọng** (DC, Biên độ, Pha)
   - **X[k]:** Đầu ra là mảng N phần tử phức, mỗi X[k] đại diện một "bin tần số" (hộp tần số).  
     - **Tần số thực tế của bin k:** f_k = k * fs / N (Hz). Ví dụ: fs=8000, N=8 → bin k=1 là 1000 Hz, k=2 là 2000 Hz,...
     - **DC (Direct Current):** Là X[0] (k=0), đại diện tần số 0 Hz – thành phần "trung bình" hoặc "offset" của tín hiệu. Trong âm thanh, nếu tín hiệu dao động quanh 0, DC=0 (không có offset). Nếu có offset (ví dụ âm thanh lệch lên), DC cao. Trong ví dụ âm thanh trước, DC=5.34 vì sóng sin bắt đầu từ 0 và tăng dần (có trung bình dương).
     - **Biên độ (|X[k]|):** Độ lớn của X[k], cho biết "sức mạnh" của tần số đó. Cao nghĩa là tần số đó đóng góp nhiều vào âm thanh (ví dụ: nốt chính).
     - **Pha (arg(X[k])):** Góc của X[k], cho biết "độ lệch thời gian" của sóng tần số đó (ví dụ: bắt đầu từ đỉnh hay đáy). Đo bằng radian hoặc độ. Trong giấu tin phase modifier, bạn chỉnh pha này để giấu bit dữ liệu.
     - **Đối xứng:** Với tín hiệu thực (như âm thanh), X[k] và X[N-k] là phức liên hợp → biên độ và pha đối xứng.

   - **Ví dụ trong âm thanh (từ ví dụ trước):**  
     Đầu vào: Đoạn sóng sin 440 Hz, N=8, fs=8000.  
     Đầu ra: Biên độ cao ở bin gần 440 Hz (nhưng vì N nhỏ, lan ra bin 1=1000 Hz do "leakage" – rò rỉ tần số, khi tần số không khớp chính xác bin). Pha cho biết sóng bắt đầu thế nào.

#### 5. **Một Số Vấn Đề Thực Tế Và Mẹo**
   - **Leakage:** Nếu tần số âm thanh không khớp chính xác bin (ví dụ 440 Hz không chia hết cho fs/N), năng lượng "rò" sang bin lân cận. Giải quyết: Dùng N lớn hơn hoặc windowing (hàm cửa sổ như Hanning).
   - **IDFT (Inverse DFT):** Biến đổi ngược để quay về miền thời gian. Quan trọng để tái tạo âm thanh sau khi chỉnh sửa (như giấu tin).
   - **Ứng dụng trong âm thanh:** Phân tích phổ (spectrum analyzer), lọc nhiễu, nén MP3, hoặc giấu tin bằng cách chỉnh pha ở tần số cao (con người ít nhạy cảm).

Nếu bạn có ví dụ cụ thể hoặc phần nào chưa rõ (như pha trong giấu tin), hãy hỏi thêm nhé!
