---
{"dg-publish":true,"permalink":"/1-project/kiem-thu-xam-nhap/cheatsheet-chuong-3/","title":"KTXN - Cheatsheet chương 3","tags":["tutran-garden","cheatsheet"],"created":"2025-05-25T11:02:55.129+07:00"}
---


# Cheetsheet - Prompt 1


**CHEATSHEET ÔN TẬP CHƯƠNG 3: KIẾN TRÚC MÁY TÍNH, HỆ ĐIỀU HÀNH VÀ CÁC KỸ THUẬT KHAI THÁC CƠ BẢN**

Dựa trên các tài liệu: "So luoc KTMT_HDH_Chuong 1", "So luoc KTMT_HDH_Chuong 2", "On tap kien thuc linux, C, assembly", "Cach ham hoat dong", "Gioi thieu ve RE 1", "Gioi thieu ve RE 2", "Buffer Overflow, Integer and Heap Overflow", "Stack Overflow examples", "Shellcoding".

## **1. Kiến trúc và Chức năng của Máy tính (Tổng quan - Chương 1)**

- **Bộ xử lý trung tâm (CPU)**:
    - **Chức năng**: Đọc lệnh từ bộ nhớ, giải mã và thực hiện lệnh.
    - **Bao gồm**: Khối điều khiển (CU), Khối tính toán số học và logic (ALU), Các thanh ghi (Registers), Bus trong CPU.
- **Biểu diễn dữ liệu trong Máy tính**:
    - Sử dụng **hệ nhị phân** (0 và 1) để biểu diễn dữ liệu. 0: False, 1: True.
    - Sử dụng **hệ hexa** (0-9, A-F).
    - Số trong hệ thập phân có thể biểu diễn dạng đa thức (ví dụ: 123 = 1*10² + 2*10¹ + 3*10⁰).
    - Số trong hệ nhị phân cũng biểu diễn dạng đa thức (ví dụ: (11001010)₂ = 1*2⁷ + 1*2⁶ + 0*2⁵ + ... = 202)₁₀.
- **Tổ chức dữ liệu**:
    - **Bits**: Đơn vị dữ liệu nhỏ nhất, lưu trữ 0 hoặc 1, true hoặc false.
    - **Nibbles**: Nhóm 4 bits, lưu 16 giá trị (0000₂ đến 1111₂) hoặc 1 số hexa.
    - **Bytes**: Nhóm 8 bits hoặc 2 nibbles, lưu 256 giá trị (0000 0000₂ đến 1111 1111₂) hoặc (00₁₆ đến FF₁₆).
    - **Words**: Nhóm 16 bits (2 bytes), lưu 2¹⁶ giá trị (0000₁₆ đến FFFF₁₆).
    - **Double words**: Nhóm 32 bits (4 bytes, 2 words), lưu 2³² giá trị (0000 0000₁₆ đến FFFF FFFF₁₆).
- **Số có dấu và không dấu**:
    - **Số có dấu**: Bit trái nhất biểu diễn dấu (0: dương, 1: âm).
    - **Phạm vi biểu diễn (n bits)**:
        - Có dấu: từ -2ⁿ⁻¹ tới +2ⁿ⁻¹-1 (ví dụ: 8 bits: -128 đến +127).
        - Không dấu: từ 0 tới 2ⁿ-1 (ví dụ: 8 bits: 0 đến 255).
- **Bảng mã ASCII**: Sử dụng 8 bit để biểu diễn 1 ký tự tiếng Anh. Định nghĩa 128 ký tự (33 điều khiển, 94 ký tự).

## **2. Khối Xử lý Trung tâm (CPU) và Tập lệnh (Chương 2)**

- **CPU - Sơ đồ khối tổng quát**: Bao gồm CU, IR, PC, MAR, MBR, ALU, Registers (A, Y, Z, FR), Internal Bus.
- **Chu kỳ xử lý lệnh**: Hệ điều hành tải chương trình vào bộ nhớ trong.
    1. Địa chỉ lệnh đầu tiên vào **PC**.
    2. Địa chỉ từ PC -> bus A qua **MAR**.
    3. Bus A truyền địa chỉ tới **MMU**.
    4. MMU chọn ô nhớ và sinh tín hiệu READ.
    5. Lệnh từ ô nhớ -> bus D qua **MBR**.
    6. MBR -> **IR**. IR -> **CU**.
    7. CU giải mã lệnh, sinh tín hiệu điều khiển cho các đơn vị khác (ví dụ: ALU).
    8. PC tăng lên trỏ tới lệnh tiếp theo.
    9. Lặp lại các bước 3-9.
