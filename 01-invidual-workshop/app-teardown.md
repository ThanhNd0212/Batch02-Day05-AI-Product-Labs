# Workshop — Mổ App AI Thật

Nguyễn Đức Thành


## 1. Chọn một sản phẩm để dùng thử

| Sản phẩm | AI feature | Cách truy cập |
|---|---|---|
| MoMo — Moni | Trợ thủ tài chính, phân tích chi tiêu, chatbot | App MoMo |

## 2. Dùng thử: promise vs reality

Ghi nhanh:

1. Product đã hứa sẽ trả lời các câu hỏi đóng vai trò như một chuyên viên hỗ trợ và phân tích tài chính trong phạm vi ứng dụng MoMo
- Ghi chép chi tiêu theo từng nhóm ăn uống
- Tổng hợp báo cáo chi tiêu theo ngày, tuần, tháng hoặc theo nhóm
- Phân tích xu hướng chi tiêu
- Đưa ra mẹo để tích kiệm
- Giải thích các khái niệm tài chính một cách cơ bản và dễ hiểu
- Tìm khuyến mãi phù hợp
2. User được hứa sẽ giúp là bất kỳ ai dùng MoMo, đặc biệt là những người muốn quản lý tài chính cá nhân tốt hơn.
3. Kỳ vọng AI sẽ giúp người dùng hiểu rõ hơn về tình hình tài chính của họ, đưa ra các phân tích chi tiêu hữu ích, và cung cấp các mẹo để tiết kiệm tiền.
4. Khi dùng, tôi phát hiện ra nhiều điểm gãy như sau
- AI có thể duy trì context của tin nhắn trước nhưng không ổn định 
![tính liền mạch moni 1](01-invidual-workshop\tính liền mạch Moni 1.jpg)
![tính liền mạch moni 2](01-invidual-workshop\tính liền mạch Moni 2.jpg)
input 1: Truy xuất dòng tiền của tôi trong 4 tuần gần nhất
output1: Moni đã trả về thống kê tống số giao dịch, tổng chi và trung bình mỗi ngày theo từng tuần. Đồng thời gợi ý người dùng có muốn xem chi tiết từng giao dịch không
input 2: hãy cho tôi biết chi tiết giao dịch
output 2: Moni trả về chi tiết giao dịch trong 3 ngày gần nhất
--> AI trả về thông tin trong 3 ngày gần nhất thay vì 4 tuần theo như context từ  tin nhắn trước. 

-AI khôg nhất quán trong việc trả lời cùng 1 câu hỏi
![lần hỏi 1 - Trả lời không có dữ liệu nhóm chi tiêu cụ thể](01-invidual-workshop\không nhất quán 1.jpg)
![lần hỏi 2 - Có dữ liệu về nhóm chi tiêu giải trí](01-invidual-workshop\không nhất quán 2.jpg)

## 3. Vẽ 4 paths
Từ hai lỗi trên và các cuộc hội thoại đã trò chuyện với Moni, tôi có thể vẽ 4 paths như sau:
| Path | Câu hỏi cần trả lời |
|---|---|
| Happy | AI đúng và tự tin trong việc trả lời các định nghĩa tài chính và chính sách của Momo đơn giản, người dùng thấy được thông tin được tổng hợp, thỏa mãn được câu hỏi  |
| Low-confidence | Khi AI không chắc, AI hỏi lại câu hỏi và hướng dẫn người dùng hỏi chuyên viên hỗ trợ kĩ thuật  |
| Failure | Khi AI sai, user đưa feedback trực tiếp trong cuộc trò chuyện qua mục đánh giá tin nhắn gần nhất có hữu ích hay không |
| Correction | Khi user sửa, correction được ghi nhận nhưng không thể áp dụng đúng cho cuộc trò chuyện sau, AI vẫn trả lời thông tin sai như cũ |

## 4. Viết finding thành quyết định

