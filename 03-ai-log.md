# 📝 Phase 6 — REFLECTION: AI Log (Cá nhân)

> **Ghi nhận phản ánh cá nhân về việc phối hợp với AI trong buổi lab.**

---

## 🤖 Tôi đã sử dụng AI như thế nào trong buổi Lab hôm nay?

### Công cụ AI sử dụng:
- **Google Gemini / LLM** — Brainstorm pain points, stress-test thẻ bài toán, tra cứu benchmark ngành.

---

## 1. AI giúp gì? (What AI did well)

| # | Tác vụ | AI hỗ trợ thế nào | Đánh giá |
|---|---|---|---|
| 1 | **Brainstorm pain points Vinhomes** | Prompt: *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng Vinhomes..."* → AI trả về 5 quy trình nghiệp vụ cụ thể kèm benchmark ngành quốc tế, giúp tôi có cái nhìn toàn cảnh thay vì mò mẫm từ đầu. | ⭐⭐⭐⭐⭐ Rất hữu ích |
| 2 | **Ước tính con số tổn thất** | AI kết hợp quy mô công khai Vinhomes (168K căn, 650K cư dân) với benchmark ngành BĐS quốc tế để ước tính range tổn thất cho từng pain point. Giúp tôi có số liệu để đưa vào Quick Card thay vì để trống. | ⭐⭐⭐⭐ Hữu ích, nhưng cần validate |
| 3 | **Gợi ý giải pháp AI cụ thể** | AI đề xuất các giải pháp kỹ thuật phù hợp (NLP Triage, Smart Routing, RAG Chatbot, Predictive Maintenance) kèm ROI kỳ vọng. Giúp tôi phân loại Rule vs LLM vs Agent nhanh hơn. | ⭐⭐⭐⭐ Tốt |
| 4 | **Phân tích workflow thủ công** | AI mô tả chi tiết từng bước trong quy trình vận hành (5 bước xử lý ticket bảo trì, 4 bước CSKH), giúp tôi vẽ Quick Card chính xác hơn. | ⭐⭐⭐⭐ Tốt |

---

## 2. AI sai gì? (Where AI was wrong or misleading)

| # | Vấn đề | Chi tiết |
|---|---|---|
| 1 | **Con số ước tính quá rộng** | Các range ước tính rất rộng (VD: tổn thất thu phí ~100–420 tỷ VNĐ/năm — range gấp 4 lần). Nếu lấy số thấp nhất thì pain point không đủ thuyết phục, lấy số cao nhất thì có vẻ phóng đại. AI không có access dữ liệu nội bộ Vinhomes nên chỉ dựa vào benchmark chung. |
| 2 | **Thiếu context đặc thù Vinhomes** | AI không biết Vinhomes đã triển khai Vinhomes Online và Hệ thống Thủ tục Tự động (launched 2024). Một số pain point có thể đã được giải quyết một phần mà AI không cập nhật. Tôi phải tự cross-check thông tin này. |
| 3 | **Xu hướng "over-sell" giải pháp AI** | AI có xu hướng đề xuất AI cho mọi vấn đề mà không đặt câu hỏi: "Liệu rule-based/code thông thường có giải quyết tốt hơn không?". Ví dụ: đối soát công nợ đa kênh có thể giải quyết bằng ETL pipeline + business rules mà không cần ML/LLM. |

---

## 3. Tôi đã sửa/bổ sung gì? (My corrections and additions)

| # | Điều chỉnh | Lý do |
|---|---|---|
| 1 | **Thu hẹp range ước tính** khi đưa vào Quick Card | Sử dụng midpoint của range thay vì lấy cả range rộng, ghi chú rõ "cần validate bằng dữ liệu nội bộ" |
| 2 | **Cross-check với thông tin công khai** | Tìm thêm thông tin về Vinhomes Online, app Vinhomes Resident, hệ thống camera AI đã triển khai để loại bỏ những pain point đã được giải quyết |
| 3 | **Điều chỉnh Quick Architecture** | Card #3 (Thu phí): AI đề xuất LLM nhưng tôi đổi thành Agent vì workflow phức tạp đa kênh cần orchestration. Card #1 (Bảo trì): giữ LLM vì quy trình tương đối cố định |
| 4 | **Bổ sung rủi ro pháp lý** | AI không đề cập rủi ro pháp lý khi xử lý thông tin tài chính cá nhân (phí dịch vụ, công nợ) — tôi bổ sung vào phần lý do loại bỏ Card #3 khỏi Deep-Dive |

---

## 4. Bài học rút ra (Key Takeaways)

1. **AI là thought-partner xuất sắc cho giai đoạn brainstorm**, đặc biệt khi cần quét nhanh nhiều domain. Nhưng output của AI chỉ là **điểm khởi đầu**, không phải kết luận cuối cùng.

2. **Luôn cross-check số liệu AI đưa ra** với dữ liệu nội bộ hoặc nguồn đáng tin cậy. AI hallucinate con số rất tự tin — nếu không kiểm tra, dễ đưa vào báo cáo số liệu sai.

3. **AI có bias thiên về đề xuất giải pháp AI** (hiển nhiên). Cần luôn tự hỏi: "Rule-based code có đủ tốt chưa?" trước khi deploy LLM/Agent.

4. **Prompt càng cụ thể → output càng hữu ích.** Prompt ban đầu ("gợi ý 5 quy trình...") cho kết quả tốt hơn nhiều so với prompt mơ hồ ("tìm pain point cho Vinhomes").

---

## 5. Nếu được làm lại, tôi sẽ...

- Chuẩn bị **dữ liệu nội bộ** (báo cáo vận hành, SLA, số liệu ticket thực tế) trước khi brainstorm với AI → AI sẽ cho output chính xác hơn khi có context cụ thể.
- Sử dụng **prompt phản biện** sớm hơn: *"Hãy đóng vai CFO khắt khe..."* ngay từ đầu thay vì chỉ dùng ở bước stress-test.
- Dành thêm thời gian **validate từng pain point** bằng cách phỏng vấn stakeholder thực tế (NV BQL, cư dân, kế toán) thay vì chỉ dựa vào AI + internet.
