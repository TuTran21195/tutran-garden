---
{"dg-publish":true,"dg-path":"1. PROJECT/Audio Steganography/LSB/LSB matching.md","dg-permalink":"2025/stego/lsb-matching","permalink":"/2025/stego/lsb-matching/","title":"LSB matching","created":"2025-09-06T11:10:32.643+07:00","updated":"2025-09-13T16:10:15.860+07:00"}
---


# Abstract

> [!cornell]
> > 
> > - random $(+/-)$ byte value.
> 
> > 
> > **Main concept:** Khái niệm chính
> > 
> > **Key points:**
> > - Giả sử muốn giấu bit `0` vào dữ liệu gốc (vật chứa) `53` (`00110101`)
> > - LSB: Thay bit 1 thành 0 → `53` - 1 = `52`. Nhìn chung là nếu mà LSB mà bị đổi thành 0 thì tức là giá trị gốc sẽ bị `-1` → Thống kê là sẽ bị phát hiện.
> > - LSB matching: 
> > 	- Random chọn việc +1 hoặc -1 vào số `53` tức là nó sẽ đổi thành `53 - 1 = 52`(`00110100`) hoặc `53 + 1 = 54`(`00110110`). Nghĩa là nó đỡ dễ bị phát hiện hơn.
> > 
> > 
> > **Links:** [[1. PROJECT/01_Đồ Án/LSB audio thuần\|LSB audio thuần]] 
> 
> > 
> > - random + hoặc trừ chứ không luôn trừ như thằng LSB.
> > - Khó bị phát hiện dựa trên thống kê hơn.

---

# Triết lý của LSB Matching
Thay vì ghi đè trực tiếp bit ít ý nghĩa nhất (LSB) của mẫu âm thanh, LSB Matching sẽ
●      So sánh LSB của mẫu âm thanh với bit thông điệp cần giấu.
●      Nếu giống nhau, giữ nguyên mẫu.
●      Nếu khác, thay vì thay thế bit, thuật toán sẽ **tăng hoặc giảm nhẹ giá trị mẫu** (±1 vào giá trị byte) sao cho LSB sau khi thay đổi sẽ khớp với bit cần giấu.

Ưu điểm:

●      Khó phát hiện hơn LSB truyền thống bằng các công cụ thống kê
●      Ít gây biến dạng tín hiệu nghe được


# Lý thuyết

### LSB Replacement (Thay thế LSB)

- **Cách hoạt động**: LSB replacement là kỹ thuật **thay thế trực tiếp** bit LSB của dữ liệu vật chứa bằng bit thông điệp cần giấu. Nếu bit LSB hiện tại của vật chứa khác với bit thông điệp, nó sẽ bị thay đổi thành bit thông điệp đó.

### LSB Matching (Đối sánh LSB)

- **Cách hoạt động**: LSB matching (còn gọi là **±1 embedding**) **chỉ thay đổi giá trị của byte bằng cách cộng thêm 1 hoặc trừ đi 1** khi bit LSB của byte đó **không trùng khớp** với bit thông điệp cần giấu. Điều quan trọng là, khi có thể, việc cộng hoặc trừ 1 này được chọn **ngẫu nhiên** để tránh các bất thường thống kê.

### Ví dụ về sự khác biệt

Hãy xem xét một ví dụ cụ thể để thấy rõ sự khác biệt trong quá trình thực hiện:

**Giả sử chúng ta có:**

- **Byte dữ liệu gốc (vật chứa):** `53` (trong hệ nhị phân là `00110101`). **LSB của byte này là `1`**.
- **Bit thông điệp bí mật cần giấu:** `0`.

**1. Với LSB Replacement:**

- **Bước 1**: So sánh LSB của byte gốc (`1`) với bit thông điệp cần giấu (`0`). Chúng không khớp.
- **Bước 2**: Thay thế trực tiếp LSB của byte gốc bằng bit thông điệp cần giấu.
    - `0011010**1**` (53) sẽ được thay thế LSB `1` thành `0`.
    - Kết quả là `0011010**0**`.
- **Kết quả**: Giá trị thập phân mới của byte là `52`.
- **Sự thay đổi**: Giá trị byte đã giảm đi 1 (từ 53 xuống 52). LSB của 52 là 0, trùng với bit cần giấu.

