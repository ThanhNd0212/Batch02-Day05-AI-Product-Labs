# Toolkit — Từ Evidence Đến Build Slice

Dùng sau khi nhóm đã có evidence. Mục tiêu là chốt một build slice đủ nhỏ cho Day 06.

## 1. Gom evidence thành cụm

Gom theo **workflow/pain**, không gom theo tên feature.

Ví dụ cụm tốt:
- booking thất bại và gặp chậm trễ trong việc hoàn tiền, thanh toán
- khó khăn trong việc giải đáp thắc mắc trực tuyến
## 2. Viết insight

Form:

```text
User khi đặt chuyến không chỉ những địa điểm và phương thức available.
Họ thật ra cần giải đáp thắc mắc kịp thời, được gợi ý chuyến đi theo như cầu (tài chính, người đi), tình hình thời tiết
vì trong app hiện tại đang thiếu các tính năng hỗ trợ giải đáp thắc mắc trực tuyến, gợi ý chuyến đi linh hoạt.
```

## 3. Viết opportunity

Form:

```text
Cơ hội là dùng AI gợi ý chuyến đi
giúp để dựa vào tình hình thời tiết từng khu vực trong khoảng thời gian user muốn đi, so sánh giá các dịch vụ đáp ứng và gợi ý người dùng trước khi đặt chuyến
trong khi vẫn kiểm soát quyền kiểm soát chốt chuyến đi cuẩ người dùng.
```

## 4. Chọn build slice

Build slice tốt phải qua 5 câu hỏi:

| Câu hỏi | Đạt khi |
|---|---|
| Người chưa hiểu rõ tình hình thời tiết, đại hình tài chính của một đất nước lạ | Khách nước ngoài, người ít kinh nghiệm du lịch được trợ giúp chọn chuyến đi |
| AI đánh giá rủi ro thời tiết & so sánh giá | AI đề xuất, lọc các địa điểm theo mức độ phù hợp giảm dần |


## 5. Quyết định: giữ, giảm scope, hay đổi hướng?

| Tình huống | Quyết định |
|---|---|
| Evidence yếu, user mơ hồ | Dừng build sâu; quay lại research 20 phút. |
| Ý tưởng quá rộng | Giữ domain, cắt xuống một flow. |
| AI không cần thiết | Dùng rule/manual prototype; ghi rõ vì sao không dùng AI sâu. |
| Rủi ro cao | Chọn augmentation hoặc conditional automation. |
| Không demo được trong 1 ngày | Đưa phần lớn vào backlog, giữ một path nhỏ. |

## 6. Câu chốt cuối

Điền câu này trước khi rời lớp:

```text
Dựa trên [evidence],
nhóm sẽ build [prototype slice],
cho [user],
để giải quyết [pain],
bằng cách AI [augment/automate task],
và sẽ test failure path [failure mode].
```

## 7. Backlog

Những thứ **không build trong Day 06**:

- 
- 
- 
