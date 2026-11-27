# Plugin Aiva 1.0.1

Một gói cài vào Claude hoặc ChatGPT để nối với Aiva (v5.aiva.vn) và đưa cả thư mục Agent/skill của bạn lên Kho Aiva, tự đóng phong bì chuẩn Aiva.

> Repo này **sinh tự động** từ `aiva-vn/aiva-fresh-foundation/plugins/aiva` bằng `scripts/plugin-aiva/build.py --publish`. Đừng sửa tay ở đây; sửa ở repo nguồn rồi đăng lại.

## Cài

| Nơi dùng | Cách cài |
|---|---|
| Claude Code · Cowork | `/plugin marketplace add aiva-vn/aiva-plugins` rồi `/plugin install aiva@aiva-plugins`. Bản mới tự kéo khi cập nhật marketplace |
| Claude (web, desktop) | Tải `aiva-plugin-1.0.1-skill-aiva-dong-bo.zip` ở https://v5.aiva.vn/plugins/ rồi Settings › Capabilities › Skills › Upload skill. Nối connector Aiva theo hướng dẫn trong Aiva |
| ChatGPT | Tải `aiva-plugin-1.0.1-chatgpt.zip` ở https://v5.aiva.vn/plugins/ rồi thêm vào mục Plugin |

## Dùng

- «Aiva ơi, đồng bộ thư mục ~/skills lên Kho» hoặc `/aiva-sync ~/skills`
- `/aiva-status`: bản plugin, bản Cầu, không gian đang nối

Luật và bảng phiên bản: ADR-025 trong repo nguồn. Lịch sử bản: `plugins/aiva/CHANGELOG.md`.