**2. Với LSB Matching:**

- **Bước 1**: So sánh LSB của byte gốc (`1`) với bit thông điệp cần giấu (`0`). Chúng không khớp.
- **Bước 2**: Cần thay đổi LSB của byte gốc thành `0`. LSB matching sẽ xem xét cả việc cộng 1 và trừ 1 để đạt được LSB mong muốn.
    - Nếu ta **trừ đi 1**: `53 - 1 = 52`. Trong hệ nhị phân là `00110100`. LSB là `0`. (Phù hợp)
    - Nếu ta **cộng thêm 1**: `53 + 1 = 54`. Trong hệ nhị phân là `00110110`. LSB là `0`. (Phù hợp)
- **Bước 3**: LSB matching sẽ **chọn ngẫu nhiên** một trong hai thao tác (+1 hoặc -1) nếu cả hai đều hợp lệ (tức là không vượt quá giới hạn 0-255).
    - Giả sử, trong trường hợp này, thuật toán LSB matching **chọn cộng thêm 1**.
- **Kết quả**: Giá trị thập phân mới của byte là `54`.
- **Sự thay đổi**: Giá trị byte đã tăng thêm 1 (từ 53 lên 54). LSB của 54 là 0, trùng với bit cần giấu.

Như vậy, với cùng một byte gốc (`53`) và cùng một bit cần giấu (`0`), **LSB replacement luôn cho ra kết quả là `52`**, trong khi **LSB matching có thể cho ra `52` hoặc `54`** (tùy thuộc vào lựa chọn ngẫu nhiên).

### Tại sao LSB Matching lại tốt hơn?

Sự khác biệt nhỏ trong cách thay đổi này mang lại lợi ích lớn về mặt bảo mật:

- **Tránh bất đối xứng thống kê**: LSB replacement tạo ra sự thay đổi **bất đối xứng** trong phân bố giá trị của dữ liệu. Cụ thể, nó không bao giờ cộng 1 vào một giá trị lẻ để thay đổi LSB thành 0, và không bao giờ trừ 1 từ một giá trị chẵn để thay đổi LSB thành 1. Sự bất cân bằng này tạo ra những dấu hiệu thống kê rõ ràng trên biểu đồ tần suất (histogram) của dữ liệu, khiến các công cụ steganalysis (công cụ phát hiện giấu tin) dễ dàng nhận biết.
- **Khó bị phát hiện**: LSB matching, bằng cách cho phép cả hai hướng thay đổi (+1 hoặc -1) một cách ngẫu nhiên khi LSB cần được thay đổi, giúp duy trì sự cân bằng thống kê tốt hơn. Điều này làm cho biểu đồ tần suất của dữ liệu được giấu tin ít bị biến dạng hơn, và do đó, thông tin được giấu **khó bị phát hiện hơn** bởi các tấn công cấu trúc.

Tóm lại, **LSB matching tốt hơn LSB replacement vì nó không tạo ra các bất thường thống kê dễ bị phát hiện**, mặc dù cả hai đều chỉ thay đổi LSB để nhúng thông tin.


