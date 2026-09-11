# 🏗️ Phase 3 — DEEP-DIVE Report

> ⚠️ **LƯU Ý:** Phase 3 — DEEP-DIVE là phase **NHÓM (Nhóm, 85 min)**, KHÔNG phải phase cá nhân.
>
> Theo yêu cầu của bạn, tôi chỉ hoàn thành các phase có role **Individual (Cá nhân)**.
> Phase 3 bao gồm:
> - 3.1. Current-State Workflow Mapping (25 min) — **Nhóm**
> - 3.2. Problem Statement (6-field) & Metrics (15 min) — **Nhóm**
> - 3.3. Future-State Flow & AI Fit (25 min) — **Nhóm**
>
> Bạn cần thảo luận và hoàn thiện phase này cùng nhóm.

---

> Tuy nhiên, dựa trên bài toán **Card #2 — AI Chatbot Chăm Sóc Cư Dân Đa Ngữ 24/7** mà tôi đề xuất ở Phase 2, tôi chuẩn bị sẵn một **bản nháp (draft)** để nhóm có thể tham khảo và chỉnh sửa:

---

## 3.1. Current-State Workflow Mapping

Quy trình xử lý yêu cầu CSKH hiện tại tại Vinhomes:

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Tiếp nhận    │     │ Tra cứu      │     │ Soạn phản    │     │ Gửi phản hồi │
│ yêu cầu     │     │ thông tin    │     │ hồi thủ công │     │ & log kết quả│
│ từ cư dân   │ ──→ │ nội bộ       │ ──→ │              │ ──→ │              │
│              │     │              │     │              │     │              │
│ Ai: NV CSKH │     │ Ai: NV CSKH │     │ Ai: NV CSKH │     │ Ai: NV CSKH │
│ ⏱ 2 phút     │     │ ⏱ 4 phút 🔴  │     │ ⏱ 5 phút 🔴  │     │ ⏱ 1 phút     │
│ Kênh: Phone, │     │ In: Câu hỏi  │     │ In: Data nội │     │ In: Bản phản │
│ App, Lễ tân  │     │ cư dân       │     │ bộ           │     │ hồi soạn sẵn │
│ Out: Log yêu │     │ Out: Thông   │     │ Out: Nội dung│     │ Out: Phản hồi│
│ cầu         │     │ tin tra cứu  │     │ phản hồi     │     │ + closed log │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Leo thang    │
                                                               │ (nếu phức    │
                                                               │ tạp/khiếu nại│
                                                               │ Ai: NV CSKH │
                                                               │ → Trưởng BQL │
                                                               │ ⏱ 24-72 giờ 🔴│
                                                               └──────────────┘
🔴 = Bottlenecks
🔄 Handoff: Bước 4 → Bước 5 (chuyển giao giữa NV CSKH → Trưởng BQL, dễ thất lạc thông tin)
⏱ Tổng thời gian xử lý FAQ: ~12 phút/lượt
⏱ Tổng thời gian xử lý khiếu nại phức tạp: 24-72 giờ/lượt
```

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Nhân viên CSKH (Call center + Lễ tân) thuộc Ban Quản Lý các khu đô thị Vinhomes. Ước tính 400–700 FTE toàn hệ thống 32 KĐT. |
| **2. Current Workflow** | Khi cư dân liên hệ qua hotline, app Vinhomes Resident, email, hoặc trực tiếp lễ tân, NV CSKH tiếp nhận yêu cầu, tra cứu thông tin nội bộ (quy định, lịch bảo trì, phí dịch vụ, tiện ích), soạn phản hồi thủ công, gửi cư dân, và log kết quả. Nếu khiếu nại phức tạp thì leo thang Trưởng BQL. 5 bước, chủ yếu thủ công, FAQ mất ~12 phút/lượt, khiếu nại mất 24-72 giờ. |
| **3. Bottleneck** | Bước 2 & 3 (mất 9 phút): Tra cứu cùng một thông tin FAQ hàng trăm lần/ngày + soạn phản hồi thủ công. 50-65% câu hỏi là FAQ lặp lại (giờ mở cửa tiện ích, cách đóng phí, quy trình đăng ký sửa chữa). NV mệt mỏi → phản hồi rập khuôn, chất lượng giảm theo thời gian trong ngày. |
| **4. Business Impact** | 80.000–150.000 lượt liên hệ/tháng toàn hệ thống. Chi phí nhân sự CSKH: ~38–84 tỷ VNĐ/năm. 20-35% cư dân không hài lòng vì phản hồi chậm → giảm ~3-5% tỷ lệ referral → ảnh hưởng doanh số bán hàng dự án mới. Vinhomes đang mở rộng nhanh (~157.000 cư dân mới/năm 2025) → quy mô CSKH phải tăng tương ứng nếu không có AI. |
| **5. Success Metric** | 1. Giảm thời gian phản hồi FAQ từ 24-72 giờ xuống dưới 5 phút (Responsiveness).<br>2. Tỷ lệ FAQ tự động xử lý thành công đạt 80%+ (Automation Rate).<br>3. Tăng NPS cư dân +15-25 điểm (Satisfaction).<br>4. Giảm 50-60% FTE CSKH hoặc redirect FTE sang xử lý khiếu nại phức tạp (Efficiency). |
| **6. Operational Boundary** | AI được phép truy cập knowledge base nội bộ Vinhomes (quy định, lịch tiện ích, hướng dẫn đóng phí, FAQ), tự động trả lời câu hỏi FAQ dạng thông tin. **CẤM:** AI không được trả lời các vấn đề liên quan tài chính cá nhân (số dư nợ, phí cụ thể từng hộ), pháp lý (tranh chấp, khiếu nại chất lượng xây dựng), hoặc an ninh (report sự cố nghiêm trọng). Các trường hợp này PHẢI leo thang sang NV CSKH con người (HITL). AI PHẢI gắn disclaimer: "Thông tin tham khảo, vui lòng liên hệ BQL để xác nhận chi tiết." |

---

## 3.3. Future-State Flow & AI Fit

* **AI Fit:** Chọn **LLM Feature** (RAG Chatbot). Không cần Agentic Loop vì:
  - FAQ có knowledge base cố định, không cần tool-calling phức tạp
  - Rủi ro khi chatbot tự ý hành động (gửi thông tin sai về phí, pháp lý) cao hơn lợi ích tự động hóa toàn bộ
  - LLM + RAG đủ giải quyết 80%+ use case với chi phí triển khai thấp

* **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Cư dân gửi   │     │ 🔵 AI phân   │     │ 🔵 AI RAG    │     │ 🟢 NV CSKH  │
│ yêu cầu qua  │ ──→ │ loại: FAQ    │ ──→ │ trả lời tự   │ ──→ │ xử lý       │
│ App/Hotline  │     │ hay Khiếu nại│     │ động từ KB   │     │ khiếu nại   │
│              │     │              │     │ (nếu FAQ)    │     │ (nếu phức   │
│              │     │ Confidence   │     │              │     │ tạp / HITL)  │
│              │     │ Score ≥ 0.85 │     │ + disclaimer │     │              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                            │                                         │
                            │ (Confidence < 0.85)                     │
                            ▼                                         ▼
                     ↩️ Fallback 1:                            ↩️ Fallback 2:
                     Chuyển thẳng sang                         Nếu NV CSKH quá tải,
                     NV CSKH con người.                        AI soạn draft phản hồi
                     Gửi kèm context                          để NV review & gửi
                     đã thu thập.                              (giảm thời gian soạn).
```

### So sánh Rule vs LLM vs Agent:

| Tiêu chí | Rule-Based | LLM (RAG) ✅ | Agentic Loop |
|---|---|---|---|
| Xử lý FAQ đa dạng ngôn ngữ tự nhiên | ❌ Cứng nhắc, cần keyword exact match | ✅ Hiểu intent, synonym, đa ngữ (Vi/En/Kr/Jp) | ✅ Nhưng overkill |
| Chi phí triển khai | 💰 Thấp | 💰💰 Trung bình | 💰💰💰 Cao |
| Rủi ro hallucination | ❌ Không có | ⚠️ Có, nhưng RAG + disclaimer giảm thiểu | ⚠️ Cao hơn vì loop phức tạp |
| Khả năng scale theo cư dân mới | ❌ Cần viết thêm rule | ✅ Chỉ cần update KB | ✅ |
| Phù hợp use case CSKH Vinhomes | ❌ | ✅ Best fit | ❌ Over-engineering |
