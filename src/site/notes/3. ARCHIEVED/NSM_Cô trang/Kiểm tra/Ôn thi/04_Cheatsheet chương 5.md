---
{"dg-publish":true,"permalink":"/3-archieved/nsm-co-trang/kiem-tra/on-thi/04-cheatsheet-chuong-5/","created":"2025-06-06T15:26:31.435+07:00"}
---



**Cheatsheet - Chương 5: Một số giải pháp nguồn mở cho NSM**

**1. Giới thiệu chung**

- **Nền tảng độc quyền:**
    - Cung cấp giải pháp **tất cả trong một**.
    - Ví dụ: LogRhythm, QRadar, ArcSight.
    - **Khá đắt** khi sử dụng lâu dài và thường nhắm đến các tổ chức lớn.
- **Giải pháp mã nguồn mở (Open Source):**
    - Thường **kết hợp các phần mềm nguồn mở khác** để tạo ra giải pháp bảo mật.
    - Hướng tới việc **phòng thủ**.
    - Thường **ưu tiên cho khả năng quan sát/hiển thị (visibility)**.
    - Các giải pháp được đề cập trong chương: OSSIM, ELK Stack, OSSEC, Wazuh, Apache Metron, SIEMonster, Prelude, và Security Onion.

**2. Các Giải pháp Cụ thể (Thông tin từ nguồn)**

- **OSSIM**
    - Phát triển bởi **AlienVault's Unified Security Management (USM)**.
    - **Bao gồm:** FProbe, Munin, Nagios, NFSen/NFDump, OpenVAS, OSSEC, PRADS, Snort, Suricata và TCPTrack.
    - (Link: https://github.com/alienfault/ossim).
- **ELK Stack**
    - (Link: https://www.elastic.co/fr/what-is/elk-stack). (Nguồn chỉ cung cấp link).
- **OSSEC và Wazuh**
    - (Link OSSEC: https://www.ossec.net/about/). (Nguồn chỉ cung cấp link).
    - (Link Wazuh: https://wazuh.com/). (Nguồn chỉ cung cấp link).
- **Apache Metron**
    - (Link: https://metron.apache.org/). (Nguồn chỉ cung cấp link).
- **SIEMonster**
    - (Link: https://siemonster.com/). (Nguồn chỉ cung cấp link).
- **Prelude**
    - Là một **khuôn khổ SIEM thống nhất** nhiều công cụ mã nguồn mở khác nhau.
    - **Các tính năng:** khả năng lọc, tương quan, cảnh báo, phân tích và trực quan hóa.
    - **Phiên bản mã nguồn mở (Prelude OSS) bị hạn chế đáng kể** so với bản thương mại về tất cả các tính năng này.
    - **Prelude OSS** nhằm mục đích **đánh giá, nghiên cứu và thử nghiệm trên các môi trường rất nhỏ**.
    - Hiệu suất Prelude OSS **thấp hơn nhiều** so với phiên bản Prelude SIEM (thương mại).
    - (Link: https://www.prelude-siem.com/en/oss-version/).
- **Security Onion**
    - Là một **bộ công cụ khá toàn diện**.
    - Có thể **khá phù hợp cho việc thử nghiệm trong môi trường nhỏ**.
    - **Gồm nhiều công cụ mã nguồn mở như:** ELK Stack, Snort, Suricata, Sguil, Squert, Snorby, Bro/Zeek, NetworkMiner, Xplico, và nhiều các công cụ an toàn khác.
    - **Sinh viên có thể thử nghiệm giải pháp Security Onion** là nền tảng theo dõi giám sát tất cả trong một một cách nhanh chóng.
    - Các giải pháp khác cũng rất đáng để thử nghiệm.

**3. Kết chương**

- Các giải pháp mã nguồn mở hiện có thường kết hợp với các phần mềm nguồn mở khác để tạo ra một giải pháp bảo mật hướng tới việc phòng thủ và thường ưu tiên cho khả năng hiển thị.
- **Security Onion được đề xuất cho sinh viên thử nghiệm** như một nền tảng giám sát tất cả trong một.
