# COPE [![Build Status](https://github.com/danquan/oj/workflows/build/badge.svg)](https://github.com/danquan/oj/actions/) [![AGPL License](https://img.shields.io/badge/license-AGPLv3.0-blue.svg)](http://www.gnu.org/licenses/agpl-3.0) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](contributing.md)

**COPE** (Competitive Online Programming Environment) là nền tảng chấm bài trực tuyến hiện đại và hệ thống tổ chức kỳ thi lập trình thi đấu.

Dự án được xây dựng và phát triển dựa trên nền tảng của [DMOJ](https://github.com/DMOJ/online-judge) và [VNOJ](https://github.com/VNOI-Admin/OJ).

---

## Tính năng nổi bật

- **Chấm bài đa ngôn ngữ**: Hỗ trợ hàng chục ngôn ngữ lập trình với độ trễ thấp và độ tin cậy cao.
- **Tổ chức contest linh hoạt**: Hỗ trợ nhiều thể thức thi đấu phổ biến (ICPC, IOI, AtCoder, VNOJ/COPE format, v.v.).
- **Tùy biến bài tập & Checker**: Tích hợp checker mặc định, custom checker bằng Python và C++ (`testlib.h`).
- **Giao diện hiện đại & Thân thiện**: Tối ưu hóa trải nghiệm người dùng, bảng xếp hạng realtime, quản lý tổ chức (Organizations) và blog/tin tức.

---

## Cài đặt (Installation)

### 1. Clone repository

```bash
git clone --recursive https://github.com/danquan/oj.git
cd oj
```

### 2. Thiết lập môi trường

Hệ thống kế thừa kiến trúc từ DMOJ & VNOJ. Bạn có thể tham khảo thêm tài liệu triển khai chuẩn của DMOJ tại [docs.dmoj.ca](https://docs.dmoj.ca/#/site/installation).

Các bước thiết lập cơ bản:
1. Cài đặt Python 3, Node.js, và các thư viện hệ thống cần thiết (MySQL/PostgreSQL, Redis, v.v.).
2. Cài đặt các gói phụ thuộc Python:
   ```bash
   pip install -r requirements.txt
   ```
3. Tạo và tinh chỉnh tệp cấu hình `dmoj/local_settings.py` từ mẫu cấu hình:
   - Cấu hình database kết nối MySQL hoặc PostgreSQL.
   - Định nghĩa `DMOJ_PROBLEM_DATA_ROOT` trỏ tới thư mục lưu trữ test case của các bài tập:
     ```python
     DMOJ_PROBLEM_DATA_ROOT = '/path/to/problem/data'
     ```
   - Cấu hình cache framework (`CACHES`) sử dụng `redis` hoặc `memcached` để đồng bộ giữa judge server và web site.
4. Chạy migration và chuẩn bị cơ sở dữ liệu:
   ```bash
   python manage.py migrate
   python manage.py loaddata demo
   ```
5. Build static assets (CSS/JS) và chạy server phát triển:
   ```bash
   python manage.py collectstatic --noinput
   python manage.py runserver 0.0.0.0:8080
   ```

---

## Lưu ý cấu hình bổ sung

- **Cấu hình Domain / Sites**: Khi tải dữ liệu mẫu bằng `python manage.py loaddata demo`, domain mặc định sẽ là `localhost:8081`. Bạn có thể thay đổi trực tiếp trong trang quản trị Admin (`/admin/sites/site/`) hoặc tệp [judge/fixtures/demo.json](judge/fixtures/demo.json) trỏ về domain mong muốn.
- **Hỗ trợ `testlib.h`**: Để sử dụng `testlib.h` cho các custom checker viết bằng C++, sao chép [testlib.h](https://github.com/MikeMirzayanov/testlib/blob/master/testlib.h) vào đường dẫn include của `g++` trên judge server. Bạn có thể tạo precompiled header (`testlib.h.gch`) để tăng tốc độ biên dịch.

---

## Đóng góp (Contributing)

Mọi đóng góp cho **COPE** đều được hoan nghênh! Vui lòng đọc [Hướng dẫn đóng góp (contributing.md)](contributing.md) trước khi gửi PR hoặc mở Issue.

- **Báo lỗi & Đề xuất tính năng**: Mở Issue tại [COPE Issues](https://github.com/danquan/oj/issues).
- **Quy chuẩn mã nguồn**: Kiểm tra định dạng code với `flake8` trước khi tạo Pull Request.
- **Đóng góp bản dịch**: Các tệp dịch thuật được lưu tại thư mục [locale/vi/LC_MESSAGES](locale/vi/LC_MESSAGES/).

---

## Giấy phép (License)

Dự án được phân phối dưới giấy phép [GNU AGPLv3](LICENSE).

