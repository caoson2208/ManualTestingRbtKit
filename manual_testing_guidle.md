# 📘 Hướng Dẫn Sử Dụng — Manual Testing RBT Kit

> Framework sinh Manual Test Cases chất lượng cao theo quy trình **AI-RBT (AI-Driven Risk-Based Testing)** 6 bước.
> Được thiết kế để dùng trực tiếp với **Antigravity AI** trong editor.

---

## 📁 Cấu Trúc Thư Mục

```
manual-testing-rbt-kit/
│
├── manual_testing_guidle.md                        ← File bạn đang đọc
├── README.md                            ← Tổng quan ngắn về framework
│
├── plans/                               ← Prompt templates cho từng bước
│   ├── QUICK_START.md                   ← Hướng dẫn khởi động nhanh
│   ├── 01_context_and_roleplay/
│   │   ├── README.md
│   │   └── prompt.txt                   ← ✏️ Copy & paste vào chat (Bước 1)
│   ├── 02_analysis_and_qna/
│   │   └── prompt.txt                   ← ✏️ Copy & paste vào chat (Bước 2)
│   ├── 03_decomposition/
│   │   └── prompt.txt
│   ├── 04_traceability/
│   │   └── prompt.txt
│   ├── 05_rbt_and_tc_generation/
│   │   └── prompt.txt
│   └── 06_template_mapping/
│       └── prompt.txt
│
├── skills/                              ← AI Skills (tự động kích hoạt)
│   ├── rbt_manual_testing/              ← Skill chính: quy trình AI-RBT
│   └── requirements_analyzer/          ← Skill phụ: phân tích UI/website
│
└── workflows/                           ← Định nghĩa Slash Commands
    ├── generate_manual_testcases_rbt.md
    ├── generate_requirements_from_website.md
    └── generate_testcases_from_requirements.md
```

---

## 🚀 Khi Bạn Có Một Tính Năng Cần Test

### ✅ Bước duy nhất cần làm: Gửi 1 tin nhắn dưới đây cho Antigravity

```
/generate_manual_testcases_rbt

Dự án: [Tên dự án của bạn]
Tính năng: [Tên tính năng cần test]
Mục tiêu: [Mô tả ngắn muốn kiểm thử gì]

[Dán toàn bộ Requirements / User Story / Mô tả BA vào đây]
```

**Antigravity sẽ tự động dẫn dắt bạn qua đủ 6 bước.** Bạn không cần phải nhớ hay làm gì thêm ngoài việc trả lời câu hỏi của AI.

---

### 💡 Ví Dụ Thực Tế

```
/generate_manual_testcases_rbt

Dự án: App Bán Hàng Online
Tính năng: Thanh toán (Checkout)
Mục tiêu: Test toàn bộ luồng thanh toán từ khi bấm "Đặt hàng" đến xác nhận đơn thành công

Yêu cầu:
1. Hỗ trợ 2 phương thức: COD và Thẻ tín dụng (Visa/Mastercard)
2. Nếu chọn COD → chuyển thẳng trang xác nhận, không cần nhập thẻ
3. Nếu chọn Thẻ → bắt buộc điền: Số thẻ, Tên, Ngày hết hạn, CVV
4. Nút "Thanh toán" chỉ sáng khi điền đủ thông tin hợp lệ
5. Thanh toán thẻ thất bại → hiện lỗi "Giao dịch bị từ chối" màu đỏ
```

---

## 🔄 Quy Trình AI-RBT 6 Bước

Sau khi gửi tin nhắn Bước 1, Antigravity sẽ **tự động dẫn dắt** theo luồng sau:

