# Template — Evidence Pack

Nộp kèm thin SPEC cuối Day 05.

## 1. Nhóm và track

**Tên nhóm:** Nhóm Track B — Travel & Hospitality  
**Track:** Track B — Travel & Hospitality  
**Product/app đã chọn:** MyVinpearl / App Vinpearl  
**Build slice đang nghĩ:** AI hỗ trợ khách du lịch gia đình chọn 2-3 gói/ưu đãi Vinpearl phù hợp theo điểm đến, ngày đi, ngân sách, số người và mục đích chuyến đi; AI chỉ gợi ý, giải thích và cảnh báo điều kiện, không tự book/tự thanh toán.

## 2. Self-use evidence

Nhóm tự dùng app/workflow và ghi lại điểm gãy.

| Observation | Screenshot/link | Path liên quan | Điều học được |
|---|---|---|---|
|  |  | Happy / Low-confidence / Failure / Correction |  |
|  |  | Happy / Low-confidence / Failure / Correction |  |

## 3. User / review / social evidence

Nguồn có thể là review App Store/Play, group, comment, phỏng vấn nhanh, hoặc nguồn public khác.

| Quote / review / observation | Nguồn | User là ai? | Pain/failure mode |
| "Đặt rất khó hay mất kết nối và ko ổn định" | CH Play (MyVinpearl page) — 9 Apr 2026 | Thanh Nguyễn Đức (hiển thị) | Booking thất bại / mất kết nối / không hoàn tất giao dịch |
| "Trải nghiệm sử dụng tệ, Hệ thống lỗi không liên hệ được bên nào để xử lý" | AppStore (MyVinpearl page) — 3y ago | T (hiển thị) | Hệ thống hỗ trợ trực tuyến không hoạt động  |
| "Tệ. Khách hàng thanh toán chuyến xe đã đặt nhưng phía VinPearl không thực hiện cung cấp dịch vụ. Yêu cầu khách hàng chủ động di chuyển và báo sẽ hoàn tiền. Đã qua đơn tháng chưa nhận được haonf tiền từ VinPearl" | AppStore (MyVinpearl page) — 4y ago | Mr.Mango87 | Có thông báo cho khách hàng khi gặp lỗi, chậm trễ trong việc thanh toán hoàn tiền  |

| **Tổng quan (Appstore)**: Điểm trung bình 4.8 từ ~1.8K đánh giá | Appstore | - | Người dùng đánh giá cao tính năng thân thiện, ưu đãi, check-in; nhưng tồn tại nhiều đánh giá 1* liên quan đến lỗi đặt phòng và kết nối |

Nếu chưa có nguồn ngoài nhóm, ghi rõ:


## 4. Competitor / analog evidence

| App / mô hình tham khảo | Họ xử lý task này thế nào? | Pattern học được | Có áp dụng trong 1 ngày không? |
|---|---|---|---|
|  |  |  |  |

## 5. Evidence -> Insight
````text
Evidence nổi bật nhất:
- CH Play: Điểm 4.7 (≈1.8K reviews) nhưng có cụm đánh giá 1* liên quan đến lỗi đặt phòng, mất kết nối và giao dịch không hoàn tất.
- Nhiều đánh giá tích cực về tính năng check-in, ưu đãi và trải nghiệm chung — nhưng các lỗi giao dịch gây mất niềm tin.

Insight:
User không chỉ gặp "lỗi đặt phòng" bề mặt.
Thật ra họ cần: xác nhận giao dịch đáng tin cậy, hướng dẫn phục hồi khi booking thất bại, và thông tin rõ ràng về trạng thái đặt.

Opportunity:
AI có thể giúp bằng cách:
- Phát hiện lỗi booking/gián đoạn và giải thích nguyên nhân theo ngôn ngữ đơn giản.
- Hướng dẫn bước phục hồi (lưu tạm thông tin, thử lại từng bước, đề xuất phương án thay thế).
- Ưu tiên trạng thái giao dịch và cảnh báo rõ khi cần can thiệp của CS.
````

## 6. Evidence đổi SPEC như thế nào?

- [ ] Đổi user chính.
- [ ] Đổi pain statement.
- [ ] Đổi build slice.
- [ ] Đổi Auto/Aug decision.
- [ ] Đổi 4 paths.
- [ ] Đổi failure mode.
- [ ] Đổi owner/test plan.

Ghi rõ 1-2 thay đổi quan trọng:

```text
Trước evidence, nhóm định: AI chỉ gợi ý 2-3 gói/ưu đãi và giải thích lựa chọn; không can thiệp vào luồng đặt.
Sau evidence, nhóm đổi thành: Giữ core là "gợi ý" nhưng bổ sung khả năng phát hiện lỗi booking, cảnh báo trạng thái kết nối, và đề xuất recovery/alternative (ví dụ: chọn ngày khác, chuyển sang đặt qua CS).
Lý do: Nhiều người dùng gặp vấn đề khi hoàn tất booking — nếu AI chỉ gợi ý mà không giúp recover, trải nghiệm vẫn dễ gây thất vọng và mất niềm tin.
```
