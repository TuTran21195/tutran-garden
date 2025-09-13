---
{"dg-publish":true,"dg-path":"1. PROJECT/Audio Steganography/STSM.md","dg-permalink":"2025/stego/stsm-lecture","permalink":"/2025/stego/stsm-lecture/","title":"STSM","tags":["do-an","lecture_notes"],"created":"2025-09-13T15:15:45.845+07:00","updated":"2025-09-13T18:02:47.198+07:00"}
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

> [!cornell]
> > 
> > - Hamming 7,4
> > - Lấy 2 sample đầu tiên làm header.
> > - chỉnh tổng của (bộ 3 sample)
> 
> > 
> > **Main concept:** GIẤU VÀ TÁCH TIN DÙNG STSM
> > 
> > **Key points:**
> > - Bản tin cần giấu thì trích thành bit rồi dùng thêm mã sửa sai Hamming (7,4).
> > - tách âm thanh ra thành phần header và phần nội dung
> > 	- Header: lấy 2 mẫu (samples[0] và samples[1]) và chuyển chúng thành số nguyên 16-bit để lưu số lượng bit đã giấu.
> > - lấy lần lượt combo 3 mẫu, tính tổng 3 mẫu đó. 
> > 	- Giấu bit 1 → chỉnh sao cho tổng 3 mẫu đó là lẻ.
> > 	- Giấu bit 0 → Chỉnh sao cho tổng 3 mẫu đó là chẵn.
> > 	- VD: Giấu 2 bit là `10` vào tín hiệu [100, 200, 300, 401, 500, 600]
> > 		- Tổng 3 bit đầu = 600, muốn giấu `1` →  điều chỉnh mẫu ở giữa +1 → signal [100, **201**, 300, 401, 500, 600]
> > 		- Tổng 3 bit sau = lẻ, muốn giấu `0` → điều chỉnh bit ở giữa -1 để tổng thành chẵn → signal [100, **201**, 300, 401, **499**, 600]
> > - Ghép signal mới này với header cũ → file âm thanh mới chứa thông điệp được giấu
> > 
> > Tách tin thì trích 2 sample đầu để xem là đã giấu bao nhiêu bit, rồi lần lượt tính tổng của 3 bit một là oke.
> > 
> > 
> > **Links:** [] • 
> 
> > 
> > - Thêm mã sửa sai vào chuỗi bit thông điệp cần giấu
> > - lấy 2 sample đầu tiên của tệp âm thanh để làm header, lưu lại số lượng bit cần giấu
> > - Chỉnh tuần tự sum(bộ 3 sample) lần lượt sao cho sum chẵn để giấu bit 0, lẻ để giấu bit 1.

# Nội dung
Phương pháp tự đánh dấu sử dụng kỹ thuật điều chỉnh tỉ lệ thời gian (Steganography using Time-Scale Modification - **STSM**) là một trong những cách tiếp cận để giấu tin trong âm thanh.

**Triết lý chính của phương pháp tự đánh dấu dùng STSM:**

Triết lý cốt lõi của STSM là **giấu thông tin bằng cách thay đổi khoảng thời gian giữa các mẫu âm thanh**, thay vì thay đổi trực tiếp nội dung tín hiệu âm thanh. Mục tiêu là làm cho thông tin giấu trở nên khó phát hiện bằng tai người vì nó không làm thay đổi nội dung mà chỉ điều chỉnh các khoảng thời gian.

Cụ thể, ý tưởng thực hiện là ==**thay đổi tỉ lệ thời gian giữa hai cực là cực đại và cực tiểu của tín hiệu âm thanh**==. Khoảng cách giữa hai cực này được chia thành N phân đoạn có biên độ bằng nhau. Việc thay đổi độ dốc của tín hiệu sẽ phụ thuộc vào bit muốn nhúng. Tín hiệu âm thanh khi chứa tin giấu sẽ có dạng sóng với những biên độ khác nhau do các giá trị cực đại, cực tiểu khác nhau, nhưng biên độ giữa các phân đoạn N là như nhau và chỉ khác ở giá trị cực đại và cực tiểu. Điều này dẫn đến đường tín hiệu đi từ giá trị cực đại đến cực tiểu sẽ bị thay đổi độ dốc.

**Quy trình giấu tin bằng phương pháp tự đánh dấu dùng STSM:**

Quy trình giấu thông tin trong tín hiệu âm thanh bằng STSM được tiến hành qua 2 bước chính:

1. **Mã hóa:**
    
    - **Đầu vào**: Chuỗi bit thông điệp bí mật **M** cần giấu, có độ dài **L** (L là bội số của 8).
    - **Chia và Mã hóa Hamming**: Chuỗi bit **M** được chia thành các đoạn **Mi** có độ dài 4 bit. Mỗi đoạn bit thông tin này sẽ được mã hóa bằng phương pháp **mã Hamming** để biến đổi từ 4 bit thành từ mã có độ dài 7 bit.
    - **Ghép chuỗi**: Ghép các chuỗi bit kết quả lại để được chuỗi bit **M'**. Độ dài chuỗi **M'** sẽ bằng (L/4) x 7.
2. **Giấu tin:**
    
    - **Đầu vào**: Tệp âm thanh gốc **C** và chuỗi bit **M'** đã mã hóa.
    - **Tiền xử lý vật chứa**: Vật chứa **C** sẽ được xử lý để trích phần header và phần dữ liệu.
    - **Kiểm tra dung lượng**: Người giấu tin sẽ kiểm tra xem vật chứa **C** có đủ để giấu chuỗi bit **M'** không. Nếu không đủ, quá trình dừng lại và thông báo không thể giấu được.
    - **Ghi header**: Nếu đủ, header của **C** được ghi vào một tệp mới **C'**.
    - **Giấu từng bit**:
        - Tiến hành ==trích tuần tự **3 mẫu dữ liệu*==* của **C** và ==tính tổng của chúng.==
        - **Điều chỉnh dựa trên bit M'**:
            - Nếu bit đang xét của **M'** là **1** mà tổng các mẫu là **lẻ**, thì thỏa mãn điều kiện giấu và không cần điều chỉnh.
            - Nếu bit đang xét của **M'** là **1** mà tổng các mẫu là **chẵn**, thì điều chỉnh **mẫu số 2** trong 3 mẫu đang xét để tổng trở thành số lẻ.
            - Nếu bit đang xét của **M'** là **0** mà tổng các mẫu là **chẵn**, thì thỏa mãn điều kiện giấu và không cần điều chỉnh.
            - Nếu bit đang xét của **M'** là **0** mà tổng các mẫu là **lẻ**, thì điều chỉnh **mẫu số 1 hoặc mẫu số 3** trong 3 mẫu đang xét để tổng trở thành số chẵn.
        - **Ghi mẫu**: Ghi 3 mẫu (đã điều chỉnh hoặc giữ nguyên) vào tệp **C'**.
        - **Lặp lại**: Lặp lại quá trình trên cho đến khi toàn bộ các bit của chuỗi **M'** đã được giấu.
    - **Hoàn tất**: Cuối cùng, ghi các mẫu còn lại từ **C** vào **C'** và kết thúc quá trình.

**Ưu điểm của phương pháp STSM:**

- **Tính vô hình cao**: STSM là một phương pháp giấu tin hiệu quả và khó phát hiện bằng tai người, vì nó không làm thay đổi nội dung của tín hiệu âm thanh, mà chỉ thay đổi khoảng thời gian giữa các mẫu.
- **Tính ứng dụng rộng rãi**: Phương pháp này có thể được áp dụng cho nhiều loại tín hiệu âm thanh khác nhau như WAV, MP3, v.v..

