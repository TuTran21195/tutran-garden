---
{"dg-publish":true,"dg-path":"1. PROJECT/Audio Steganography/LSB/LSB audio thuần.md","dg-permalink":"2025/stego/basic-lsb","permalink":"/2025/stego/basic-lsb/","title":"LSB thuần","tags":["do-an"],"created":"2025-09-06T09:57:45.389+07:00","updated":"2025-09-13T17:58:56.402+07:00"}
---

# Information
<div style="display: flex; justify-content: center; gap: 10px;">
  <form action="https://github.com/TuTran21195/steg-labs">
    <button type="submit" style="padding: 10px; background: #24292e; color: white; border-radius: 5px; border: none;">Github Labs Repository</button>
  </form>
  <form action="https://tutran21195.github.io/steg-labs/docs/lsb-labs.html">
    <button type="submit" style="padding: 10px; background: #007bff; color: white; border-radius: 5px; border: none;">This Labs tutorial</button>
  </form>
</div>

# Abstract
> [!cornell]
> > 
> >  - replace k bit
> > 
> 
> > 
> > **Main concept:** Quy trình giấu LSB và tách.
> > 
> > **Key points:**
> > - thay đổi `k` bit cuối cùng của một vector bằng `k` bit thông điệp mà mình cần giấu.
> > - vector đấy là giá trị của mẫu.
> > - tách tin thì sẽ cần phải quan tâm đến vấn đề là: chiều dài thông điệp đã giấu bằng bao nhiêu? (có thể tạo header hoặc quy ước ký tự kết thúc, hoặc thống nhất luôn giữa bên giấu với tách là t sẽ giấu bao nhiêu ký tự ở trỏng).
> > 
> > 
> > **Phát hiện dựa trên thống kê**: Histogram
> > **Ưu:** Đơn giản, dễ làm
> > **Nhược:** Dễ bị phát hiện.
> > 
> > 
> > **Links:** [[1. PROJECT/01_Đồ Án/LSB matching\|LSB matching]]
> 
> > 
> > - cắt lát âm thanh → giá trị → replace k bit LSB
> >  - quy ước ký tự kết thúc khi tách tin.


# Lý thuyết quy trình chung

Giả sử chúng ta có:

- **Dữ liệu âm thanh gốc**: Một đoạn âm thanh có các giá trị mẫu (sample values) biên độ dưới dạng số thập phân.
- **Thông điệp bí mật cần giấu**: Chữ cái **'a'**.

Chúng ta sẽ sử dụng **2 bit LSB** (`k=2`) của mỗi mẫu âm thanh để giấu tin.

---

**Các bước giấu tin vào file âm thanh bằng phương pháp LSB:**

1. **Chia dữ liệu âm thanh gốc thành các đoạn và biến đổi thành vector giá trị tín hiệu**:
    
    - Đầu tiên, chương trình sẽ đọc file âm thanh và trích xuất các mẫu âm thanh. Giả sử 4 giá trị mẫu âm thanh đầu tiên của file gốc là: **123, 197, 213, 255**.
    - Các giá trị mẫu này (thường là 8-bit hoặc 16-bit) sẽ được biểu diễn dưới dạng nhị phân. Ví dụ, nếu là 8-bit:
        - 123 = `01111011`
        - 197 = `11000101`
        - 213 = `11010101`
        - 255 = `11111111`
2. **Biến đổi thông tin cần giấu thành dạng nhị phân và xác định chiều dài**:
    
    - Thông điệp bí mật là chữ **'a'**. Mã ASCII của 'a' là 97.
    - Biểu diễn 97 dưới dạng nhị phân (8-bit) là: `01100001`.
    - Chiều dài chuỗi bit thông điệp (L) là 8 bit.
3. **Chọn số bit LSB (`k`) để giấu tin**:
    
    - Trong ví dụ này, chúng ta chọn **`k = 2` bit LSB**. Điều này có nghĩa là mỗi 2 bit của thông điệp sẽ thay thế 2 bit cuối cùng của một mẫu âm thanh.
