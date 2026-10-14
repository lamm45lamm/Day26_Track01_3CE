# Phần phụ trách và rà soát – Hà Thị Mỹ Linh (2A202602619)

Phạm vi: **Tầng 5 Giá trị và Rủi ro / bàn giao (chỉ số #9–#12)** trong [dashboard v2](../dashboard/dashboard_hanh_dong_v2.xlsx).

> File này chỉ ghi lại phần việc và góp ý rà soát. Không thay đổi nội dung dashboard v2 và memo nhóm đã chốt.

## 1. Chỉ số phụ trách

| # | Chỉ số | Mốc đầu → Mục tiêu 90 ngày (ngưỡng cảnh báo) | Quyết định gắn với chỉ số |
|---|---|---|---|
| 9 | Tỷ lệ khách hài lòng sau ticket (CSAT) | 82% → 85% (80%) | Tiếp tục, thu hẹp hay dừng mở rộng trợ lý AI |
| 10 | Tỷ lệ giải quyết ngay lần phản hồi đầu (FCR) | 65% → 72% (62%) | Có đủ bằng chứng giá trị để trình duyệt ngân sách giai đoạn 2 |
| 11 | Số sự cố nghiêm trọng do bản nháp AI | 0 → 0 (1 vụ) | Bật / tắt nháp AI cho từng loại ticket |
| 12 | Tỷ lệ ticket nhạy cảm được AI gắn cờ chuyển người xử lý | 70% → 95% (85%) | Phạm vi ticket được phép có nháp AI |

## 2. Góp ý đã đưa cho nhóm và đã có trong v2

1. Ghi nguồn dữ liệu tới từng trường / sự kiện (`draft_generated`, `assigned_at`, `first_reply_at`, `flag_sensitive`…) và đánh dấu mốc đầu nào đã đo, mốc đầu nào còn ước tính.
2. #12: lấy mẫu ngẫu nhiên từ toàn bộ ticket, không lấy từ danh sách AI đã gắn cờ, để tránh sai lệch.
3. #10: ghi chú FCR trễ 1 tuần do phải chờ 7 ngày xem ticket có bị mở lại không.
4. Mỗi hành động khi chỉ số xấu đều có thời hạn ("Trong 1 tuần", "Trong 24 giờ") và bước leo thang.

## 3. Lưu ý rà soát thêm (đề xuất cho vòng sau, chưa áp dụng)

1. **#12:** mốc đầu 70% thấp hơn ngưỡng 85% là cố ý, vì 85% là ngưỡng an toàn dùng để chặn nháp cho ticket nhạy cảm. Đây là ngoại lệ của nguyên tắc "ngưỡng tệ hơn mốc đầu" và nên được ghi rõ.
2. **#12 – cỡ mẫu:**
   - Muốn có khoảng 30 ticket nhạy cảm từ mẫu ngẫu nhiên thì cần ghi tổng số ticket phải lấy mẫu.
   - Với n = 30, sai số khoảng ±16 điểm % nên nên đọc xu hướng nhiều tuần.
3. **#12:** mới đo tỷ lệ bắt đúng (recall). Nên theo dõi thêm tỷ lệ gắn cờ nhầm để tránh dồn việc cho người xử lý.
4. **#11:** cần thống nhất "trong kỳ" là tuần hay tháng, cho khớp với ngưỡng 1 vụ.
5. **#10:** có thể tách FCR theo nhóm có nháp / không nháp như #9, để thấy tác động của nháp AI.
