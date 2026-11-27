# Plugin Aiva · nhật ký phiên bản

Luật đánh số (ADR-025 §3, V1):
- Thêm hoặc đổi skill, lệnh, connector → tăng bản phụ.
- Chỉ sửa chữ → tăng bản vá.
- Bỏ hoặc đổi nghĩa lệnh, công cụ → tăng bản chính. Cầu vẫn nhận bản cũ ít nhất 90 ngày.
- `version` trong `.claude-plugin/plugin.json` và `plugin.json` luôn cùng số với `PLUGIN_AIVA.latest` (`src/transports/phong-bi-nhap.ts`).

## 1.0.0 · 27/11/2026 (SP-78)
- Connector `aiva` → Cầu Aiva `https://v5.aiva.vn/api/public/bridge`. Cần Cầu có `import_skill.files[]` + `upload` (SP-73 · 73-2, khe 73c) trên v5.
- Skill `aiva-core` 1.0.4 (Trợ lý Aiva, chép nguyên bản trong Kho).
- Skill mới `aiva-dong-bo` 1.0.0: đưa thư mục hoặc zip lên Kho. Mỗi kỹ năng một lần `import_skill`, gửi đủ mọi tệp kèm, chia lượt khi lớn. Hỏi người dùng một lần trước khi gửi. Gặp trần gói thì dừng. Gợi ý giao cho nhân sự rồi `install_package(staff_id)`.
- Lệnh Claude: `/aiva-sync <thư mục|zip>`, `/aiva-status`.
- Gói chở `aiva.bundle.v1` · nhãn `aiva.core.v2` · vỏ chạy `aiva.envelope.v1`.
