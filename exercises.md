# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)
Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing
Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Tăng temperature từ 0.0 lên 1.5 khiến phản hồi chuyển từ dễ đoán, lặp ý (ở mức 0.0 - 0.5) sang phong phú, tự nhiên (mức 1.0), và cuối cùng bị vỡ cấu trúc câu, nói nhảm (mức 1.5).

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Chọn **0.0** (hoặc tối đa **0.1**). Khách hàng cần thông tin chuẩn xác và nhất quán, nhiệt độ thấp giúp triệt tiêu hoàn toàn sự ngẫu hứng và hallucination.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Gấp **16,67 lần** (105 USD/ngày so với 6,3 USD/ngày trên tổng 10,5 triệu token output).

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> - **GPT-4o đáng tiền**: Các bài toán suy luận logic sâu, gỡ lỗi code phức tạp, hoặc phân tích đa phương thức (hình ảnh/bảng biểu).
> - **GPT-4o-mini tốt hơn**: Các tác vụ đơn giản, lặp đi lặp lại như phân loại ý định (intent classifier) hoặc trích xuất thông tin thô (name/email extraction).

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> **Streaming** tối quan trọng đối với giao diện tương tác người dùng trực tiếp (như chatbot) giúp giảm thời gian chờ đợi cảm nhận. Ngược lại, **non-streaming** phù hợp hơn cho các tác vụ nền, xử lý hàng loạt hoặc khi cần trả về cấu trúc dữ liệu hoàn chỉnh (như JSON) cho hệ thống khác tiêu thụ trực tiếp.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
