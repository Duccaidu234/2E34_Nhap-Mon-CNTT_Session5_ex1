# BÁO CÁO VÀ KẾ HOẠCH TÀI CHÍNH CÁ NHÂN VỚI CHAIN-OF-THOUGHT (COT)

Dưới đây là nội dung chi tiết hoàn chỉnh thực hiện yêu cầu bài toán lập kế hoạch tài chính cá nhân sử dụng kỹ thuật suy luận từng bước (**Chain-of-Thought**), thiết kế prompt, minh họa số liệu cụ thể, trình bày rõ ràng nhật ký suy luận và bảng phân bổ ngân sách theo đúng các tiêu chí kỹ thuật đã đề ra.

---

## PHẦN I: THIẾT KẾ PROMPT MẪU ỨNG DỤNG CHAIN-OF-THOUGHT

Để định hướng LLM thực hiện đúng quy trình logic, tránh sai sót số học và tuân thủ các ràng buộc tài chính, câu lệnh (Prompt) mẫu được thiết kế như sau:

```text
Bạn là một chuyên gia tư vấn tài chính cá nhân chuyên nghiệp. Hãy xây dựng một kế hoạch tài chính cá nhân hàng tháng dựa trên dữ liệu đầu vào dưới đây bằng kỹ thuật suy luận từng bước (Chain-of-Thought).

### Dữ liệu đầu vào (Ví dụ thực tế):
- Tổng thu nhập dự kiến trong tháng: 25.000.000 VNĐ
- Thuế và chi phí cố định bắt buộc (Nhà cửa, điện nước, bảo hiểm, v.v.): 8.000.000 VNĐ
- Các khoản nợ cần thanh toán (Gốc + Lãi tối thiểu): 5.000.000 VNĐ
- Tỷ lệ mục tiêu tiết kiệm tối thiểu: 20% tổng thu nhập (hoặc trên thu nhập khả dụng tùy cơ cấu)

### Yêu cầu đặc biệt:
Hãy suy nghĩ từng bước một và tính toán chi tiết trước khi đưa ra quyết định. Tuyệt đối không được nhảy cóc số liệu hoặc đưa ra đáp án cuối cùng ngay từ đầu.

### Quy trình suy luận bắt buộc:
1. Bước 1: Tính toán tổng thu nhập khả dụng (Net Disposable Income) sau khi trừ đi thuế và chi phí cố định bắt buộc.
2. Bước 2: Xác định và phân bổ khoản tiền trả nợ tối thiểu theo cam kết.
3. Bước 3: Trích lập quỹ tiết kiệm theo tỷ lệ cam kết (tối thiểu 20%).
4. Bước 4: Phân bổ phần ngân sách còn lại cho chi tiêu linh hoạt dựa trên quy tắc 50/30/20 cải tiến.

### Cấu trúc kết quả đầu ra:
- Phần 1: Nhật ký suy luận logic (Reasoning Steps) trình bày rõ từng bước với các phép tính cộng, trừ, nhân, chia trung gian tường minh.
- Phần 2: Bảng phân bổ ngân sách cuối cùng bằng Markdown Table với các cột: [Hạng mục], [Số tiền (VNĐ)], [Tỷ lệ %], [Ghi chú]. Đảm bảo tổng tỷ lệ phần trăm chính xác tuyệt đối 100%.
```

---

## PHẦN II: MINH HỌA THỰC TẾ QUY TRÌNH SUY LUẬN VÀ BẢNG PHÂN BỔ NGÂN SÁCH

Dưới đây là kết quả thực hiện chi tiết dựa trên dữ liệu giả định:
*   **Tổng thu nhập dự kiến ($I$):** 25.000.000 VNĐ
*   **Chi phí cố định bắt buộc ($F$):** 8.000.000 VNĐ
*   **Các khoản nợ ($D$):** 5.000.000 VNĐ
*   **Mục tiêu tiết kiệm ($S$):** 20% trên tổng thu nhập = $25.000.000 \times 0,20 = 5.000.000$ VNĐ

---

### Phần 1: Nhật ký suy luận logic (Reasoning Steps)

*   **Bước 1: Tính toán thu nhập khả dụng sau chi phí cố định**
    *   Công thức: $\text{Thu nhập khả dụng} = \text{Tổng thu nhập} - \text{Chi phí cố định bắt buộc}$
    *   Phép tính trung gian: $25.000.000 - 8.000.000 = 17.000.000$ VNĐ
    *   *Kết luận bước 1:* Thu nhập còn lại sau khi bảo đảm sinh hoạt thiết yếu là **17.000.000 VNĐ**.

