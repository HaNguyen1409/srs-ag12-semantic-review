# Changelog

Mọi thay đổi đáng kể của skill ghi ở đây. Định dạng theo [Keep a Changelog](https://keepachangelog.com/vi/1.1.0/), phiên bản theo [SemVer](https://semver.org/lang/vi/).

## [Unreleased]

## [1.1.0] - 2026-11-25

### Added

- Tách thành repo độc lập (microservice skill): `skill.json` khai báo hợp đồng giao tiếp và skill phụ thuộc, CI kiểm tính nhất quán, Release tự đóng zip.
- Ẩn danh hoá: bỏ tham chiếu tới dự án áp dụng cụ thể; skill dùng được cho mọi dự án.

### Lịch sử trước khi tách repo

- Phiên bản: 1.1 (21/11/2026: số bước theo bảng mục 1 của `srs-sop-pipeline`) · Đầu vào: SRS lắp từ các tài liệu con (Code Node B20, mẫu TL-02 bản 3.0) cùng `srs_bundle.json` và đã qua kiểm tra toàn vẹn cấu trúc (Code Node B21) + prototype phiên bản đã chốt (B14/B25) · Đầu ra: danh sách phát hiện + kết luận ĐẠT/KHÔNG ĐẠT · KHÔNG ĐẠT → chuyển Blocker tới bước sở hữu lỗi (`fix_owner`, mặc định B18); ĐẠT → Bước 23 (Tech Lead review).