4. **Chia chuỗi bit thông điệp thành các chuỗi con có độ dài `k` bit**:
    
    - Chuỗi bit thông điệp của 'a' là `01100001`.
    - Chia thành các chuỗi con có độ dài 2 bit: `01`, `10`, `00`, `01`.
5. **Thay thế `k` bit LSB của tín hiệu âm thanh bằng các chuỗi con của thông điệp**:
    
    - Chúng ta sẽ lần lượt thay thế 2 bit LSB của các mẫu âm thanh gốc bằng các chuỗi con vừa chia.
        
    - **Mẫu âm thanh gốc thứ nhất**: 123 (`01111011`)
        
        - 2 LSBs của 123 là `11`.
        - Chuỗi con thông điệp đầu tiên là `01`.
        - Thay thế: `011110`**`01`** (giá trị thập phân mới là 121)
    - **Mẫu âm thanh gốc thứ hai**: 197 (`11000101`)
        
        - 2 LSBs của 197 là `01`.
        - Chuỗi con thông điệp thứ hai là `10`.
        - Thay thế: `110001`**`10`** (giá trị thập phân mới là 194)
    - **Mẫu âm thanh gốc thứ ba**: 213 (`11010101`)
        
        - 2 LSBs của 213 là `01`.
        - Chuỗi con thông điệp thứ ba là `00`.
        - Thay thế: `110101`**`00`** (giá trị thập phân mới là 212)
    - **Mẫu âm thanh gốc thứ tư**: 255 (`11111111`)
        
        - 2 LSBs của 255 là `11`.
        - Chuỗi con thông điệp thứ tư là `01`.
        - Thay thế: `111111`**`01`** (giá trị thập phân mới là 253)
    - **Kết quả**: Các giá trị mẫu âm thanh sau khi giấu tin sẽ là: **121, 194, 212, 253**.
        
    - File âm thanh mới này, chứa các giá trị mẫu đã được thay đổi, chính là **file âm thanh đã giấu tin**.
        

Như bạn thấy, sự thay đổi ở các bit LSB thường rất nhỏ (ví dụ từ 123 xuống 121, từ 197 xuống 194), do đó **chất lượng âm thanh sau khi giấu tin hầu như không bị ảnh hưởng và khó bị phát hiện bằng tai người**. Tuy nhiên, phương pháp này cũng tương đối đơn giản nên dễ bị phát hiện bằng các phương pháp thống kê hoặc bị thay đổi/phá hủy nếu file âm thanh bị xử lý (ví dụ như nén).
 
dựa vào code thì bước giấu tin vào file âm thành thì các đoạn code đó đã thực hiện cụ thể thế nào? 



# Nhận xét về phương pháp
Phương pháp giấu tin **Least Significant Bit (LSB)** là một trong những kỹ thuật cơ bản và phổ biến nhất, đặc biệt là trong các môi trường đa phương tiện như ảnh và âm thanh. Dưới đây là tổng kết ngắn gọn về ưu và nhược điểm của phương pháp này dựa trên các nguồn đã cung cấp:

### **Tổng quan về phương pháp LSB**

LSB là bit có trọng số thấp nhất trong mỗi byte dữ liệu, ví dụ như một điểm ảnh trong ảnh hoặc một mẫu âm thanh. Việc thay đổi giá trị của các bit này thường không ảnh hưởng đáng kể đến chất lượng của dữ liệu gốc, khiến sự thay đổi trở nên khó nhận biết bằng các giác quan thông thường.

### **Ưu điểm của phương pháp LSB**

1. **Tính vô hình cao (khó bị phát hiện bằng giác quan thường):**
    - **Chất lượng hình ảnh/âm thanh hầu như không bị ảnh hưởng:** Thay đổi LSB của một điểm ảnh chỉ làm thay đổi giá trị của điểm ảnh đó lên hoặc xuống một đơn vị, sự thay đổi nhỏ này không làm thay đổi nhiều cấp độ màu của điểm ảnh. Do đó, chất lượng hình ảnh hoặc âm thanh sau khi giấu tin hầu như không bị ảnh hưởng, khiến người dùng khó có thể phân biệt được bằng mắt thường hay tai người.
    - **Khó phát hiện bằng tai người (trong âm thanh):** Đặc biệt trong mã hóa pha (một phương pháp liên quan đến LSB trong âm thanh), với những thay đổi đủ nhỏ, tai người không nhạy cảm với sự thay đổi pha âm thanh nên khó bị phát hiện.
