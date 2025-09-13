---
{"dg-publish":true,"dg-path":"1. PROJECT/Audio Steganography/Phase-Coding/Phase Coding.md","dg-permalink":"2025/stego/phase-coding","permalink":"/2025/stego/phase-coding/","title":"Phase Coding","tags":["do-an","lecture_notes"],"created":"2025-09-12T14:00:14.784+07:00","updated":"2025-09-13T18:02:16.143+07:00"}
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

# Abstract
### Giấu tin
> [!cornell]
> > 
> >  - Có những bước chính nào
> >  - Input output của DFT
> >  - chỉ giấu vào đoạn đầu tiên, các đoạn sau đó thì chỉnh theo $\Delta$ giữa các pha để tránh bị lộ. 
> 
> > 
> > **Main concept:** QUY TRÌNH GIẤU TIN
> > 
> > **Key points:**
> > 1. Chia đoạn âm thanh thành các đoạn bằng nhau có chiều dài đủ để giấu message.
> > 	- Chia thành các đoạn sao cho Mỗi đoạn âm thanh có S mẫu, $S > {len_{mes}}$ [^1] 
> > 1. Biến đổi DFT cho từng đoạn [^3]. Mỗi đoạn thì phân tích ra được: ma trận biên độ (A) và ma trận pha.
> > 	- DFT thì phân tích đoạn âm thanh (A.Cos...) thành *các tần số cấu thành* nó, mỗi tần số thì nó cũng có một công thức same same sóng. Nên là nó có được biên độ và pha của tần số đó.
> > 	- Mỗi đoạn âm thanh có S mẫu -> DFT cho S mẫu đó thì ra được vector (vector X có $S$ hoặc $S/2$ phần tử [^2])
> > 1. Thay đổi giá trị pha để giấu tin (chỉ giấu ở đoạn đầu tiên):
> > 	    - Nếu bit cần giấu là 0, $Phase_{new} = \frac{\pi}{2}$.
> > 	    - Nếu bit cần giấu là 1, $Phase_{new} = -\frac{\pi}{2}$.
> > 1. Tạo ma trận pha mới: Điều chỉnh các đoạn sau đó sao cho độ lệch pha ko bị thay đổi → tránh bị phát hiện
> > 2. Kết hợp cường độ pha: Ghép pha vừa đổi với ma trận cường độ ban đầu
> > 3. Ghép các đoạn vào với nhau sau khi IDFT để đưa tín hiệu âm thanh về miền thời như ban đầu.
> > 	- Mỗi đoạn âm thanh (dài S mẫu) được xử lý IDFT riêng, rồi ghép lại thành tín hiệu dài N.
> > 
> > **Links:** [[1. PROJECT/01_Đồ Án/Phase coding - Cách chia đoạn âm thanh\|Phase coding - Cách chia đoạn âm thanh]] ● [[1. PROJECT/01_Đồ Án/Cơ bản về âm thanh, Fourier\|Cơ bản về âm thanh, Fourier]]
> 
> > 
> > 

### Tách tin
> [!cornell]
> > 
> > - Câu hỏi review chính?
> > - Keywords để nhớ?
> > - Điểm cần kiểm tra lại?
> 
> > 
> > **Main concept:** QUY TRÌNH TÁCH TIN
> > 
> > **Key points:**
> > - Lấy đoạn đầu tiên của âm thanh.
> > - Thực hiện DFT để lấy pha $\phi[k]$.
> > - So sánh pha ở đoạn đầu tiên của âm thanh với quy ước ($\frac{\pi}{2}$ $-\frac{\pi}{2}$) để lấy bit.
> > - Tái tạo thông điệp (ví dụ, chuỗi bit "01001100" thành ký tự ASCII).
> > 
> > **Links:** 
> 
> > 
> > 


# Nội dung
Phương pháp mã hóa pha là một kỹ thuật giấu tin trong âm thanh dựa trên đặc điểm tai người không thể phân biệt được sự khác nhau về pha của hai tín hiệu âm thanh. Việc giấu tin được thực hiện bằng cách thay thế một đoạn âm thanh ban đầu bằng một pha tham chiếu biểu thị dữ liệu, đồng thời điều chỉnh pha của các đoạn tiếp theo để đảm bảo độ chênh lệch pha giữa các đoạn không đổi.