```
┌─────────────────────────────────────────────────────────────────┐
│  BƯỚC 1: Context & Role-play                                    │
│  → Bạn: Gửi requirements                                       │
│  → AI: Tóm tắt lại scope kiểm thử                              │
│  → Bạn: Xác nhận OK                                            │
└────────────────────────┬────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│  BƯỚC 2: Analysis & Q&A  ⚠️ QUAN TRỌNG NHẤT                    │
│  → AI: Phân tích requirements, tìm điểm mờ (Ambiguity)         │
│  → AI: Đặt danh sách câu hỏi đánh số 1, 2, 3...               │
│  → Bạn: ⏸️ DỪNG LẠI — Trả lời kỹ từng câu hỏi               │
└────────────────────────┬────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│  BƯỚC 3: Decomposition                                          │
│  → AI: Chia tính năng thành Modules / Sub-modules              │
│  → Bạn: Review nhanh, xác nhận đúng                            │
└────────────────────────┬────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│  BƯỚC 4: Traceability  ⚠️ HUMAN CHECKPOINT                      │
│  → AI: Map từng Module → REQ code                              │
│  → AI: Sinh danh sách High-Level Scenarios                      │
│  → Bạn: ⏸️ DỪNG LẠI — Review, bổ sung scenario còn thiếu     │
└────────────────────────┬────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│  BƯỚC 5: RBT & TC Generation                                    │
│  → AI: Đánh giá Risk Level (High/Medium/Low) từng Module       │
│  → AI: Sinh Test Cases chi tiết: Title, Steps, Expected...     │
│  → Bạn: Review test cases                                       │
└────────────────────────┬────────────────────────────────────────┘
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│  BƯỚC 6: Template Mapping  ✅ DONE                              │
│  → AI: Xuất bảng Markdown chuẩn                                 │
│  → Bạn: Copy bảng → Paste vào Excel / Jira / TestRail          │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📊 Tóm Tắt Bảng 6 Bước

| Bước | Tên | Bạn cần làm | AI làm | Chờ gì? |
|------|-----|------------|--------|---------|
| **1** | Context & Role-play | Cung cấp requirements | Đọc, tóm tắt scope | ✅ Xác nhận OK |
| **2** | Analysis & Q&A | **Trả lời kỹ Q&A** | Phân tích ambiguity, đặt câu hỏi | ⏸️ **Bắt buộc dừng** |
| **3** | Decomposition | Review module list | Chia Modules/Sub-modules | Review nhanh |
| **4** | Traceability | **Review scenarios** | Map Module → REQ, sinh scenarios | ⏸️ **Bắt buộc dừng** |
| **5** | RBT & TC Generation | Review test cases | Sinh TCs đầy đủ theo Risk | Review |
| **6** | Template Mapping | Copy bảng vào tool | Xuất bảng Markdown chuẩn | ✅ Xong! |

---

## 📋 Slash Commands

| Command | Khi nào dùng |
|---------|-------------|
| `/generate_manual_testcases_rbt` | **Dùng chính** — Có requirements, muốn sinh Test Cases |
| `/generate_requirements_from_website` | **Chưa có requirements** — Muốn AI phân tích website/UI để lấy requirements trước |
| `/generate_testcases_from_requirements` | Đã có requirements chi tiết, muốn sinh TC nhanh (bỏ qua bước Q&A) |

---

## ⚠️ Nguyên Tắc Bắt Buộc

| ❌ KHÔNG làm | ✅ NÊN làm |
|-------------|-----------|
| Gộp nhiều bước vào 1 tin nhắn | Chạy tuần tự từng bước |
| Bỏ qua Bước 2 Q&A | Trả lời đầy đủ từng câu hỏi của AI |
| Mở conversation mới giữa chừng | Dùng chung 1 conversation cho cả 6 bước |
| Bỏ qua Bước 4 review | Review và bổ sung scenarios trước khi sinh TC |
| Sang Bước 6 mà chưa review TC | Review TC ở Bước 5 trước khi format |

---

## 💡 Mẹo Hay

1. **Bước 2 là quan trọng nhất** — Đừng vội vàng. AI sẽ phát hiện những điểm mơ hồ trong requirements mà bạn chưa để ý. Trả lời càng kỹ, test cases càng chính xác.

2. **Feature lớn? Chia nhỏ** — Ở Bước 5, nếu có >5 modules, yêu cầu AI sinh từng module một:
   ```
   Sinh TC cho module: [Tên module]. Xong rồi dừng lại cho tôi review.
   ```

3. **Chưa có Requirements?** — Dùng command `/generate_requirements_from_website` trước, AI sẽ tự vào website phân tích và sinh requirements cho bạn. Sau đó mới bắt đầu 6 bước.

4. **Output chuẩn của Bước 6:**
   ```
   | TC ID | Module | Risk | Test Title | Pre-Condition | Steps | Expected | Priority | Test Data |
   ```
   Bảng này copy thẳng vào Google Sheets/Excel là dùng được ngay.

---

## 📞 Bắt Đầu Ngay

Khi bạn sẵn sàng, chỉ cần gửi tin nhắn này cho Antigravity:

```
/generate_manual_testcases_rbt

Dự án: ...
Tính năng: ...
Mục tiêu: ...

[Requirements của bạn]
```

**Antigravity sẽ làm phần còn lại.** 🎯