- **Thanh ghi (Registers)**:
    - Thành phần nhớ bên trong CPU, lưu tạm lệnh và dữ liệu.
    - Dung lượng nhỏ, số lượng ít, tốc độ rất cao.
    - Kích thước phụ thuộc thiết kế CPU (8, 16, 32, 64, 128, 256 bit).
    - **Thanh ghi Tích lũy A (Accumulator)**: Lưu toán hạng đầu vào, kết quả đầu ra, trao đổi dữ liệu với thiết bị I/O.
    - **Bộ đếm Chương trình PC (Program Counter/Instruction Pointer)**: Lưu địa chỉ bộ nhớ của lệnh tiếp theo.
    - **Thanh ghi Trạng thái FR (Flag Register)**: Mỗi bit lưu trạng thái kết quả phép tính của ALU. Gồm cờ trạng thái (CF, OF, AF, ZF, PF, SF) và cờ điều khiển (IF, TF, DF). Bit cờ dùng làm điều kiện rẽ nhánh.
        - ZF (Zero Flag): =1 nếu kết quả =0.
        - SF (Sign Flag): =1 nếu kết quả âm.
        - CF (Carry Flag): =1 nếu có nhớ/mượn ở bit trái nhất.
        - OF (Overflow Flag): =1 nếu có tràn.
    - **Con trỏ Ngăn xếp SP (Stack Pointer)**: Luôn trỏ tới đỉnh ngăn xếp (LIFO). Thao tác: Push (SP  SP+1, {SP}  Data), Pop (Register  {SP}, SP  SP-1).
    - **Thanh ghi Lệnh IR (Instruction Register)**: Lưu trữ lệnh đang được xử lý. Nhận lệnh từ MBR, chuyển tới CU giải mã.
    - **Thanh ghi MAR và MBR**:
        - **MAR (Memory Address Register)**: Giao diện CPU-bus địa chỉ. Nhận địa chỉ lệnh từ PC, chuyển tới bus địa chỉ.
        - **MBR (Memory Buffer Register)**: Giao diện CPU-bus dữ liệu. Nhận lệnh từ bus dữ liệu, chuyển tới IR.
    - **Thanh ghi tạm thời (Temporary Register)**: Lưu toán hạng/kết quả đầu ra, hỗ trợ xử lý song song/thực hiện không trật tự (OOO).
    - **Thanh ghi Đa năng**: Sử dụng cho nhiều mục đích (ví dụ: AX, BX, CX, DX trong 8086).
- **Khối Điều khiển CU (Control Unit)**: Điều khiển mọi hoạt động của CPU theo xung nhịp đồng hồ. Nhận đầu vào (lệnh từ IR, giá trị cờ, xung đồng hồ). Sinh tín hiệu điều khiển nội bộ CPU và ngoại vi.
- **Khối Số học và Logic ALU (Arithmetic and Logic Unit)**: Thực hiện phép toán số học (ADD, SUB, MUL, DIV, INC, DEC) và logic (NOT, AND, OR, XOR, COMPARE, SHIFT, ROTATE). Có 2 cổng IN nhận đầu vào, 1 cổng OUT gửi kết quả tới thanh ghi.
- **Bus trong (Internal Bus)**: Kênh liên lạc của các thành phần trong CPU. Hỗ trợ 2 chiều, giao diện với bus ngoài, tốc độ cao hơn bus ngoài.
- **Tập lệnh Máy tính**:
    - **Lệnh máy tính**: Từ nhị phân thực hiện nhiệm vụ cụ thể. Lưu trong bộ nhớ, đọc vào CPU giải mã/thực hiện.
    - **Tập lệnh**: Gồm nhiều lệnh, phân nhóm theo chức năng (vận chuyển dữ liệu, tính toán, điều khiển/rẽ nhánh, I/O).
    - **Các pha thực hiện lệnh**: Mỗi lệnh qua 4 giai đoạn:
        1. **Đọc lệnh (Instruction Fetch - IF)**: Lệnh đọc từ bộ nhớ vào CPU.
        2. **Giải mã lệnh (Instruction Decode - ID)**: CPU giải mã lệnh.
        3. **Chạy lệnh (Instruction Execution - IE)**: CPU thực hiện lệnh.
        4. **Ghi (Write Back - WB)**: Ghi kết quả (nếu có) vào thanh ghi/bộ nhớ.
