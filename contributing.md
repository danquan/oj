# Hướng dẫn đóng góp cho COPE (Contributing to COPE)

Cảm ơn bạn đã quan tâm và muốn đóng góp cho dự án **COPE**! Dưới đây là các hướng dẫn giúp bạn tham gia phát triển dự án một cách hiệu quả và thuận tiện nhất.

---

## 1. Báo cáo lỗi (Issue Tracker)

Trước khi mở một issue mới:
- Kiểm tra danh sách [Issues đã có trên GitHub](https://github.com/danquan/oj/issues) xem vấn đề bạn gặp phải đã được báo cáo hay xử lý chưa.

Nếu chưa có:
- Vui lòng [mở một Issue mới tại đây](https://github.com/danquan/oj/issues/new).
- Cung cấp tiêu đề ngắn gọn, mô tả chi tiết các bước tái hiện lỗi (reproduction steps), ảnh chụp màn hình hoặc log lỗi nếu có.

---

## 2. Gửi thay đổi (Submitting Pull Requests)

1. **Fork & Tạo nhánh mới**:
   ```bash
   git checkout -b feature/ten-tinh-nang-moi
   # hoặc:
   git checkout -b fix/mo-ta-loi
   ```
2. **Quy chuẩn mã nguồn (Coding Conventions)**:
   - **Python**: Kiểm tra code tuân thủ tiêu chuẩn PEP 8 bằng [flake8](https://flake8.pycqa.org/en/latest/):
     ```bash
     flake8
     ```
   - **JavaScript / Frontend**: Định dạng code với `prettier` (trong `websocket/` hoặc các thư mục giao diện tương ứng).
3. **Mô tả Pull Request rõ ràng**:
   - Nêu rõ vấn đề mà PR này giải quyết, kèm theo liên kết tới issue liên quan (ví dụ: `Closes #123`).
   - Kiểm tra kỹ các commit trước khi tạo [Pull Request trên GitHub](https://github.com/danquan/oj/pulls).

---

## 3. Đóng góp bản dịch (Localization)

Hệ thống hỗ trợ đa ngôn ngữ thông qua Django gettext:
- Các tệp bản dịch tiếng Việt nằm tại thư mục [locale/vi/LC_MESSAGES/](locale/vi/LC_MESSAGES/).
- Sau khi chỉnh sửa tệp `.po`, hãy biên dịch sang tệp `.mo` trước khi kiểm thử:
  ```bash
  python manage.py compilemessages
  ```