# Code phân tích, thống kê → detect
```python
import wave
import numpy as np
import matplotlib.pyplot as plt
import os


def read_wav(filename):
    """Read samples from a WAV file."""
    try:
        wav_file = wave.open(filename, 'rb')
        nchannels = wav_file.getnchannels()
        sampwidth = wav_file.getsampwidth()
        framerate = wav_file.getframerate()
        nframes = wav_file.getnframes()
        if sampwidth != 2:
            raise ValueError("Only 16-bit WAV files are supported.")
        samples = np.frombuffer(wav_file.readframes(nframes), dtype=np.int16)
        wav_file.close()
        return samples, nchannels, sampwidth, framerate
    except FileNotFoundError:
        print(f"Audio file {filename} not found.")
        return None, None, None, None
    except Exception as e:
        print(f"Error reading WAV file: {e}")
        return None, None, None, None


def extract_lsb(samples):
    """Extract 6 LSBs from each sample."""
    return samples & 0x3F  # Get 6 LSBs (values from 0 to 63)


def analyze_files(file1, file2):
    """Analyze two WAV files for steganography with improved visualization."""
    # Read files
    samples1, nchannels1, sampwidth1, framerate1 = read_wav(file1)
    samples2, nchannels2, sampwidth2, framerate2 = read_wav(file2)
    
    if samples1 is None or samples2 is None:
        return
    
    # Check compatibility
    if (nchannels1 != nchannels2 or sampwidth1 != sampwidth2 or 
        framerate1 != framerate2 or len(samples1) != len(samples2)):
        print("Files are not compatible (different channels, sample width, framerate, or length).")
        return
    
    # Extract LSBs
    lsb1 = extract_lsb(samples1)
    lsb2 = extract_lsb(samples2)
    
    # Calculate sample differences
    diff = samples2 - samples1  # Difference between samples
    
    # Count modified samples
    modified_samples = np.sum(diff != 0)
    total_samples = len(samples1)
    modified_percentage = (modified_samples / total_samples) * 100
    
    # Create histograms
    plt.figure(figsize=(12, 10))
    
    # Histogram of LSB values (first 1000 samples to focus on stego region)
    plt.subplot(2, 1, 1)
    plt.hist(lsb1[:1000], bins=64, range=(0, 64), alpha=0.5, label=os.path.basename(file1), color='blue', density=True)
    plt.hist(lsb2[:1000], bins=64, range=(0, 64), alpha=0.5, label=os.path.basename(file2), color='red', density=True)
    plt.title(f'LSB Distribution (First 1000 Samples): {os.path.basename(file1)} vs {os.path.basename(file2)}')
    plt.xlabel('LSB Value (0 to 63)')
    plt.ylabel('Normalized Frequency')
    plt.legend()
    plt.grid(True, alpha=0.3)
    plt.ylim(0, 0.1)  # Limit y-axis to make differences visible
    
    # Histogram of sample differences (excluding zero to highlight changes)
    non_zero_diff = diff[diff != 0]
    plt.subplot(2, 1, 2)
    if len(non_zero_diff) > 0:
        plt.hist(non_zero_diff, bins=127, range=(-63.5, 63.5), color='green', density=True)
        plt.title(f'Sample Differences (Non-Zero): {os.path.basename(file2)} - {os.path.basename(file1)}')
    else:
        plt.text(0.5, 0.5, 'No differences detected', horizontalalignment='center', verticalalignment='center')
        plt.title(f'Sample Differences: {os.path.basename(file2)} - {os.path.basename(file1)}')
    plt.xlabel('Difference Value')
    plt.ylabel('Normalized Frequency')
    plt.grid(True, alpha=0.3)
    
    plt.tight_layout()
    plt.savefig('stego_analysis_improved.png')
    plt.close()
    
    # Conclusion
    print(f"Analysis Results:")
    print(f"- Total samples: {total_samples}")
    print(f"- Modified samples: {modified_samples} ({modified_percentage:.2f}%)")
    
    # Calculate LSB entropy
    def calculate_entropy(data):
        counts, _ = np.histogram(data, bins=64, range=(0, 64), density=True)
        entropy = -np.sum([p * np.log2(p + 1e-10) for p in counts if p > 0])
        return entropy
    
    entropy1 = calculate_entropy(lsb1)
    entropy2 = calculate_entropy(lsb2)
    print(f"- LSB Entropy ({os.path.basename(file1)}): {entropy1:.2f} bits")
    print(f"- LSB Entropy ({os.path.basename(file2)}): {entropy2:.2f} bits")
    
    # Determine which file is stego
    if modified_samples > 0:
        print(f"\nConclusion: {os.path.basename(file2)} is likely the stego file (contains hidden data).")
        print(f"Reason: {modified_samples} samples differ, indicating LSB modifications.")
    else:
        print(f"\nConclusion: No clear evidence of steganography.")
        print(f"Reason: No sample differences detected.")


def main():
    file1 = input("Enter the first WAV file (original): ")
    file2 = input("Enter the second WAV file (potentially stego): ")
    analyze_files(file1, file2)


if __name__ == "__main__":
    main()

```


# Ref: 
- [LSB steganography in images and audio.](https://daniellerch.me/stego/intro/lsb-en/#information-embedding-with-lsb-matching)