- **Khuôn dạng lệnh**: Gồm Mã lệnh (opcode) và Địa chỉ các toán hạng (addresses of operands). Số lượng toán hạng (0, 1, 1.5, 2, 3 địa chỉ) phụ thuộc lệnh.
- **Các chế độ địa chỉ**: Cách thức CPU tổ chức toán hạng.
    - **Tức thì (Immediate)**: Giá trị toán hạng nguồn có sẵn trong lệnh (hằng số). (Ví dụ: LOAD R1, #1000).
    - **Trực tiếp/Tuyệt đối (Direct/Absolute)**: Một toán hạng là địa chỉ ô nhớ chứa dữ liệu. (Ví dụ: LOAD R1, 1000).
    - **Gián tiếp (Indirect)**: Thanh ghi/ô nhớ lưu địa chỉ của toán hạng.
        - Gián tiếp thanh ghi: LOAD Rj, (Ri); M[Ri]  Rj.
        - Gián tiếp bộ nhớ: LOAD Ri, (1000); M[M]  Ri.
    - **Chỉ số (Indexed)**: Địa chỉ toán hạng = hằng số (trong lệnh) + nội dung thanh ghi chỉ số. (Ví dụ: LOAD Ri, X(Rind)).
    - **Tương đối (Relative)**: Địa chỉ toán hạng = hằng số + nội dung thanh ghi PC. (Ví dụ: LOAD Ri, X(PC)).
- **Một số dạng lệnh thông dụng**:
    - **Vận chuyển dữ liệu**: MOVE, LOAD, STORE, PUSH, POP.
    - **Số học và logic**: ADD, SUB, MUL, DIV, INC, DEC, NOT, AND, OR, XOR, COMPARE, SHIFT, ROTATE.
    - **Điều khiển/Tuần tự**: Thay đổi trình tự thực hiện lệnh. Rẽ nhánh có/không điều kiện (BRANCH/JUMP), CALL, RETURN. Thay đổi giá trị PC. Sử dụng cờ ALU.
    - **Vào/Ra (I/O)**: Truyền dữ liệu giữa máy tính và thiết bị ngoại vi qua cổng có địa chỉ. INPUT (ngoại vi -> VXL), OUTPUT (VXL -> ngoại vi).

## **3. Ôn tập Kiến thức Linux, C, x86 Assembly**

- **Linux**: Hệ điều hành mã nguồn mở, phát triển trên UNIX, sử dụng kernel Linux. Viết bằng C và assembly. Sử dụng ELF (Executable and Linkable Format) files.
    - **Một số lệnh cơ bản**: `ls`, `cd`, `pwd`, `man`, `apropos`, `cat`, `less`, `mv`, `cp`, `rm`, `nano/vim/emacs`. `|` (pipes) nối các lệnh.
- **Ngôn ngữ C**: Ngôn ngữ lập trình hướng thủ tục cho các hệ thống. Biên dịch nhanh, kiểm soát tốt bộ nhớ. Được coi là 'cấp thấp' so với ngôn ngữ hiện đại. Được dùng để viết kernel Linux. (Ví dụ về `read` vào buffer và lỗi tràn buffer tiềm năng).
- **x86 Assembly**: Ngôn ngữ lập trình hợp ngữ cho phép tương tác trực tiếp với phần cứng, kiểm soát cao. Biên dịch thành executable files/dynamic libraries.
    - **Cú pháp**: Tập lệnh, toán hạng (Operands, OpCode, mnemonics). Cú pháp Intel (đích, nguồn: `mov eax, 5`) và AT&T (nguồn, đích: `mov $5, eax`).
    - **Các thanh ghi quan trọng**:
        - **EAX, EBX, ECX, EDX**: Thanh ghi đa năng.
        - **ESP (Stack Pointer)**: Con trỏ đầu ngăn xếp (bộ nhớ thấp hơn).
        - **EBP (Base Pointer)**: Con trỏ cơ sở ở đáy khung ngăn xếp (bộ nhớ cao hơn). Còn gọi là Frame Pointer.
        - **EIP (Instruction Pointer)**: Con trỏ tới lệnh tiếp theo CPU thực hiện. Lưu địa chỉ trả về của hàm gọi.
        - **EFLAGS**: Lưu trữ các bit cờ (ZF, IF, SF).
    - **Di chuyển dữ liệu**: `mov` (thanh ghi <-> thanh ghi, giá trị hằng, bộ nhớ). `DWORD PTR [địa chỉ]` chỉ định kích thước 4 byte.
    - **Các phép tính toán học**: `sub`, `add`, `inc`, `dec`, `xor`, `or`.
    - **Một số bước nhảy có điều kiện**: `jz` (ZF=1), `jnz` (ZF=0), `jg` (đích > nguồn).
    - **Thao tác với ngăn xếp**:
        - `push ebx`: Trừ 4 từ ESP, sao chép EBX vào đỉnh ngăn xếp.
        - `pop ebx`: Sao chép giá trị từ đỉnh ngăn xếp vào EBX, thêm 4 vào ESP.
    - **Calling / Returning**:
        - `call some_function`: Đẩy EIP hiện tại vào ngăn xếp, nhảy tới `some_function`.
        - `ret`: Bật đỉnh ngăn xếp thành EIP, trở về từ hàm.
        - `nop`: "no operation", không làm gì cả. (\x90).

## **4. Cách hoạt động của hàm trong ngăn xếp**

- **Hàm (Function)**: Chương trình con, tái sử dụng mã, có thể gọi từ bất kỳ đâu. Có tham số đầu vào, giá trị trả về, biến cục bộ. Biến cục bộ tồn tại trong phạm vi hàm.
- **Lưu trữ giá trị**:
    - Tham số đầu vào: Đẩy vào ngăn xếp trước khi gọi hàm.
    - Biến cục bộ: Lưu trong bộ nhớ của ngăn xếp.
- **Quá trình gọi hàm**: Đẩy tham số -> nhảy đến địa chỉ hàm -> thực thi mã hàm -> quay lại lệnh tiếp theo sau lời gọi hàm.
- **Ngăn xếp (Stack)**: Hoạt động theo nguyên tắc LIFO. ESP trỏ đến đầu ngăn xếp.
- **Khung ngăn xếp (Stack Frame)**: Vùng bộ nhớ trên ngăn xếp dành cho một lần gọi hàm. Mỗi lần gọi hàm -> khung mới trên ngăn xếp. Khi hàm trả về, khung bị "unwound"/"collapsed".
    - EBP (Frame Pointer) chỉ đến vùng nằm trong ngăn xếp. Các biến cục bộ và tham số có quan hệ với EBP.
- **Prologue**: Phần mã lúc đầu hàm, lưu EBP cũ và đặt EBP lên đầu khung ngăn xếp mới.
- **Epilogue**: Phần mã cuối hàm, dọn dẹp khung ngăn xếp, khôi phục EBP cũ. ESP trỏ đến nơi EIP được lưu.
- **Return**: Lệnh `RET` bật giá trị EIP đã lưu trở lại thanh ghi EIP. Chương trình trở về lệnh tiếp theo sau lệnh `CALL`.

## **5. Kỹ thuật Reverse Engineering (RE)**

- **Khái niệm**: Phân tích một chương trình nhị phân để hiểu cách nó hoạt động.
- **Static RE**: Phân tích mã mà không chạy chương trình (ví dụ: xem mã assembly).
- **Dynamic RE**: Phân tích mã bằng cách chạy chương trình và theo dõi hành vi (ví dụ: sử dụng debugger).
- **Tools**:
    - **Hex Editors/Viewers**: wxHexEditor (GUI), xxd (dòng lệnh).
    - **strings**: Hiển thị chuỗi ASCII > 4 ký tự.
    - **File Format Tools**:
        - Linux: `readelf` (xem cấu trúc ELF).
        - Windows: Peview.exe (xem cấu trúc PE).
        - Unknown: `file` (xác định loại file).
    - **Hashing**: `md5sum` (kiểm tra file giống nhau?), `ssdeep` (fuzzy hashing - kiểm tra file tương tự). Upload hash lên virustotal.com.
    - **Disassemblers**: `objdump -d` (dòng lệnh, cú pháp AT&T theo mặc định). IDA Pro.exe (GUI, mạnh mẽ).
    - **Debuggers**: IDA Pro (cũng có chức năng debugger), Evan’s Debugger (edb - Windows), GNU Debugger (gdb - Linux).
    - **IDA Pro Basics**: Thay đổi chế độ xem (space bar). Đổi tên biến (n). Comment (: hoặc ;). Chuyển đổi format hằng số (chuột phải). Tìm kiếm tham chiếu (x). Xem stack usage trong assembly.
    - **GDB Basics**: `disassemble [hàm]` (`disas main`). `set disassembly-flavor intel` (đổi cú pháp assembly). `break [địa chỉ/tên hàm/dòng]` (`b main`). `run [args]`. `stepi` (s - từng lệnh assembly). `nexti` (n - từng lệnh assembly, nhảy qua hàm con). `examine memory` (`x/NFU address`). `list` (xem mã nguồn C với số dòng). `info frame` (xem thông tin khung ngăn xếp hiện tại: EIP, EBP, biến cục bộ, tham số). `x &variable` (xem địa chỉ và giá trị biến). `x address` (xem nội dung bộ nhớ tại địa chỉ). `backtrace` (trace lời gọi hàm).

## **6. Lỗi tràn bộ đệm (Buffer Overflow)**

- **Khái niệm**: Xảy ra khi dữ liệu được ghi vào một vùng đệm vượt quá kích thước cho phép, làm ghi đè lên dữ liệu ở các vùng bộ nhớ lân cận.
- **IA32 Stack**: Vùng bộ nhớ được quản lý theo nguyên tắc stack, phát triển về phía địa chỉ thấp hơn. %esp trỏ đến địa chỉ stack thấp nhất.
- **Cấu trúc Stack Frame (IA32/Linux)**:
    - Từ trên xuống dưới (địa chỉ cao xuống thấp):
        - Tham số cho hàm sắp gọi ("Argument build").
        - Biến cục bộ (nếu không giữ trong thanh ghi).
        - Ngữ cảnh thanh ghi đã lưu (Saved register context).
        - **Con trỏ khung cũ (Old frame pointer)** - Saved %ebp.
        - **Địa chỉ trả về (Return address)** - Old EIP.
        - Tham số cho lệnh gọi hàm hiện tại.
    - %esp trỏ đến đỉnh stack (địa chỉ thấp nhất). %ebp trỏ đến đáy khung hiện tại (địa chỉ cao hơn).
- **Khai thác Stack Buffer Overflow**: Ghi đè dữ liệu vào buffer trên stack để ghi đè lên các dữ liệu quan trọng nằm liền kề, phổ biến nhất là ghi đè **Địa chỉ trả về (Return Address)** trên stack. Khi hàm kết thúc, CPU sẽ nhảy đến địa chỉ giả mạo, thay đổi luồng thực thi chương trình.
    - **Ví dụ stack1.c**: Ghi đè biến `cookie` nằm sau buffer.
    - **Ví dụ stack4.c**: Ghi đè địa chỉ trả về để nhảy đến một phần mã khác trong chương trình (Return-to-text).
    - **Hàm `gets()`**: Dễ bị tấn công buffer overflow vì không kiểm tra kích thước đầu vào. Có vấn đề với ký tự xuống dòng `0x0A` (kết thúc chuỗi).
- **Các biện pháp bảo vệ Stack Overflow**:
    - **Stack Smashing Protection (SSP)** / StackGuard / StackShield: Chèn một giá trị ngẫu nhiên (Canary) giữa buffer và địa chỉ trả về/EBP cũ. Kiểm tra giá trị canary trước khi hàm trả về. Nếu canary bị thay đổi, chương trình bị dừng (`stack smashing detected`). Có thể bỏ qua bằng `-fno-stack-protector` (gcc).
    - **Non-executable Stack** / Data Execution Prevention (DEP) / PaX/ExecShield: Đánh dấu vùng nhớ stack là không được thực thi mã. Ngăn việc đặt shellcode trực tiếp trên stack và nhảy đến đó. Có thể bỏ qua bằng cờ biên dịch `-z execstack` (gcc) hoặc `execstack -s`.
    - **Address Space Layout Randomization (ASLR)**: Ngẫu nhiên hóa địa chỉ cơ sở của các vùng bộ nhớ (mã thực thi, thư viện, stack, heap) mỗi lần chương trình chạy. Khó đoán địa chỉ chính xác để nhảy tới (địa chỉ trả về, địa chỉ shellcode). Có thể bỏ qua bằng cách thiết lập `kernel.randomize_va_space = 0`.
    - **Libsafe**: Thay thế các hàm không an toàn (như strcpy) bằng phiên bản an toàn hơn.

## **7. Lỗi tràn số nguyên (Integer Overflow) và tràn Heap (Heap Overflow)**

- **Integer Overflow**: Xảy ra khi kết quả của một phép toán số học vượt quá phạm vi biểu diễn của kiểu dữ liệu số nguyên.
    - **Đặc điểm chung của lỗ hổng Integer Overflow**: Nguồn không tin cậy (untrusted source), kiểm tra không đầy đủ (incomplete check), tràn số nguyên (integer overflow), thao tác nhạy cảm (sensitive operation).
    - Ví dụ: Đọc kích thước từ nguồn không tin cậy, kiểm tra kích thước đó nhưng phép nhân sau đó gây tràn số nguyên, dẫn đến cấp phát bộ nhớ nhỏ hơn dự kiến. Thao tác ghi dữ liệu vào vùng bộ nhớ này sẽ gây tràn heap (heap overflow). (Ví dụ về CVE-2008-5238, CVE-2008-1722, CVE-2008-2430).
- **Heap Overflow**: Xảy ra khi dữ liệu được ghi vào một vùng đệm trên heap vượt quá kích thước cho phép, làm ghi đè lên dữ liệu ở các vùng bộ nhớ lân cận trên heap. Có thể khai thác để thay đổi cấu trúc dữ liệu nội bộ của bộ quản lý heap hoặc ghi đè dữ liệu quan trọng khác trên heap.

## **8. Shellcoding**

- **Shellcode**: Một chuỗi mã máy (thường viết bằng assembly) dùng để khai thác lỗ hổng bảo mật. Thay đổi luồng điều khiển để thực hiện hành động độc hại (ví dụ: mở shell, thực thi lệnh). Cũng có thể dùng cho mục đích kiểm thử bảo mật.
- **Mục tiêu khai thác Buffer Overflow với Shellcode**: Tràn buffer, thay đổi EIP để trỏ đến đoạn mã máy trong chính stack và thực thi nó.
- **NOP Sled**: Một chuỗi các lệnh NOP (`\x90`) đặt trước shellcode. Khi EIP trỏ vào bất kỳ đâu trong NOP sled, CPU sẽ thực hiện các lệnh NOP và trượt đến shellcode. Hữu ích khi không biết chính xác địa chỉ của shellcode.
- **Cách viết Shellcode**:
    - Cách dài dòng: Viết C -> dịch sang assembly (dùng gdb) -> viết assembly -> dịch sang mã máy.
    - Cách ngắn: Viết thẳng bằng assembly -> dịch sang mã máy (dùng nasm).
    - Cách lười/chuyên nghiệp: Sử dụng bytecode có sẵn hoặc xây dựng thư viện riêng.
- **System Calls (Unix)**: Shellcode thường gọi các hàm hệ thống (system calls) để thực hiện tác vụ (ví dụ: `write`, `execve`, `exit`). Gọi system call bằng cách bỏ mã số của system call vào thanh ghi `%eax`, các tham số vào `%ebx, %ecx, %edx`, sau đó gọi ngắt `int 0x80` để chuyển sang chế độ kernel.
- **Vấn đề với NULL byte**: Các hàm xử lý chuỗi như `strcpy` dừng copy khi gặp byte `\x00` (NULL byte). Shellcode không được chứa `\x00` nếu được copy bằng các hàm này, đặc biệt là trước phần địa chỉ trả về. Cần tránh sử dụng các lệnh/giá trị hằng sinh ra byte `\x00` hoặc sử dụng các kỹ thuật để bypass (ví dụ: sử dụng các lệnh di chuyển byte/word thay vì double word, tính toán giá trị runtime).
- **Vấn đề kích thước/vị trí shellcode**: Buffer có thể quá nhỏ để chứa toàn bộ shellcode. Cần tìm vị trí phù hợp để đặt shellcode (ví dụ: buffer, biến môi trường, vùng nhớ khác).
- **Bypassing Non-executable Stack**: Nếu stack không thực thi, không thể đặt shellcode trên stack. Kỹ thuật thay thế: Return-to-libc (nhảy đến hàm có sẵn trong thư viện chuẩn như `system` hoặc `execve`). Cần tìm địa chỉ hàm `system` hoặc `execve` và địa chỉ chuỗi lệnh cần thực thi ("/bin/sh").
- **Bypassing ASLR**: Khó đoán địa chỉ chính xác. Kỹ thuật: Sử dụng NOP sled để tăng khả năng đoán trúng. Đoán địa chỉ stack pointer hiện tại, trừ đi một offset để tìm địa chỉ NOP sled. Quay về thư viện chuẩn (Return-to-libc) vẫn cần đoán địa chỉ hàm trong libc, nhưng libc có thể được ngẫu nhiên hóa. Position-Independent Executables (PIE) và Position-Independent Code (PIC) làm ngẫu nhiên cả địa chỉ mã thực thi.
- **Công cụ hỗ trợ shellcoding**: Online x86/x64 Assembler/Disassembler, Keystone, Capstone. Shell-storm.org, exploit-db.com (kho shellcode).