*   **Bước 2: Phân bổ khoản tiền trả nợ tối thiểu**
    *   Công thức: Trừ trực tiếp khoản nợ bắt buộc phải trả trong tháng từ nguồn tiền khả dụng.
    *   Phép tính trung gian: $17.000.000 - 5.000.000 = 12.000.000$ VNĐ
    *   *Kết luận bước 2:* Đã hoàn thành nghĩa vụ trả nợ **5.000.000 VNĐ**. Dòng tiền còn lại tiếp tục phân bổ là **12.000.000 VNĐ**.

*   **Bước 3: Trích lập quỹ tiết kiệm theo tỷ lệ cam kết**
    *   Công thức: $\text{Tiết kiệm} = \text{Tổng thu nhập} \times 20\%$
    *   Phép tính trung gian: $25.000.000 \times \frac{20}{100} = 5.000.000$ VNĐ
    *   *Kết luận bước 3:* Trích quỹ tiết kiệm/đầu tư số tiền **5.000.000 VNĐ**. Số tiền còn lại để phân bổ cho chi tiêu linh hoạt: $12.000.000 - 5.000.000 = 7.000.000$ VNĐ.

*   **Bước 4: Phân bổ chi tiêu linh hoạt (Quy tắc 50/30/20 cải tiến)**
    *   Phần ngân sách còn lại cho chi tiêu linh hoạt (ăn uống ngoài, giải trí, mua sắm cá nhân, phát sinh) là **7.000.000 VNĐ**.
    *   Kiểm tra tỷ trọng phần trăm của từng khoản so với tổng thu nhập (25.000.000 VNĐ):
        *   Tỷ lệ Chi phí cố định: $\frac{8.000.000}{25.000.000} \times 100\% = 32\%$
        *   Tỷ lệ Trả nợ: $\frac{5.000.000}{25.000.000} \times 100\% = 20\%$
        *   Tỷ lệ Tiết kiệm: $\frac{5.000.000}{25.000.000} \times 100\% = 20\%$
        *   Tỷ lệ Chi tiêu linh hoạt: $\frac{7.000.000}{25.000.000} \times 100\% = 28\%$
    *   Kiểm tra tổng tỷ lệ: $32\% + 20\% + 20\% + 28\% = 100\%$. (Đảm bảo chính xác tuyệt đối).

---

### Phần 2: Bảng phân bổ ngân sách cuối cùng

| Hạng mục | Số tiền (VNĐ) | Tỷ lệ % | Ghi chú |
| :--- | :---: | :---: | :--- |
| **1. Chi phí cố định bắt buộc** | 8.000.000 | 32% | Nhà cửa, điện, nước, internet, bảo hiểm |
| **2. Trả nợ gốc & lãi** | 5.000.000 | 20% | Thanh toán đúng hạn các khoản vay |
| **3. Quỹ tiết kiệm & đầu tư** | 5.000.000 | 20% | Đạt tỷ lệ cam kết tối thiểu |
| **4. Chi tiêu linh hoạt** | 7.000.000 | 28% | Ăn uống, giải trí, cá nhân, phát sinh |
| **TỔNG CỘNG** | **25.000.000** | **100%** | **Cân đối hoàn toàn dòng tiền** |

---

## PHẦN III: RÀNG BUỘC KỸ THUẬT VÀ LƯU Ý VẬN HÀNH

1. **Kiểm soát sai số học:** Bắt buộc AI phải liệt kê từng phép tính trung gian ở Phần 1 trước khi vẽ bảng ở Phần 2 nhằm ngăn chặn triệt để hiện tượng suy luận nhảy cóc (hallucination/calculation drift).
2. **Kiểm tra tính toàn vẹn của dữ liệu:** Tổng tiền các hạng mục phải khớp hoàn toàn với tổng thu nhập ban đầu ($8.000.000 + 5.000.000 + 5.000.000 + 7.000.000 = 25.000.000$ VNĐ).
3. **Tính cộng dồn tỷ lệ phần trăm:** Tổng tỷ trọng các cột % phải đạt chính xác tuyệt đối **100%** không dư thừa hoặc thiếu hụt do làm tròn số lẻ.