```text
Khi user yêu cầu truy xuất dòng tiền trong 4 tuần gần nhất, tin nhắn sau yêu cầu muốn biết chi tiết giao dịch 
AI/product không nhớ được context của câu trước là 4 tuần, dẫn đến câu sau trả lời thông tin của 3 ngày gần nhất theo ý hiểu của AI
hậu quả là người dùng nhận được thiếu thông tin, phải gửi lại nhiều lần.
Lỗi thuộc layer intent & Context management khi không ghi nhớ được context của cuộc trò chuyện.
Nên sửa bằng low-confidence path: khi AI không chắc về context, AI sẽ hỏi lại để xác nhận khoảng thời gian người dùng muốn truy xuất.
Nên cập nhật quản lý trạng thái trong frame work để bắt buộc kiểm tra tham số thời gian trong cuộc trò chuyện 
```
## 5. Sketch as-is / to-be

## Sơ đồ So sánh Luồng Hội Thoại (As-is vs To-be)

| LUỒNG HIỆN TẠI (As-is) | LUỒNG ĐỀ XUẤT (To-be) |
| :--- | :--- |
| **[User]** Yêu cầu: "Truy xuất dòng tiền 4 tuần gần nhất" | **[User]** Yêu cầu: "Truy xuất dòng tiền 4 tuần gần nhất" |
| ⬇️ | ⬇️ |
| **[AI]** Trả về tổng quan 4 tuần.<br>*(Xóa/Không lưu thuộc tính thời gian vào State)* | **[AI]** Trả về tổng quan 4 tuần + **[UX] Lưu trạng thái `thời gian = 4 tuần` vào Chat State và hiển thị nhãn/nút gợi ý trên màn hình**. |
| ⬇️ | ⬇️ |
| **[User]** Yêu cầu: "Hãy cho tôi biết chi tiết giao dịch" | **[User]** Yêu cầu: "Hãy cho tôi biết chi tiết giao dịch" *(hoặc bấm nút gợi ý)* |
| ⬇️ | ⬇️ |
| **[AI (Intent Layer)]** Không nhận diện được từ thay thế "chi tiết giao dịch của chúng".<br>⚠️ **[ĐIỂM GÃY]:** Tự động áp dụng giá trị mặc định hệ thống (3 ngày gần nhất). | **[AI (Intent Layer)]** Trích xuất tham số: phát hiện từ khóa "chi tiết". Kiểm tra Chat State thấy có sẵn `thời gian = 4 tuần`. |
| ⬇️ | ⬇️ |
| **[AI]** Gọi tool lấy dữ liệu từ ngày 01-06 đến 03-06. | ❓ **[LÚC AI KHÔNG CHẮC CHẮN]:**<br>Nếu hệ thống phân vân giữa 4 tuần và 3 ngày, AI sẽ đưa ra câu hỏi xác nhận (Fallback Prompt): *"Bạn muốn xem chi tiết của 4 tuần vừa truy xuất hay 3 ngày gần đây?"* |
| ⬇️ | ⬇️ |
| 🛑 **[HẬU QUẢ]:** Trả về thông báo trống (01-06 đến 03-06 không có giao dịch). User nhận thiếu thông tin, phải gõ đi gõ lại. | **[AI]** Kế thừa chính xác tham số, gọi tool lấy dữ liệu chi tiết của toàn bộ 4 tuần. |
| ⬇️ | ⬇️ |
| 🔄 **[USER RECOVER]:**<br>Người dùng buộc phải gõ lại từ đầu một câu lệnh thủ công, đầy đủ thực thể: *"Hãy cho tôi biết chi tiết giao dịch của 4 tuần gần nhất"* để ép AI chạy đúng hướng. | ⚡ **[USER RECOVER (Nếu AI vẫn đoán sai)]:**<br>Nếu AI tự ý lấy 3 ngày, giao diện hiển thị ngay nút cứu cánh: `[Xem chi tiết của 4 tuần trước]`. Người dùng chỉ cần bấm nút để sửa sai cho AI ngay lập tức mà không cần gõ lại. |

