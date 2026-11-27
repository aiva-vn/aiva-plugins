# Nhãn phong bì Aiva (ADR-025 §2, §6.3)

Phong bì Aiva có hai mặt:
- **Nhãn** là khối `metadata.aiva` trong SKILL.md. Từ khi SP-78 · 78-1 lên v5, Cầu tự đóng nhãn khi nhập: chỉ thêm phần thiếu, thân SKILL.md giữ nguyên. Trước đó, gói thiếu nhãn vẫn nhập được và chạy với vỏ chạy mặc định.
- **Vỏ chạy** là 8 mục Cầu bọc ở mỗi lần `begin_work`. Bạn không tự viết vỏ chạy, cũng không chép ĐẦU/ĐUÔI Aiva vào thân skill.

Khi người dùng muốn nhãn đẹp hơn bản máy điền, gợi ý họ tự khai trong SKILL.md:

```yaml
metadata:
  aiva:
    version: "1.0.0"            # semver; Kho ghi đúng bản này cho gói mới, hoặc khi lớn hơn bản đang có
    core:
      schema: aiva.core.v2
      uses_when: "≤ 12 chữ, khác gói khác"
      call_example: "@<Tên> <câu mẫu>"
      context:
        reads: []               # khoá bối cảnh chuẩn cần đọc
        writes: []
      knowledge:
        tags: []
      outputs: ["doc"]          # doc | sheet | link | site | team | form
      drive:
        default: false
      metrics:
        minutes_saved_estimate: 15
    output:
      kind: page
      template: page.report     # page.report | page.analysis | page.plan | page.content | page.brief | sheet.table | app.html | site.landing
```

Trường máy điền được ghi trong `metadata.aiva.imported.inferred`. Trang Agent ở Kho hiện danh sách này để người dùng biết chỗ nên sửa tay.

## Bản của từng lớp
| Lớp | Bản |
|---|---|
| Plugin Aiva | 1.0.0 |
| Cầu Aiva | bản có `import_skill.files[]` (SP-73) · đóng nhãn từ SP-78 |
| Gói chở | `aiva.bundle.v1` |
| Nhãn | `aiva.core.v2` |
| Vỏ chạy | `aiva.envelope.v1` |
| Từng Agent | semver riêng trong Kho |

`/aiva-status` in đủ các bản này.
