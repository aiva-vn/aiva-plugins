# Nhận dạng thư mục/zip (ADR-025 §6.1 · cùng bảng `NHAN_DANG` ở `src/transports/phong-bi-nhap.ts`)

Xét gốc của từng thư mục con, theo đúng thứ tự dưới. Gặp luật nào khớp thì dừng.

| # | Dấu hiệu ở gốc | Loại | Kỹ năng nằm ở |
|---|---|---|---|
| 1 | `aiva.plugin.v1.json` | `aiva_plugin_v1` | `skills/*/` |
| 2 | `.claude-plugin/plugin.json` | `claude_plugin` | `skills/*/` |
| 3 | `plugin.json` có `$schema` chứa `agent-plugins` | `agent_plugins_1` | `skills/*/` |
| 4 | `SKILL.md` ở gốc | `single` | chính thư mục đó |
| 5 | còn lại | `skills_folder` | mọi thư mục có `SKILL.md`, sâu ≤ 6 cấp |

Tên và bản của bộ lấy từ `name` và `version` của tệp plugin (luật 1–3). Dùng để báo người dùng («từ ban-hang-pro 1.2.0»).

Một thư mục có `SKILL.md` là **một kỹ năng**, gồm mọi tệp bên trong nó. Có `tac-nhan/<tên>/SKILL.md` hoặc `agents/<tên>/SKILL.md` bên trong thì đó là đội: gửi cả cây một lần, Aiva dựng Agent chính và Agent con (SP-73 · 73-4).

## Bỏ (báo người dùng kèm lý do)
| Mẫu | Lý do |
|---|---|
| `node_modules/`, `venv/`, `.venv/`, `__pycache__/`, `dist/`, `build/` | thư mục thư viện hoặc bản dựng |
| `.git/`, `__MACOSX/`, `.DS_Store`, thư mục bắt đầu bằng `.` (trừ `.claude-plugin/`) | thư mục ẩn hoặc tạm |
| `.env`, `*.pem`, `*.key`, tệp tên có `secret`, `credential`, `token` | có thể chứa bí mật |
| `commands/`, `hooks/` của plugin Claude | Plugin Aiva 1.0.0 chưa nhận |

## Gửi (SP-73)
- **Tệp chữ** (`.md .txt .json .yaml .yml .csv .py .sh .js .ts .html .css .xml .svg`): `encoding: "utf8"`.
- **Tệp còn lại:** `encoding: "base64"`.
- `sha256` tính trên byte gốc.
- **Trần:**
  - một tệp ≤ 5 MB;
  - một kỹ năng ≤ 200 tệp, ≤ 25 MB;
  - một lượt gửi ≤ 4 MB, ≤ 60 mục. Lớn hơn thì chia lượt bằng `upload`.
