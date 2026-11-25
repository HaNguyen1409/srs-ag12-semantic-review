# srs-ag12-semantic-review

**AG-12** · Agent Node · phiên bản **1.1.0** · giấy phép MIT

> Vietnamese-language Claude skill — one independent, reusable service of the SRS-SOP agent pipeline. Machine-readable contract: [`skill.json`](skill.json).

Agent Node AG-12 (Bước 22 SOP viết SRS): rà soát SRS với góc nhìn dev mới, tìm mơ hồ, mâu thuẫn, yêu cầu không kiểm thử được, lệch SRS–prototype và thiếu dữ kiện; chấm mức độ, kết luận ĐẠT/KHÔNG ĐẠT, chỉ chặn với Blocker.

## Hợp đồng giao tiếp

Skill là một dịch vụ độc lập, ghép lỏng: nhận đầu vào và trả đầu ra dưới dạng tài liệu/JSON mô tả trong [`SKILL.md`](SKILL.md), không gọi trực tiếp skill khác và không gắn với dự án cụ thể. Dùng riêng lẻ, hoặc ghép qua bộ điều phối [`srs-sop-pipeline`](https://github.com/HaNguyen1409/srs-sop-pipeline).

| Bước SOP | Việc | Loại | Nhận từ | Chuyển tới |
|---|---|---|---|---|
| 22 | Rà soát chất lượng ngữ nghĩa | Agent | B20, B21, B13 | B23 (đạt) / B18, B19, B20 (Blocker) |

**Skill phía trước (cấp đầu vào):** [`srs-ag08-prototype-builder`](https://github.com/HaNguyen1409/srs-ag08-prototype-builder) `^1.1.0`

**Skill phía sau (dùng đầu ra):** [`srs-ag10-functional-spec`](https://github.com/HaNguyen1409/srs-ag10-functional-spec) `^1.0.0` · [`srs-ag14-data-design`](https://github.com/HaNguyen1409/srs-ag14-data-design) `^1.0.0` · [`srs-ag11-nfr-spec`](https://github.com/HaNguyen1409/srs-ag11-nfr-spec) `^1.0.0`

## Cài đặt

**Claude Code** — clone đúng phiên bản vào thư mục skill:

```bash
git clone --branch v1.1.0 https://github.com/HaNguyen1409/srs-ag12-semantic-review.git ~/.claude/skills/srs-ag12-semantic-review
```

Nâng cấp: `git -C ~/.claude/skills/srs-ag12-semantic-review fetch --tags && git -C ~/.claude/skills/srs-ag12-semantic-review checkout v<phiên-bản-mới>`.

**claude.ai / Claude Desktop** — tải `srs-ag12-semantic-review-v1.1.0.zip` ở trang [Releases](https://github.com/HaNguyen1409/srs-ag12-semantic-review/releases) rồi tải lên ở phần Skills trong cài đặt.

**Cả bộ** — xem [`srs-sop-skills`](https://github.com/HaNguyen1409/srs-sop-skills) (cài toàn bộ skill theo phiên bản đã khoá).

## Quản lý phiên bản

Theo [SemVer](https://semver.org/lang/vi/), áp cho hợp đồng giao tiếp của skill:

| Tăng | Khi |
|---|---|
| MAJOR | Đổi hợp đồng làm vỡ skill phía sau: đổi/bỏ trường JSON, đổi hệ mã ID, đổi bố cục tài liệu đầu ra |
| MINOR | Thêm khả năng tương thích ngược: trường tuỳ chọn, mục mới, chế độ mới |
| PATCH | Sửa câu chữ, sửa lỗi, làm rõ luật mà không đổi đầu ra |

Phát hành: sửa `SKILL.md` → tăng `version` trong frontmatter, `VERSION`, `skill.json` → thêm mục vào [`CHANGELOG.md`](CHANGELOG.md) → `python tools/check_skill.py` → commit → `git tag -a vX.Y.Z -m "vX.Y.Z"` → `git push --follow-tags`. GitHub Actions kiểm lại, chạy test và đính kèm zip vào Release.

## Giấy phép

MIT — xem [`LICENSE`](LICENSE).
