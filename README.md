# 📋 MANUAL TESTING — AI-RBT FRAMEWORK

> Folder này tổng hợp **toàn bộ tài liệu, skill, workflow và prompt templates** phục vụ cho quy trình **Manual Testing** theo framework AI-RBT 6 bước.

---

## 📁 Cấu trúc Folder

```
manual-testing/
│
├── README.md                          ← File này — tổng quan
│
├── skills/
│   ├── rbt_manual_testing.md          ← Skill chính: quy trình AI-RBT 6 bước
│   └── requirements_analyzer.md      ← Skill phụ: phân tích requirements từ UI
│
├── workflows/
│   ├── generate_manual_testcases_rbt.md         ← Workflow chính (slash: /generate_manual_testcases_rbt)
│   ├── generate_requirements_from_website.md    ← Sinh requirements từ website
│   └── generate_testcases_from_requirements.md  ← Sinh TC từ requirements có sẵn
│
└── plans/
    ├── README.md          ← Giới thiệu framework AI-RBT
    ├── QUICK_START.md     ← Hướng dẫn sử dụng nhanh ⚡
    │
    ├── 01_context_and_roleplay/
    │   ├── README.md      ← Hướng dẫn Bước 1
    │   └── prompt.txt     ← ✏️ COPY & PASTE vào chat (Bước 1)
    │
    ├── 02_analysis_and_qna/
    │   ├── README.md      ← Hướng dẫn Bước 2
    │   └── prompt.txt     ← ✏️ COPY & PASTE vào chat (Bước 2)
    │
    ├── 03_decomposition/
    │   ├── README.md      ← Hướng dẫn Bước 3
    │   └── prompt.txt     ← ✏️ COPY & PASTE vào chat (Bước 3)
    │
    ├── 04_traceability/
    │   ├── README.md      ← Hướng dẫn Bước 4
    │   └── prompt.txt     ← ✏️ COPY & PASTE vào chat (Bước 4)
    │
    ├── 05_rbt_and_tc_generation/
    │   ├── README.md      ← Hướng dẫn Bước 5
    │   └── prompt.txt     ← ✏️ COPY & PASTE vào chat (Bước 5)
    │
    └── 06_template_mapping/
        ├── README.md      ← Hướng dẫn Bước 6
        └── prompt.txt     ← ✏️ COPY & PASTE vào chat (Bước 6)
```

---

## 🚀 Quy Trình AI-RBT — 6 Bước

| Bước | Tên | Mục đích | Chờ User? |
|------|-----|----------|-----------|
| **1** | Context & Role-play | Thiết lập vai trò Senior QA + nạp bối cảnh | ✅ Xác nhận |
| **2** | Analysis & QnA | Phân tích requirements, phát hiện Ambiguity, đặt Q&A | ✅ **Trả lời Q&A** |
| **3** | Decomposition | Phân rã hệ thống thành Modules/Sub-modules | Review nhanh |
| **4** | Traceability | Traceability Matrix + High-Level Scenarios | ✅ **Human Checkpoint** |
| **5** | RBT & TC Generation | Sinh Test Cases chi tiết theo Risk Level | Review |
| **6** | Template Mapping | Xuất bảng Markdown chuẩn → Excel/Jira/TestRail | Copy bảng |

---

## ⚡ Bắt đầu nhanh

**Bước 1** — Gửi vào chat Antigravity:
```
/generate_manual_testcases_rbt

Dự án: [Tên dự án]
Tính năng: [Tên tính năng]
Mục tiêu: [Mô tả ngắn]

[Dán requirements/user stories vào đây]
```

**Các bước tiếp theo** — Copy nội dung `prompt.txt` trong từng folder tương ứng và gửi vào chat.

> 💡 **Mẹo:** Chạy tất cả 6 bước trong **cùng 1 conversation** để AI giữ nguyên context.

---

## ⚠️ Nguyên tắc quan trọng

1. **BẮT BUỘC chạy tuần tự** — KHÔNG gộp nhiều bước vào 1 lần
2. **PHẢI dừng tại Bước 2** — Chờ user trả lời Q&A trước khi tiếp tục
3. **PHẢI dừng tại Bước 4** — Human Checkpoint: Tester tự đánh giá rủi ro
4. **Test Data phải cụ thể** — Không dùng placeholder (`"email hợp lệ"` → `"test@domain.com"`)

---

## 🔗 Slash Commands

| Command | Mô tả |
|---------|-------|
| `/generate_manual_testcases_rbt` | Sinh manual TCs theo AI-RBT 6 bước (**dùng chính**) |
| `/generate_requirements_from_website` | Phân tích UI/website → sinh Requirements |
| `/generate_testcases_from_requirements` | Sinh TCs từ requirements đã có |
