# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

> **Bối cảnh:** Tôi là AI Engineer tại **Vin Smart Future (Vingroup)**. Tôi được giao phối hợp với Khối Vận Hành **Vinhomes** để tìm kiếm cơ hội tối ưu bằng AI. Vinhomes hiện quản lý **32 khu đô thị**, **~168.000 căn hộ/biệt thự/nhà phố**, phục vụ **~650.000 cư dân** (2025).

Dùng **4 Lenses** quét qua hoạt động vận hành của Vinhomes.

### List bài toán:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Vinhomes** | Lặp lại (Repetitive) | Xử lý yêu cầu bảo trì & sửa chữa: Nhân viên BQL tiếp nhận ~25.000–40.000 ticket/tháng, mỗi ticket tốn ~45 phút qua 5 bước giao tiếp thủ công (ghi nhận → liên hệ vendor → xin phê duyệt → lên lịch → follow-up). 15–25% ticket bị trễ hoặc miss follow-up. |
| 2 | **Vinhomes** | Tốn thời gian (Time-consuming) | Thu phí dịch vụ & quản lý công nợ: 8–15% hộ dân (~13.000–25.000 hộ/tháng) nợ quá hạn. ~150–250 FTE dành toàn thời gian cho việc gọi điện nhắc nợ, gửi thông báo giấy, đối soát công nợ đa kênh (ngân hàng, ví điện tử, tiền mặt). Thất thoát ~100–420 tỷ VNĐ/năm. |
| 3 | **Vinhomes** | Pain từ người khác (Stakeholder Pain) | Chăm sóc cư dân & xử lý khiếu nại: 80.000–150.000 lượt liên hệ/tháng, 50–65% là câu hỏi lặp lại (FAQ). Thời gian phản hồi trung bình 24–72 giờ cho yêu cầu không khẩn cấp. 20–35% cư dân không hài lòng vì phản hồi chậm, ảnh hưởng giá trị thương hiệu. |
| 4 | **Vinhomes** | Tốn thời gian (Time-consuming) | Giám sát an ninh & xử lý sự cố: ~3.000–5.000 nhân sự bảo vệ giám sát hàng chục nghìn camera bằng mắt. Tỷ lệ phát hiện sự cố nhỏ chỉ 20–40% (human attention span giảm mạnh sau 20 phút). Thời gian phản ứng trung bình 8–15 phút. |
| 5 | **Vinhomes** | AI có thể tốt hơn (AI-upgrade) | Quản lý năng lượng & hạ tầng kỹ thuật: 15–30% năng lượng khu vực chung bị lãng phí (~30–120 tỷ VNĐ/năm). Bảo trì thiết bị (thang máy, PCCC, HVAC) theo lịch cố định hoặc reactive, không tối ưu theo tình trạng thực tế. Chi phí sửa chữa khẩn cấp gấp 3–5x bảo trì dự phòng. |

---

# Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#1 (Bảo trì & Sửa chữa), #3 (CSKH & Khiếu nại), #2 (Thu phí & Công nợ).**

## Card #1 — Vinhomes: Xử lý yêu cầu bảo trì & sửa chữa tự động

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Nhân viên BQL Vinhomes xử lý hàng chục nghìn     │
│ ticket bảo trì/tháng hoàn toàn thủ công: tiếp nhận, phân   │
│ loại, liên hệ vendor, lên lịch, theo dõi tiến độ.          │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? Nhân viên BQL (quá tải ticket),               │
│              Cư dân (chờ đợi sửa chữa quá lâu),            │
│              Vendor (nhận thông tin thiếu/sai)               │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Cư dân gọi hotline/gửi app báo sự cố                  │
│   → 2. NV BQL tiếp nhận, ghi log, phân loại thủ công       │
│   → 3. Tra cứu vendor phù hợp, liên hệ báo giá            │
│   → 4. Xin phê duyệt chi phí, lên lịch sửa chữa           │
│   → 5. Theo dõi tiến độ, xác nhận hoàn thành, đóng ticket  │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 25-30 phút/lượt)            │
│   Phân loại mức độ ưu tiên sai → sửa chữa muộn → hư hại   │
│   lan rộng → chi phí tăng thêm 30-50%                      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3             │
│   NLP tự động phân loại ưu tiên + Smart Routing match       │
│   ticket → vendor phù hợp nhất (skill, khoảng cách, rating)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│   Giảm thời gian xử lý từ 45 phút ──> dưới 15 phút/ticket  │
│   Giảm tỷ lệ ticket bị trễ từ 20% ──> dưới 5%              │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
│   (NLP phân loại + Smart Routing, không cần Agent tự trị    │
│   vì quy trình có cấu trúc cố định)                        │
└─────────────────────────────────────────────────────────────┘
```

---

## Card #2 — Vinhomes: AI Chatbot chăm sóc cư dân đa ngữ 24/7

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Bộ phận CSKH Vinhomes xử lý 80K-150K lượt liên  │
│ hệ/tháng, trong đó 50-65% là câu hỏi lặp lại (FAQ) như    │
│ giờ tiện ích, cách đóng phí, quy trình đăng ký sửa chữa.  │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? NV CSKH (400-700 FTE, quá tải),               │
│              Cư dân (chờ phản hồi 24-72 giờ),              │
│              BQL (chi phí CSKH 38-84 tỷ VNĐ/năm)            │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân gọi hotline / nhắn app / đến lễ tân            │
│   → 2. NV CSKH tiếp nhận, tra cứu thông tin nội bộ         │
│   → 3. Soạn phản hồi thủ công (hoặc copy-paste mẫu cũ)    │
│   → 4. Gửi phản hồi, log kết quả, chuyển tiếp nếu phức tạp│
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 8-12 phút/lượt cho FAQ)     │
│   NV phải tra cứu cùng một thông tin lặp lại hàng trăm     │
│   lần/ngày, dễ nhầm lẫn khi mệt mỏi                       │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1-3             │
│   Chatbot/Voicebot tự động trả lời 50-65% FAQ, 24/7,       │
│   hỗ trợ tiếng Việt + Anh + Hàn/Nhật (cư dân quốc tế)     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│   Giảm thời gian phản hồi FAQ từ 24-72 giờ ──> dưới 5 phút │
│   Giảm 50-60% FTE CSKH, tăng NPS +15-25 điểm               │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
│   (RAG chatbot trên knowledge base nội bộ Vinhomes,         │
│   Smart Escalation khi vượt FAQ)                            │
└─────────────────────────────────────────────────────────────┘
```

