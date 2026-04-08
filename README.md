# 📘 Hướng Dẫn Sử Dụng — Manual Testing RBT Kit

> Framework sinh Manual Test Cases chất lượng cao theo quy trình **AI-RBT (AI-Driven Risk-Based Testing)** 6 bước.
> Được thiết kế để dùng trực tiếp với **Antigravity AI** trong editor.

---

## 📁 Cấu Trúc Thư Mục

```text
ManualTestingRbtKit/
│
├── README.md                            ← File hướng dẫn chi tiết bạn đang đọc
│
├── plans/                               ← Prompt templates cho từng bước
│   ├── QUICK_START.md                   ← Hướng dẫn khởi động nhanh
│   ├── 01_context_and_roleplay/
│   │   ├── README.md
│   │   └── prompt.txt                  
│   ├── 02_analysis_and_qna/
│   │   └── prompt.txt                   
│   ├── 03_decomposition/
│   │   └── prompt.txt
│   ├── 04_traceability/
│   │   └── prompt.txt
│   ├── 05_rbt_and_tc_generation/
│   │   └── prompt.txt
│   └── 06_template_mapping/
│       └── prompt.txt
│
└── .agent/                              ← Thư mục thiết lập cho Antigravity AI
    ├── skills/                          ← AI Skills (tự động kích hoạt)
    │   ├── rbt_manual_testing/          ← Skill chính: quy trình AI-RBT 6 bước
    │   └── requirements_analyzer/       ← Skill phụ: phân tích UI/website
    │
    └── workflows/                       ← Định nghĩa Slash Commands
        ├── generate_manual_testcases_rbt.md
        ├── generate_requirements_from_website.md
        └── generate_testcases_from_requirements.md
```

---

## 🚀 Bắt Đầu Nhanh

### ✅ Bước duy nhất cần làm: Gửi lệnh dưới đây cho Antigravity

```text
/generate_manual_testcases_rbt

Dự án: [Tên dự án của bạn]
Tính năng: [Tên tính năng cần test]
Mục tiêu: [Mô tả ngắn muốn kiểm thử gì]

[Dán toàn bộ Requirements / User Story / Mô tả BA vào đây]
```

**Antigravity sẽ khởi động Agent và tự động dẫn dắt bạn qua đủ 6 bước.** Bạn không cần phải nhớ hay làm gì thêm ngoài việc cung cấp input khi AI hỏi.

### 💡 Ví Dụ Thực Tế

```text
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

| Bước | Tên | Bạn Cần Làm | Antigravity AI Làm | Chốt Chặn Trạng Thái? |
|------|-----|------------|------------------|----------------------|
| **1** | Context & Role-play | Cung cấp yêu cầu | Thiết lập vai trò QA, tóm tắt scope | ✅ Bạn xác nhận phạm vi |
| **2** | Analysis & QnA | **Trả lời kỹ Q&A** | Phân tích điểm mơ hồ (ambiguity), hỏi bạn | ⏸️ **Bắt buộc AI đợi câu trả lời** |
| **3** | Decomposition | Xem nhanh | Phân rã hệ thống thành Modules/Sub-modules | Review nhanh |
| **4** | Traceability | **Bổ sung Scenario** | Map Module sang Scenario bậc cao | ⏸️ **Bắt buộc AI đợi đánh giá Risk** |
| **5** | RBT & TC Generation | Xem Test Cases | Sinh Test Cases chi tiết theo Risk Level | Review |
| **6** | Template Mapping | Lấy thành quả | Xuất bảng chuẩn | ✅ Hoàn thành! |

---

## 📋 Các Lệnh Tiện Ích (Slash Commands)

| Command | Mục Đích Sử Dụng |
|---------|-----------------|
| `/generate_manual_testcases_rbt` | **Lệnh chính thống** — Đã có specs, muốn sinh Manual Test Cases chuẩn 6 bước |
| `/generate_requirements_from_website` | **Biến UI thành Specs** — Chưa có specs, cần AI soi code UI sinh ra requirements trước |
| `/generate_testcases_from_requirements` | **Fast-Track** — Đã có specs quá chuẩn, chỉ muốn sinh luôn Test Cases bỏ qua hỏi đáp |

---

## ⚠️ Nguyên Tắc Bắt Buộc

| ❌ KHÔNG LÀM | ✅ NÊN LÀM |
|-------------|-----------|
| Gộp lệnh chạy 6 bước vào 1 tin nhắn | **BẮT BUỘC** Chạy tuần tự từng bước theo dẫn dắt của AI |
| Lướt qua Bước 2 Q&A | Trả lời đầy đủ, chi tiết từng câu hỏi để xóa điểm mù yêu cầu |
| Mở một đoạn Hội thoại (Conversation) mới | Dùng chung một Conversation duy nhất để AI duy trì context |
| Bỏ qua duyệt mảng Rủi ro (Risk) Bước 4 | Kiểm duyệt cẩn thận, thêm bớt Scenario trước khi AI viết TC chi tiết |
| Dùng Test Data kiểu placeholder chung chung | Đòi hỏi AI sinh Test Data thực tế (VD: `test@domain.com` thay vì `email hợp lệ`) |

---

## 💡 Mẹo Hay Dành Cho Bạn

1. **Bước 2 là Trái Tim Của Quy Trình** 
   Đừng vội vàng skip. AI với góc nhìn QA sành sỏi sẽ tìm ra những điểm chết trong requirement mà đôi khi BA vô tình bỏ sót. Trả lời càng tường minh, Test Cases sinh ra càng sắc lẹm.
   
2. **Quy Tắc "Chia Để Trị" Cho Feature Lớn**
   Khi đi đến Bước 5, nếu danh sách module cần test lớn hơn 5, hãy yêu cầu AI generate từng cụm một:
   > _"Hãy sinh Test Cases chi tiết cho module [Tên module A]. Dừng lại sau khi xong để tôi duyệt trước khi qua module tiếp theo."_

3. **Từ Không Thành Có?** 
   Bạn đưa cho tôi 1 trang web không hề có tài liệu? Hãy chạy `/generate_requirements_from_website` trước. AI sẽ đi soi code và UI để viết requirement cho bạn. Sau đó kết hợp requirement vừa nhận được chạy vào luồng 6 bước này.
   
4. **Copy Output Siêu Dễ Dàng** 
   Kết quả của Bước 6 là một bảng Markdown định dạng chuẩn (ID, Module, Traceability, Steps, Code Test Data). Bạn chỉ cần copy bôi đen đoạn Markdown đó và dán thẳng vào Jira Excel / Google Sheets là bảng sẽ tự căn đúng cột.

---

## 📞 Thử Ngay Nào!

Gửi tin nhắn dưới cho tôi luôn nhé:

```text
/generate_manual_testcases_rbt

Dự án: [Dự án của bạn]
Tính năng: [Tính năng]
Mục tiêu: [Mục tiêu test]

[Dán yêu cầu vào đây]
```