### Các thuật ngữ cơ bản
#### Công thức sóng & pha
Để hiểu về công thức âm thanh $x(t) = A\cos(2\pi ft + \phi)$ và tác động của pha, cũng như sự chênh lệch pha giữa hai bản âm thanh, chúng ta cần xem xét các yếu tố cấu thành và cách chúng tương tác trong phương pháp mã hóa pha.

**1. Giải thích công thức âm thanh $x(t) = A\cos(2\pi ft + \phi)$** Trong công thức biểu diễn tín hiệu sóng hình sin cơ bản này:

- **A** là **biên độ** (amplitude) của tín hiệu. Biên độ thể hiện độ lớn của sóng.
- **f** là **tần số** (frequency) của tín hiệu. Tần số xác định số chu kỳ sóng hoàn thành trong một đơn vị thời gian (ví dụ: Hertz - Hz).
- **t** là **thời gian**. Đây là biến số độc lập của tín hiệu.
- **$\phi$** (phi) là **pha** (phase) của tín hiệu. ==Pha biểu thị vị trí ban đầu của sóng trong một chu kỳ, hoặc sự dịch chuyển của sóng so với một điểm tham chiếu.==

**2. Tác động của pha ($\phi$)** Thuật ngữ =="pha" được hiểu theo nghĩa tham chiếu đến một tín hiệu khác. Ví dụ, nếu lấy tín hiệu $A\cos(2\pi ft)$ làm tham chiếu, thì tín hiệu $x(t) = A\cos(2\pi ft + \phi)$ có pha là $\phi$. Tương tự, tín hiệu $y(t) = A\sin(2\pi ft + \phi)$ có thể được viết lại thành $A\cos(2\pi ft + \phi - \pi/2)$, cho thấy pha của nó là $\phi - \pi/2$ so với cùng một tham chiếu.==

Trong phương pháp mã hóa pha để giấu tin, mỗi dữ liệu được coi là một **dịch pha** (phase shift) trong phổ pha của tín hiệu sóng mang. Cụ thể, việc điều chỉnh pha được thực hiện để giấu thông tin:

- Nếu bit cần giấu là 0, giá trị pha mới được đặt là $\frac{\pi}{2}$.
- Nếu bit cần giấu là 1, giá trị pha mới được đặt là $-\frac{\pi}{2}$. ==Thông tin giấu chỉ được phép giấu trong vector pha của đoạn đầu tiên.== Điều này cho thấy pha có thể được thay đổi một cách có chủ đích để mang thông tin mật. Tai người không thể phân biệt được sự thay đổi pha nhỏ của âm thanh, khiến phương pháp này khó bị phát hiện bằng giác quan. Hình 3.12 trong tài liệu minh họa rằng cấu trúc pha của âm thanh thay đổi sau khi giấu thông tin.

**3. Sự chênh lệch pha giữa hai bản âm thanh (hoặc các đoạn âm thanh)** Trong quy trình giấu tin bằng mã hóa pha, dữ liệu âm thanh gốc được chia thành nhiều đoạn. Sau đó, phép biến đổi Fourier rời rạc (DFT) được áp dụng cho mỗi đoạn để thu được ma trận độ lớn pha $\phi_j[\omega_k]$ và ma trận độ lớn tín hiệu $A_j[\omega_k]$.

**Độ lệch pha giữa các đoạn kề nhau** là một yếu tố quan trọng và được tính bằng công thức: $\Delta\phi_j[\omega_k] = \phi_{j+1}[\omega_k] - \phi_j[\omega_k]$ Việc tính toán này nhằm đảm bảo rằng sự khác biệt giữa các pha không quá lớn sau khi các biến đổi được thực hiện. Sau khi điều chỉnh pha của đoạn đầu tiên để giấu bit thông tin, một ma trận pha mới sẽ được tạo ra, thỏa mãn điều kiện căn chỉnh lại độ chênh lệch đã tính toán: $\phi'_{j+1}[\omega_k] = \phi'[\omega_k] + \Delta\phi_{j+1}[\omega_k]$ Sự tồn tại của cặp $\phi'_{j+1}[\omega_k]$ và $\phi'[\omega_k]$ thỏa mãn công thức này là do phép biến đổi Fourier rời rạc có tính đầy đủ. Sau đó, pha mới này được kết hợp với cường độ pha của tín hiệu cũ sau khi đã giấu thông tin để tái tạo lại ma trận pha của các đoạn kề nhau.