2. **Đơn giản và dễ cài đặt:** Kỹ thuật LSB tương đối đơn giản và dễ dàng cài đặt.
3. **Dung lượng giấu tin lớn:** Phương pháp giấu tin dựa trên thay thế LSB (LSB replacement) cho phép giấu được một lượng thông tin lớn và tốc độ truyền dữ liệu nhanh. Khi giấu 1 bit vào mỗi byte, một kỹ thuật LSB có thể đạt dung lượng 100%. Về mặt thống kê, khoảng một nửa số byte sẽ không cần thay đổi LSB vì đã trùng với bit tin nhắn, giúp nâng cao hiệu quả giấu tin lên 2 bit mỗi lần sửa đổi.

### **Nhược điểm của phương pháp LSB**

Các nhược điểm này chủ yếu liên quan đến kỹ thuật **thay thế LSB (LSB replacement)** đơn giản, vốn được coi là **không an toàn**:

1. **Kém an toàn và dễ bị phát hiện bằng phân tích thống kê:**
    - **Bất thường thống kê do thao tác bất đối xứng:** Kỹ thuật thay thế LSB thực hiện việc nhúng thông tin một cách **bất đối xứng**. Cụ thể, khi thay thế LSB của một giá trị **chẵn** (LSB = 0) bằng bit thông điệp là '1', giá trị byte sẽ tăng lên 1 đơn vị. Ngược lại, khi thay thế LSB của một giá trị **lẻ** (LSB = 1) bằng bit thông điệp là '0', giá trị byte sẽ giảm đi 1 đơn vị. Tuy nhiên, kỹ thuật này **không bao giờ cộng 1 vào một giá trị lẻ** và **không bao giờ trừ 1 từ một giá trị chẵn**.
    - **Tạo ra dấu vết thống kê rõ ràng trên biểu đồ tần suất:** Sự bất đối xứng này dẫn đến một bất thường thống kê rõ rệt trên biểu đồ tần suất (histogram) của các giá trị byte: các cặp thanh chẵn-lẻ liên tiếp sẽ có xu hướng đạt chiều cao tương tự nhau một cách bất thường. Điều này xảy ra do các thanh chẵn nhường một phần giá trị cho thanh lẻ kế tiếp, trong khi các thanh lẻ nhường một phần giá trị cho thanh chẵn đứng trước.
    - **Dễ bị tấn công cấu trúc:** Dấu vết thống kê này có thể bị khai thác bởi một họ các cuộc tấn công được gọi là **tấn công cấu trúc (structural attacks)**, sử dụng các công cụ phân tích giấu tin như Aletheia để phát hiện.
    - **Quy trình giấu tin thô sơ:** Do quy trình giấu tin tương đối thô, thông tin mật dễ bị phát hiện bằng các phương pháp thống kê.
2. **Tính bền vững thấp:** Thông tin mật dễ bị thay đổi do sự tác động vào vật chứa (ví dụ: hình ảnh).
3. **Rủi ro về dải giá trị (đối với LSB matching):** Mặc dù kỹ thuật LSB matching (±1 embedding) an toàn hơn vì nó thực hiện các thay đổi một cách cân bằng hơn, nhưng việc cộng hoặc trừ 1 có thể tạo ra kết quả nằm ngoài dải giá trị cho phép của byte (0-255). Cần kiểm soát để không trừ 1 từ giá trị 0 hoặc cộng 1 vào giá trị 255.

Do những nhược điểm về tính an toàn và khả năng bị phát hiện bằng thống kê, **phương pháp thay thế LSB không được khuyến nghị sử dụng**.

# Ref: 
- [LSB steganography in images and audio.](https://daniellerch.me/stego/intro/lsb-en/#information-embedding-with-lsb-matching)
- [Labs LSB | Audio Steganography](https://tutran21195.github.io/steg-labs/docs/lsb-labs.html)
