Team: 3CE
| Họ tên | MSSV | Phần phụ trách | Góp ý đã đưa cho nhóm bạn |
| :--- | :--- | :--- | :--- |
| Đỗ Thanh Lâm | 2A202602577 | Tầng 1 Sử dụng và tầng 2 Hành vi (chỉ số #1–#4): tỷ lệ ticket được sinh nháp, tỷ lệ nháp được dùng, tỷ lệ nháp bị sửa >50%, tỷ lệ nhân viên dùng nháp; hành động chẩn đoán theo ADKAR | Thống nhất mẫu số của #2 và #3 ("ticket có nháp được hiển thị") để đọc được thành phễu dùng / sửa nhiều / bỏ; chuyển #3 sang Product-level, owner là PO trợ lý AI; đặt lại ngưỡng cảnh báo #2, #3, #4 ở mức tệ hơn baseline (v1 vượt ngưỡng ngay từ đầu) |
| Vũ Quốc Bảo | 2A202602829 | Tầng 3 Năng suất và tầng 4 Chất lượng & độ tin cậy (chỉ số #5–#8): AHT, số ticket/nhân viên/ca, tỷ lệ đạt QA lần đầu, tỷ lệ nháp trích dẫn đúng chính sách | Định nghĩa lại AHT: tính từ lúc nhân viên nhận ticket, không lẫn thời gian chờ trong hàng đợi; đặt lại ngưỡng cảnh báo #5, #6, #8 ở mức tệ hơn baseline; mẫu QA 50 ticket/tuần chia 25 có nháp + 25 không nháp, có lưu ý sai số khoảng ±9 điểm % |
| Hà Thị Mỹ Linh | 2A202602619 | Tầng 5 Giá trị và Rủi ro / bàn giao (chỉ số #9–#12): CSAT, FCR, số sự cố nghiêm trọng, tỷ lệ ticket nhạy cảm được gắn cờ; quyết định gắn với từng chỉ số | Ghi nguồn dữ liệu tới từng trường/sự kiện và đánh dấu baseline nào đã đo, baseline nào còn ước tính; mẫu ticket nhạy cảm (#12) lấy ngẫu nhiên từ toàn bộ ticket để tránh sai lệch; ghi chú FCR trễ 7 ngày; mỗi hành động khi chỉ số xấu có thời hạn và bước leo thang |

## Phạm vi

Sau 3 tháng triển khai trợ lý AI soạn nháp phản hồi, nhân viên CSKH tuyến 1 chỉ dùng khoảng 1/4 số bản nháp. Phần còn lại bị xoá và viết lại thủ công, nên thời gian xử lý trung bình mỗi ticket gần như không đổi.

## Nguyên nhân gốc

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

## Cách làm mới

- **Nguồn kiểm chứng:** mỗi bản nháp hiển thị điều khoản chính sách được trích (ID/link từ knowledge base đã chuẩn hoá); nháp không có nguồn tự gắn nhãn "cần kiểm tra".
- **Người chịu trách nhiệm:** nhân viên gửi chịu trách nhiệm nội dung cuối cùng gửi khách; PO trợ lý AI chịu trách nhiệm chất lượng nháp (knowledge base, prompt, dữ liệu đơn); Phụ trách QA kiểm mẫu hằng tuần.
- **Khi AI không chắc:** nếu không tìm được nguồn chính sách thì AI không đưa nháp, nhân viên tự soạn; ticket nhạy cảm (pháp lý, bồi thường, khách VIP) không sinh nháp mà chuyển thẳng cho người xử lý.

## Chỉ số

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

## Quyết định

**Sửa** — tiếp tục thí điểm ở tuyến 1 và chưa mở rộng sang tuyến 2.

**Lý do:** nguyên nhân gốc nằm ở chất lượng nháp và sửa được, trong khi chất lượng dịch vụ chưa bị ảnh hưởng (QA đạt lần đầu 88%, CSAT 82%, 0 sự cố).

**2 thay đổi so với v1:**

1. Đặt lại ngưỡng cảnh báo ở mức tệ hơn baseline — ở v1, 6/12 chỉ số đã vượt ngưỡng ngay từ đầu nên cảnh báo mất tác dụng.
2. Định nghĩa lại AHT: tính từ lúc nhân viên nhận ticket thay vì lúc ticket được tạo, để không lẫn thời gian chờ trong hàng đợi.