Tóm lại, pha trong tín hiệu âm thanh là một tham số quan trọng có thể được điều chỉnh để giấu thông tin. Sự chênh lệch pha giữa các đoạn âm thanh được tính toán và duy trì để đảm bảo rằng thông tin giấu được tích hợp một cách khó phát hiện và có thể phục hồi.

#### Biến đổi DFT (Fourier)
Trong phương pháp mã hóa pha để giấu tin trong âm thanh, **biến đổi Fourier rời rạc (DFT)** đóng một vai trò trung tâm và có tác dụng vô cùng quan trọng [28, 33.3.1, 33.3.2].

**1. Tác dụng của biến đổi Fourier (cụ thể là DFT) cho mã hóa pha:**

Biến đổi Fourier nói chung và DFT nói riêng có tác dụng chuyển đổi tín hiệu âm thanh từ miền thời gian sang miền tần số [33.3.1]. ==Trong miền tần số, tín hiệu được biểu diễn bởi các thành phần tần số khác nhau, mỗi thành phần có một độ lớn (biên độ) và một pha== [33.3.1]. Điều này rất quan trọng đối với mã hóa pha vì:

- **Truy cập thông tin pha**: Phương pháp mã hóa pha khai thác đặc tính tai người không thể phân biệt được sự khác nhau nhỏ về pha của hai tín hiệu âm thanh [33.3.1, 33.3.4]. Để thay đổi pha của tín hiệu âm thanh nhằm giấu tin, trước hết cần phải truy cập được các giá trị pha này. ==DFT cung cấp khả năng tách biệt thông tin độ lớn và pha của tín hiệu, cho phép chúng ta thao tác trực tiếp với thành phần pha mà không ảnh hưởng đáng kể đến độ lớn== (là yếu tố chính ảnh hưởng đến cảm nhận âm thanh) [33.3.1].
{ #dft-why}

- **Giấu tin không gây nhiễu**: Bằng cách điều chỉnh pha trong miền tần số, phương pháp này có thể giấu tin mà không gây nhiễu tín hiệu như các phương pháp khác (ví dụ như LSB) [33.3.4]. Sự thay đổi pha nhỏ do giấu tin gây ra sẽ rất khó bị phát hiện bởi hệ thống thính giác của con người [33.3.1, 33.3.4].
- **Tái tạo tín hiệu**: ==Sau khi thao tác pha, biến đổi Fourier ngược (IDFT) được sử dụng để chuyển đổi tín hiệu đã sửa đổi trở lại miền thời gian,== tạo ra file âm thanh chứa tin đã giấu [33.3.2].

**2. Biến đổi Fourier rời rạc (DFT) được thực hiện như thế nào và tác dụng trong mã hóa pha:**

**Cách DFT hoạt động (ví dụ cụ thể biến đổi):**

Trong quy trình giấu tin bằng mã hóa pha, DFT được thực hiện như sau:

1. **Chia dữ liệu âm thanh**: Dữ liệu âm thanh gốc có chiều dài N được chia thành nhiều đoạn nhỏ có chiều dài bằng với thông tin cần giấu [28, 33.3.2].
2. **Áp dụng DFT**: Mỗi đoạn âm thanh sau khi chia sẽ được biến đổi bằng phép biến đổi Fourier rời rạc (DFT) [28, 33.3.2].
    - Kết quả của bước này là **ma trận độ lớn tín hiệu** $A_j[\omega_k]$ và **ma trận độ lớn pha** $\phi_j[\omega_k]$ (Hình 3.8) [28, 33.3.2].
    - Độ lớn tín hiệu được tính bằng công thức: $A_i(k) = \sqrt{Re[F{c_i}(k)]^2 + Im[F{c_i}(k)]^2}$ [33.3.1].
    - Ma trận độ lớn pha được tính bằng công thức: $\phi_i(k) = \arctan \frac{Im[F{c_i}(k)]}{Re[F{c_i}(k)]}$ [33.3.1].
    - _Lưu ý_: Nguồn tài liệu mô tả kết quả của việc áp dụng DFT lên từng đoạn âm thanh dưới dạng các ma trận độ lớn và pha, nhưng không cung cấp một ví dụ số học cụ thể cho quá trình biến đổi DFT từng bước [28, 33.3.1, 33.3.2].

**Tác dụng cụ thể của DFT trong mã hóa pha:**

- **Trích xuất pha để giấu tin**: DFT cho phép trích xuất ma trận độ lớn pha $\phi_j[\omega_k]$ từ mỗi đoạn âm thanh [28, 33.3.2]. Thông tin cần giấu (bit 0 hoặc 1) sau đó sẽ được sử dụng để điều chỉnh giá trị pha của đoạn đầu tiên. Cụ thể, nếu bit cần giấu là 0, pha mới sẽ là $\frac{\pi}{2}$; nếu là 1, pha mới là $-\frac{\pi}{2}$ [33.3.2]. Thông tin giấu chỉ được phép giấu trong vector pha của đoạn đầu tiên [33.3.2].
- **Duy trì mối quan hệ pha**: Sau khi điều chỉnh pha của đoạn đầu tiên, DFT giúp tính toán độ lệch pha giữa các đoạn kề nhau ($\Delta\phi_j[\omega_k] = \phi_{j+1}[\omega_k] - \phi_j[\omega_k]$) [33.3.2]. Điều này đảm bảo rằng mối liên hệ về sự khác biệt giữa các pha của các đoạn liên tiếp được duy trì, tránh gây ra sự thay đổi lớn và dễ nhận biết về mặt âm thanh [33.3.2].
- **Tạo ma trận pha mới**: DFT (với tính đầy đủ của nó) đảm bảo rằng luôn có thể tạo ra ma trận pha mới ($\phi'_{j+1}[\omega_k] = \phi'[\omega_k] + \Delta\phi_{j+1}[\omega_k]$) thỏa mãn các độ chênh lệch pha đã được căn chỉnh [33.3.2].
- **Tái tạo âm thanh**: Cuối cùng, các pha mới được kết hợp với cường độ pha của tín hiệu cũ, và sau đó biến đổi Fourier ngược (IDFT) được thực hiện để tái tạo dữ liệu âm thanh đã chứa tin ở miền thời gian [33.3.2].
- **Tối ưu hóa hiệu suất**: Mặc dù DFT truyền thống có độ phức tạp là O($N^2$), các nghiên cứu gần đây đã đề xuất sử dụng thuật toán Fast Fourier Transform (FFT) thay vì DFT để tối ưu hóa thời gian, giảm độ phức tạp xuống O(N log N) với điều kiện N phải có dạng $2^x$ [33.3.4]. FFT là một phiên bản hiệu quả hơn của DFT.

### **Quy trình giấu tin trong âm thanh bằng phương pháp mã hóa pha**
diễn ra qua các bước sau:

1. **Chia dữ liệu âm thanh**: Dữ liệu âm thanh gốc có chiều dài N được chia thành nhiều đoạn có chiều dài bằng với thông tin cần giấu (Hình 3.7).
2. **Biến đổi Fourier**: Mỗi đoạn âm thanh sau khi chia sẽ được biến đổi bằng phép biến đổi Fourier rời rạc (DFT). Kết quả của bước này là ma trận độ lớn pha $A_j[\omega_k]$ và ma trận độ lớn tín hiệu $\phi_j[\omega_k]$ (Hình 3.8).
    - Độ lớn tín hiệu được tính bằng công thức: $A_i(k) = \sqrt{Re[F{c_i}(k)]^2 + Im[F{c_j}(k)]^2}$.
    - Ma trận độ lớn pha được tính bằng công thức: $\phi_i(k) = \arctan \frac{Im[F{c_i}(k)]}{Re[F{c_i}(k)]}$.
3. **Tính độ lệch pha**: Tính độ lệch pha giữa các đoạn kề nhau để đảm bảo sự khác biệt giữa các pha không quá lớn sau khi biến đổi. Độ lệch pha được tính bằng công thức: $\Delta\phi_j[\omega_k] = \phi_{j+1}[\omega_k] - \phi_j[\omega_k]$.
4. **Điều chỉnh pha**: Giá trị pha của đoạn đầu tiên sẽ được điều chỉnh dựa trên bit cần giấu. Thông tin giấu chỉ được phép giấu trong vector pha của đoạn đầu tiên (Hình 3.9).
    - Nếu bit cần giấu là 0, $Phase_{new} = \frac{\pi}{2}$.
    - Nếu bit cần giấu là 1, $Phase_{new} = -\frac{\pi}{2}$.
5. **Tạo ma trận pha mới**: Tiến hành tạo ma trận pha mới thỏa mãn để căn chỉnh lại độ chênh lệch đã tính ở bước 3. Ma trận pha mới thỏa mãn điều kiện: $\phi'_{j+1}[\omega_k] = \phi'[\omega_k] + \Delta\phi_{j+1}[\omega_k]$ (Hình 3.10).
6. **Kết hợp cường độ pha**: Kết hợp pha mới với cường độ pha của tín hiệu cũ sau khi giấu thông tin để tái tạo lại ma trận pha của các đoạn kề nhau (Hình 3.11).
7. **Ghép các đoạn và DFT ngược**: Thực hiện ghép các đoạn lại và biến đổi Fourier rời rạc ngược (IDFT) để tạo lại dữ liệu âm thanh chứa tin đã giấu.
	- Mỗi đoạn âm thanh (dài S mẫu) được xử lý IDFT riêng, rồi ghép lại thành tín hiệu dài N.
	- Vì chỉ pha thay đổi (biên độ giữ nguyên), x[n]x[n]x[n] nghe gần giống tín hiệu gốc, nhưng có thông điệp ẩn trong pha.

**Ưu và nhược điểm của phương pháp mã hóa pha**:

- **Ưu điểm**:
    - **Khó phát hiện**: Phương pháp này khó bị phát hiện bởi giác quan của con người vì hệ thính giác không nhạy cảm với sự thay đổi pha nhỏ của âm thanh.
    - **Không gây nhiễu**: Không gây nhiễu tín hiệu như các phương pháp khác (ví dụ: LSB).
- **Nhược điểm**:
    - **Dung lượng giấu tin nhỏ**: Lượng thông tin có thể giấu được khá nhỏ, vì thông tin chỉ được giấu trên một đoạn nhỏ của âm thanh.
    - **Khả năng ứng dụng hạn chế**: Nếu muốn tăng lượng thông tin giấu, có thể kéo dài đoạn âm thanh gốc, nhưng điều này sẽ tăng khả năng bị phát hiện.
    - **Quá trình phức tạp**: Quy trình giấu và tách tin tương đối phức tạp và tốn thời gian.

Để khắc phục một số nhược điểm, các nghiên cứu gần đây đã đề xuất sử dụng thuật toán Fast Fourier Transform (FFT) thay vì DFT truyền thống để tối ưu hóa thời gian, giảm độ phức tạp từ O($N^2$) xuống O(N log N) với điều kiện N phải có dạng $2^x$.

# Ref
- [An Improved Phase Coding Audio Steganography Algorithm.pdf](https://arxiv.org/pdf/2408.13277)
- [Audio Steganograpgy by Phase Modification.pdf](https://personales.upv.es/thinkmind/dl/conferences/securware/securware_2014/securware_2014_2_20_30036.pdf)
- [Discrete Fourier Transform Explained Easily - Youtube](https://www.youtube.com/watch?v=ZUi_jdOyxIQ&t=131s)
- [Can you guess the song? Fourier Music Decomposition - YouTube](https://www.youtube.com/watch?v=G7XL-7rj45M&t=93s)

[^1]: Xem cách chia đoạn âm thanh tại [[1. PROJECT/01_Đồ Án/Phase coding - Cách chia đoạn âm thanh\|Phase coding - Cách chia đoạn âm thanh]]

[^2]: Xem ví dụ về input, output của DFT trên đoạn âm thanh [[1. PROJECT/01_Đồ Án/Cơ bản về âm thanh, Fourier#Ví dụ đơn giản về đoạn âm thanh và DFT\|Cơ bản về âm thanh, Fourier#Ví dụ đơn giản về đoạn âm thanh và DFT]]

[^3]: Tại sao lại có bước này: [[1. PROJECT/01_Đồ Án/Phase Coding#^dft-why\|Phase Coding#^dft-why]]
