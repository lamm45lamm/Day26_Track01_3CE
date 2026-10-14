Team: 3CE
| Họ tên | MSSV | Phần phụ trách | Góp ý đã đưa cho nhóm bạn |
| :--- | :--- | :--- | :--- |
| Đỗ Thanh Lâm | 2A202602577 | Nhóm chỉ số mức sử dụng của trợ lý AI (#1–#3): tỷ lệ ticket được sinh nháp, tỷ lệ nháp được dùng để gửi khách, tỷ lệ nháp bị sửa >50% nội dung | Nhóm ABU: Thống nhất mẫu số của #2 và #3 ("ticket có nháp được hiển thị") để đọc được thành phễu dùng / sửa nhiều / bỏ; chuyển #3 sang Product-level, owner là PO trợ lý AI; đặt lại ngưỡng cảnh báo #2, #3 ở mức tệ hơn baseline (v1 vượt ngưỡng ngay từ đầu); ghi nguồn #1 là sự kiện `draft_generated` cần bật tracking trước ngày 1, #2 có phương án dự phòng là nút "Dùng nháp / Không dùng" |
| Vũ Quốc Bảo | 2A202602829 | Nhóm chỉ số chất lượng và an toàn (#7, #8, #12): tỷ lệ ticket đạt QA lần đầu, tỷ lệ nháp trích dẫn đúng chính sách, tỷ lệ ticket nhạy cảm được AI gắn cờ chuyển người xử lý | Nhóm ABU: Mẫu QA 50 ticket/tuần chia 25 có nháp + 25 không nháp, có lưu ý sai số khoảng ±9 điểm %; #8 đặt lại ngưỡng ở mức tệ hơn baseline và bắt buộc kiểm tra nguồn khi còn <80%; mẫu ticket nhạy cảm (#12) lấy ngẫu nhiên từ toàn bộ ticket để tránh sai lệch, chưa đạt 85% thì chặn nháp cho nhóm này |
| Hà Thị Mỹ Linh | 2A202602619 | Nhóm chỉ số giá trị và rủi ro (#9–#11): CSAT, FCR, số sự cố nghiêm trọng do bản nháp AI; quyết định tiếp tục / thu hẹp / dừng gắn với từng chỉ số | Nhóm ABU: CSAT tách theo ticket có / không dùng nháp, tuần ít hơn 100 phản hồi thì đọc theo tháng; ghi chú FCR trễ 1 tuần do chờ 7 ngày mở lại; #11 lập biểu mẫu báo cáo sự cố và định nghĩa "nghiêm trọng" bằng văn bản trước ngày 1, xử lý trong 24 giờ, vụ thứ 2 trong 30 ngày thì tạm dừng toàn bộ nháp |
| Đào Trọng Khang | 2A2026020974 | Nhóm chỉ số hành vi và năng suất (#4–#6): tỷ lệ nhân viên dùng nháp cho ≥50% ticket, thời gian xử lý trung bình mỗi ticket (AHT), số ticket xử lý / nhân viên / ca | Nhóm ABU: Định nghĩa lại AHT: tính từ lúc nhân viên nhận ticket, loại ticket >60 phút, tính lại baseline theo cùng công thức để so sánh công bằng; đặt lại ngưỡng cảnh báo #4, #5, #6 ở mức tệ hơn baseline; #4 chỉ báo cáo cấp nhóm, không dùng để phạt cá nhân; #6 ghi kèm tổng ticket đầu vào và lịch ca thực tế nộp mỗi thứ Hai |

## 2. Phạm vi

Sau 3 tháng triển khai trợ lý AI soạn nháp phản hồi, nhân viên CSKH tuyến 1 chỉ dùng khoảng 1/4 số bản nháp. Phần còn lại bị xoá và viết lại thủ công, nên thời gian xử lý trung bình mỗi ticket gần như không đổi.

## 3. Nguyên nhân gốc

**Nguyên nhân:**

1. Bản nháp sai hoặc thiếu chính sách và không hiển thị nguồn, nên nhân viên không tin và phải tự tra lại — tốn thời gian ngang với tự viết.
2. Không có người chịu trách nhiệm chất lượng bản nháp và không có quy tắc khi AI không chắc: AI vẫn sinh nháp cho mọi ticket, kể cả ticket nhạy cảm.

**Framework:**

- **5 Whys:** từ AHT không giảm lần ra knowledge base chính sách chưa chuẩn hoá và nháp thiếu nguồn.
- **Thang chỉ số 5 tầng** (Sử dụng → Hành vi → Năng suất → Chất lượng → Giá trị): chuỗi giá trị đứt ở bước "nháp được dùng".

**Bằng chứng:**

- Định lượng, từ log helpdesk (so sánh nháp với bản gửi): 25% nháp được dùng, 60% nháp bị sửa >50% nội dung, AHT 9,5 phút.
- Kiểm tra mẫu của QA, 30 nháp/tuần: chỉ 40% nháp trích dẫn đúng điều khoản chính sách.
- QA gắn nhãn mẫu 30 ticket nhạy cảm: AI chỉ gắn cờ đúng 70%.

## 4. Cách làm mới

- **Nguồn kiểm chứng:** mỗi bản nháp hiển thị điều khoản chính sách được trích (ID/link từ knowledge base đã chuẩn hoá); nháp không có nguồn tự gắn nhãn "cần kiểm tra".
- **Người chịu trách nhiệm:** nhân viên gửi chịu trách nhiệm nội dung cuối cùng gửi khách; PO trợ lý AI chịu trách nhiệm chất lượng nháp (knowledge base, prompt, dữ liệu đơn); Phụ trách QA kiểm mẫu hằng tuần.
- **Khi AI không chắc:** nếu không tìm được nguồn chính sách thì AI không đưa nháp, nhân viên tự soạn; ticket nhạy cảm (pháp lý, bồi thường, khách VIP) không sinh nháp mà chuyển thẳng cho người xử lý.

## 5. Chỉ số

- **Product — Tỷ lệ bản nháp được dùng để gửi khách** (sửa ≤50% nội dung)
  - Baseline: 25%
  - Target: 60% sau 90 ngày
  - Nguồn: log helpdesk so sánh nháp với bản gửi
  - Owner: Trưởng nhóm CSKH tuyến 1
- **Product — Tỷ lệ bản nháp trích dẫn đúng điều khoản chính sách**
  - Baseline: 40%
  - Target: 90%
  - Nguồn: log truy xuất nguồn của AI + kiểm tra mẫu QA 30 nháp/tuần
  - Owner: Phụ trách QA
- **Workflow — Thời gian xử lý trung bình mỗi ticket (AHT)**, tính từ lúc nhân viên nhận ticket đến phản hồi đầu tiên
  - Baseline: 9,5 phút
  - Target: 7,0 phút
  - Nguồn: timestamp helpdesk (assigned_at → first_reply_at)
  - Owner: Quản lý vận hành CSKH

## 6. Quyết định

**Sửa** — tiếp tục thí điểm ở tuyến 1 và chưa mở rộng sang tuyến 2.

**Lý do:** nguyên nhân gốc nằm ở chất lượng nháp và sửa được, trong khi chất lượng dịch vụ chưa bị ảnh hưởng (QA đạt lần đầu 88%, CSAT 82%, 0 sự cố).

**2 thay đổi so với v1:**

1. Đặt lại ngưỡng cảnh báo ở mức tệ hơn baseline — ở v1, 6/12 chỉ số đã vượt ngưỡng ngay từ đầu nên cảnh báo mất tác dụng.
2. Định nghĩa lại AHT: tính từ lúc nhân viên nhận ticket thay vì lúc ticket được tạo, để không lẫn thời gian chờ trong hàng đợi.