---

## Card #3 — Vinhomes: Hệ thống thu phí & nhắc nợ thông minh

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: 8-15% hộ dân Vinhomes (~13K-25K hộ/tháng) nợ quá│
│ hạn phí dịch vụ. NV BQL phải gọi điện nhắc nợ, gửi thông  │
│ báo giấy, đối soát công nợ đa kênh hoàn toàn thủ công.     │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? NV tài chính BQL (150-250 FTE nhắc nợ),       │
│              Ban Giám đốc (thất thoát 100-420 tỷ VNĐ/năm), │
│              Cư dân thiện chí (phiền vì nhận thông báo muộn)│
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Kế toán xuất danh sách nợ quá hạn từ hệ thống         │
│   → 2. Phân loại thủ công theo mức nợ, thời gian nợ        │
│   → 3. Gọi điện/gửi thông báo giấy nhắc từng hộ           │
│   → 4. Đối soát thanh toán đa kênh (NH, ví, tiền mặt)      │
│   → 5. Cập nhật trạng thái, báo cáo tổng hợp công nợ      │
│                                                             │
│ Bước nào tốn nhất? Bước 3-4 (⏱ 15-20 phút/hộ)              │
│   Gọi điện nhắc nợ sai thời điểm → cư dân không nghe máy   │
│   Đối soát đa kênh thủ công → sai sót, trùng lặp           │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4             │
│   Phân nhóm hành vi thanh toán + gửi nhắc nhở cá nhân hóa  │
│   tự động + đối soát đa kênh tự động                        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│   Giảm tỷ lệ nợ quá hạn từ 12% ──> dưới 5%                 │
│   Giảm 40-60% FTE nhắc nợ, tăng tỷ lệ thu hồi +30%         │
│                                                             │
│ Quick Architecture: [x] Agent                                │
│   (AI Dunning Agent: phân tích hành vi → chọn kênh →        │
│   gửi nhắc nhở → đối soát → cập nhật tự động, cần          │
│   orchestration loop vì workflow phức tạp, đa kênh)         │
└─────────────────────────────────────────────────────────────┘
```

---

# 🗳️ Quyết định lựa chọn bài toán Deep-Dive:

Tôi đề xuất nhóm chọn bài toán **Card #2 — AI Chatbot Chăm Sóc Cư Dân Đa Ngữ 24/7** để thực hiện Deep-Dive.

## Lý do lựa chọn và loại bỏ các thẻ khác:

* **Card #2 (CSKH Chatbot) — ĐỀ XUẤT CHỌN:** Quick win rõ ràng nhất — 50-65% FAQ có thể tự động hóa ngay, ROI nhanh (4-8x Year 1), rủi ro thấp vì chatbot chỉ trả lời thông tin có sẵn, dễ đo lường bằng NPS và thời gian phản hồi, pilot tại 1 KĐT trước khi scale. Không ảnh hưởng tài chính trực tiếp nếu AI trả lời sai (chỉ là thông tin hướng dẫn, không phải giao dịch tiền).
* **Card #1 (Bảo trì):** Impact lớn nhưng cần tích hợp sâu với hệ thống vendor management, IoT sensor. Phù hợp Phase 2 sau khi có AI infrastructure cơ bản.
* **Card #3 (Thu phí):** Tổn thất tài chính lớn nhất (~100-420 tỷ/năm) nhưng rủi ro cao — nhắc nợ sai có thể gây phản cảm, cần dữ liệu hành vi thanh toán lịch sử ít nhất 12 tháng để train model, liên quan pháp lý về thông tin tài chính cá nhân.
