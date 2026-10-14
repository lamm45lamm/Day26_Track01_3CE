# Phần phụ trách và rà soát – Vũ Quốc Bảo (2A202602829)

Phạm vi: **Tầng 4 Chất lượng & độ tin cậy (chỉ số #7, #8)** và **Tầng Rủi ro / bàn giao (chỉ số #12)** trong [dashboard v2](../dashboard/dashboard_hanh_dong_v2.xlsx).

> File này chỉ ghi lại phần việc và góp ý rà soát. Không thay đổi nội dung dashboard v2 và memo nhóm đã chốt.

## 1. Chỉ số phụ trách

| # | Chỉ số | Mốc đầu → Mục tiêu 90 ngày (ngưỡng cảnh báo) | Quyết định gắn với chỉ số |
|---|---|---|---|
| 7 | Tỷ lệ ticket đạt QA lần đầu (không cần làm lại) | 88% → 92% (85%) | Mức kiểm soát của người cho từng loại ticket (người làm / AI hỗ trợ / tự động có kiểm soát) |
| 8 | Tỷ lệ bản nháp trích dẫn đúng điều khoản chính sách | 40% → 90% (35%) | Cho phép gửi nháp ít chỉnh sửa hay luôn bắt buộc kiểm tra chính sách |
| 12 | Tỷ lệ ticket nhạy cảm được AI gắn cờ chuyển người xử lý | 70% → 95% (85%) | Phạm vi ticket được phép có nháp AI |

## 2. Góp ý đã đưa cho nhóm và đã có trong v2

1. Mẫu QA (#7) tách 50 ticket/tuần thành 25 có nháp + 25 không nháp, báo cả hai nhóm; kèm lưu ý cỡ mẫu nhỏ nên sai số khoảng ±9 điểm % — đọc xu hướng nhiều tuần thay vì một tuần đơn lẻ.
2. #8: đặt ngưỡng cảnh báo tệ hơn mốc đầu (35% so với mốc đầu 40%) và quy định khi tỷ lệ trích dẫn đúng còn <80% thì bắt buộc nhân viên kiểm tra nguồn trước khi gửi, không chỉ dựa vào nhãn tự động của nháp.
3. #12: lấy mẫu ticket nhạy cảm ngẫu nhiên từ toàn bộ ticket (không lấy từ danh sách AI đã tự gắn cờ) để tránh thiên lệch; chưa đạt ngưỡng 85% thì chặn nháp cho nhóm ticket nhạy cảm.

## 3. Lưu ý rà soát thêm (đề xuất cho vòng sau, chưa áp dụng)

1. **#7 – ngưỡng cảnh báo trùng ngưỡng hành động:** "cảnh báo" (85%) và điều kiện bị coi là xấu ("<85% hai tuần liên tiếp") đang dùng chung một mốc. Với sai số mẫu ±9 điểm %, chỉ số dao động quanh baseline 88% có thể chạm 85% dù chất lượng không thực sự giảm. Nên tách ngưỡng cảnh báo sớm (ví dụ 87%) khỏi ngưỡng hành động (85%) để tránh cảnh báo giả mỗi tuần.
2. **#7 – so sánh nhóm có nháp / không nháp:** điều kiện leo thang "nhóm có nháp thấp hơn nhóm không nháp ≥5 điểm trong 2 tuần" khó tin cậy vì mỗi nhóm chỉ 25 ticket/tuần (sai số ước tính ±9–19 điểm % tuỳ tuần). Nên dồn số liệu theo cửa sổ trượt 3–4 tuần trước khi so sánh chênh lệch, thay vì so sánh theo từng tuần.
3. **#8 – tiêu chí "trích dẫn đúng":** chưa có định nghĩa bằng văn bản cho "đúng điều khoản" (đúng điều khoản nhưng hết hiệu lực, đúng ý nhưng sai mã điều khoản, v.v.). Cần một rubric ngắn (2–3 tiêu chí) để QA chấm nhất quán giữa các tuần và giữa các thành viên QA.
4. **#8 – chọn mẫu 30 nháp/tuần:** mẫu hiện chỉ lấy "nháp có nội dung chính sách", nhưng không có tiêu chí để xác định ticket nào thuộc nhóm này. Nếu để QA tự chọn thủ công, dễ thiên lệch về các ticket rõ ràng/dễ chấm. Nên lọc tự động theo từ khoá/loại ticket rồi lấy mẫu ngẫu nhiên trong nhóm đó.
5. **#12 – nhịp báo cáo:** #12 đọc "hằng tuần" nhưng cỡ mẫu ước tính chỉ ~30 ticket nhạy cảm/tuần (sai số lớn như Hà Thị Mỹ Linh đã nêu, ±16 điểm % với n=30). Đề xuất bổ sung rõ: quyết định chặn/mở nháp cho nhóm nhạy cảm chỉ dựa trên số liệu dồn ≥2 tuần, số liệu 1 tuần chỉ mang tính theo dõi.
6. **#12 – ranh giới với #8:** một ticket nhạy cảm có nội dung chính sách có thể vừa tính vào mẫu #8 vừa vào mẫu #12. Nên ghi rõ thứ tự ưu tiên xử lý (ví dụ: ticket nhạy cảm luôn bị chặn nháp trước, nên sẽ không xuất hiện trong mẫu #8 "nháp được kiểm") để hai chỉ số không đếm trùng hoặc mâu thuẫn khi báo cáo.
