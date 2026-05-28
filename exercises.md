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
> Temperature càng thấp (0.0-0.5), phản hồi càng nhất quán, dễ đoán và thường lặp lại cùng một sự thật. Temperature càng cao (1.0-1.5), phản hồi càng sáng tạo, ngẫu nhiên và có thể thiếu chính xác. Ở mức 1.5, câu trả lời bắt đầu có dấu hiệu lạc đề hoặc không mạch lạc.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Temperature khoảng 0.2-0.3. Lý do: chatbot hỗ trợ khách hàng cần câu trả lời chính xác, nhất quán và đáng tin cậy. Temperature thấp giúp giảm thiểu rủi ro "ảo giác" (hallucination) và đảm bảo khách hàng nhận được thông tin giống nhau cho cùng một câu hỏi.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> GPT-4o đắt hơn GPT-4o-mini khoảng **33.3 lần**.
> Cụ thể: (10,000 × 3) × ~350 token = 10.5M token/ngày. Với GPT-4o: (10.5M × $12.5/million blended rate) = ~$131/ngày. Với GPT-4o-mini: (10.5M × $0.375/million) = ~$3.94/ngày.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> **Dùng GPT-4o:** Phân tích hợp đồng pháp lý hoặc chẩn đoán y tế, nơi độ chính xác và lý luận sâu là quan trọng hơn chi phí. Một lỗi nhỏ có thể gây hậu quả lớn. **Dùng GPT-4o-mini:** Chatbot hỗ trợ khách hàng, tóm tắt email, hoặc phân loại ticket — những tác vụ đơn giản, tần suất cao, cần chi phí thấp và tốc độ nhanh.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng thời gian thực như chatbot hội thoại, nơi người dùng cần phản hồi ngay lập tức để có trải nghiệm mượt mà (giống như đang trò chuyện với người thật). Non-streaming phù hợp hơn khi cần xử lý toàn bộ response trước khi hiển thị — ví dụ: kiểm tra nội dung trước khi gửi, phân tích batch dữ liệu, hoặc các tác vụ background không yêu cầu tương tác tức thời.


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
