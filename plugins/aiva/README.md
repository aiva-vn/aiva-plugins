# Plugin Aiva 1.0.1

Một gói cài vào Claude hoặc ChatGPT. Plugin nối trợ lý với không gian Aiva. Khi người dùng nói «đưa thư mục này lên Aiva», plugin đưa cả bộ skill/Agent vào Kho riêng: đủ tài liệu kèm, đóng phong bì chuẩn Aiva, có gợi ý giao cho nhân sự AI.

## Cài
| Trạm | Cách cài |
|---|---|
| Claude Code · Cowork | `/plugin marketplace add aiva-vn/aiva-plugins`, rồi `/plugin install aiva@aiva-plugins`. Bản mới tự cập nhật qua marketplace. Chưa có marketplace thì giải nén `aiva-plugin-1.0.1-claude.zip` rồi `/plugin install` từ thư mục `aiva/` |
| Claude (web/desktop) | Settings › Connectors › Add custom connector › URL `https://v5.aiva.vn/api/public/bridge`. Sau đó Settings › Capabilities › Skills › tải `aiva-plugin-1.0.1-skill-aiva-dong-bo.zip` |
| ChatGPT | Nối connector Aiva theo hướng dẫn ở v5.aiva.vn › Cài đặt › Kết nối. Sau đó Plugin › Thêm › tải `aiva-plugin-1.0.1-chatgpt.zip` |

Kiểm sau khi cài:
- Claude: gõ `/aiva-status`;
- ChatGPT: nói «Aiva ơi, kiểm plugin».

## Dùng
- Claude: `/aiva-sync ~/skills`, hoặc «Aiva ơi, đồng bộ thư mục ~/skills lên Kho».
- ChatGPT: kéo `skills.zip` vào chat rồi nói «đưa lên Aiva».

## Bên trong
- `skills/aiva-core`: Trợ lý Aiva. Định tuyến `@Agent`, Chợ, lưu kết quả.
- `skills/aiva-dong-bo`: đồng bộ thư mục/zip. Bảng nhận dạng ở `references/nhan-dien.md`, nhãn phong bì ở `references/dong-nhan.md`.
- `commands/`: `/aiva-sync`, `/aiva-status`. Chỉ dùng trên Claude.
- `.mcp.json`: connector `aiva`.

Nguồn ở repo `aiva-vn/aiva-fresh-foundation`, thư mục `plugins/aiva/`. Bản dựng tạo bằng `python3 -I scripts/plugin-aiva/build.py`. Thiết kế: ADR-025.
