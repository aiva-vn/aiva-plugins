---
description: Đưa cả thư mục hoặc tệp zip skill/Agent lên Kho Aiva (Plugin Aiva 1.0.0)
argument-hint: <đường dẫn thư mục hoặc .zip>
---

Dùng skill `aiva-dong-bo` để đưa `$ARGUMENTS` lên Kho riêng của không gian Aiva đang nối.

- Không có đường dẫn thì hỏi một câu và gợi ý `~/.claude/skills`.
- Làm đúng thứ tự trong skill:
  1. `start` (kiểm nối và bản);
  2. đọc, nhận dạng, lọc;
  3. `search_skills` (installed_only) rồi hỏi người dùng một lần;
  4. `import_skill` cho từng kỹ năng (đủ tệp, chia lượt bằng `upload` khi lớn);
  5. báo kết quả;
  6. `list_staff` để gợi ý giao, rồi `install_package(staff_id)` cho từng cặp được đồng ý.
