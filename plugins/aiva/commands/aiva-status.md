---
description: Xem bản Plugin Aiva, bản Cầu, không gian và đội đang nối
---

Gọi công cụ `start` của Aiva, rồi in đúng 3 dòng:

```
Plugin Aiva 1.0.0 · <«mới nhất» nếu start.plugin.latest = 1.0.0, không thì «có bản <latest>: <download.claude>»>
Cầu Aiva <start.versions.bridge> · phong bì <start.versions.core> / <start.versions.envelope>
Không gian: <tên> (<vai của người dùng nếu có>) · <số nhân sự> nhân sự · <số việc chờ> việc chờ
```

- Không có công cụ Aiva → in «Chưa nối Aiva: thêm connector Aiva (https://v5.aiva.vn/api/public/bridge) rồi mở chat mới».
- `start.plugin.min` lớn hơn 1.0.0 → thêm dòng «Bản này đã cũ, cần cập nhật».
- `start` chưa có `plugin` hay `versions` (Cầu trước SP-78) → in «chưa báo» ở chỗ thiếu, không đoán.
