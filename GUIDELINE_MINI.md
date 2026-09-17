# Mini guideline - nhóm: ______  |  người gán: Hoàng Tiến Dũng  |  ngày: 16/09/2026

> Điền file này **trong lúc** gán nhãn, không phải sau khi xong. Mỗi lần bạn dừng lại
> hơn 10 giây để phân vân, đó là một dòng phải ghi vào đây.

## 1. Luật bắt buộc (đã thống nhất cả lớp - không sửa)

- Bộ 17 điểm COCO, đúng tên, đúng thứ tự. Lấy từ file `.SVG` chung.
- Mọi người trong ảnh đều có **đủ 17 điểm**. Điểm không dùng được thì gắn cờ, không xoá.
- Trái/phải tính theo **cơ thể người**, không theo bức ảnh.
- Bị che, còn trong khung -> `v = 1`, **vẫn đặt chấm** ở vị trí ước lượng.
- Ra ngoài mép ảnh -> `v = 0`, **không** đặt chấm.
- Không dùng `Hidden` (`h`) - nó không được lưu vào file.

## 2. Luật của nhóm bạn (phải điền)

| Tình huống | Luật nhóm bạn chọn | Vì sao |
| --- | --- | --- |
| Hông của người mặc quần áo dài |vẫn đánh nhưng để ở loại đã bị che khuất | không giống như mặc quần có thể xác định bằng cạp quần thì áo dài sẽ dài tuần xuống đến chân|
| Tai bị tóc hoặc mũ bảo hiểm che một phần | vẫn đánh như thường  | vị trí tai của mỗi người ở trên đầu gần như tương đương nhau không có sự khác biệt nhiều |
| Người bị cắt ở mép ảnh (chỉ thấy từ hông trở lên) | để toàn bộ điểm đầu gối xuống ở chế độ outside |vì nó không còn thuộc khung hình đấy nữa |
| Cổ tay nằm sau tay lái / sau thân mình |vẫn đánh như ình thường và để chế độ bị che | về sau muốn huấn luyện mô hình thì model luôn phải track theo cái bàn tay xem nó đang làm gì  |
| Hai người chồng lên nhau |  | |
| Người nhỏ đến mức nào thì không gán nữa |không đủ để khác định các khớp xương | không thể đánh chính xác các khớp xương và nếu cố tình đánh sẽ thành 1 nhiễu trong việc huấn luyện mode sau này|

Với mỗi luật, chèn **một ảnh mẫu** (screenshot từ CVAT) thay vì chỉ viết một câu.x
Slide 12 nói rõ: khớp không có bề mặt nhìn thấy được thì phải có ảnh mẫu, không phải
một câu văn chung chung.

## 3. Ba ca mơ hồ đã gặp (bắt buộc, ghi ít nhất 3)

### Ca 1 - ảnh `train_04`, người thứ `2`, khớp `Hip`

- Mơ hồ ở chỗ nào:không thể xác định được HIP đã ra khỏi khung hình hay chưa
- Bạn quyết thế nào:vẫn đánh và để nó sâu nhất có thể
- Vì sao:Vẫn còn phần thân và hướng cơ thể để ước lượng vị trí của HIP; nếu bỏ ngay thì có thể làm mất thông tin về cấu trúc cơ thể. Điểm được đặt theo vị trí ước lượng thay vì đặt tùy ý.
- Nếu người khác quyết ngược lại thì model học sai cái gì:Nếu gán outside/v=0, model có thể học rằng trong tư thế tương tự HIP không cần xuất hiện hoặc không có thông tin vị trí, làm giảm khả năng dự đoán HIP khi phần thân dưới bị che hoặc nằm ngoài khung hình.

### Ca 2 - ảnh `train-11`, người thứ `1`, khớp `ankle`

- Mơ hồ ở chỗ nào: không biết người trong ảnh thu  chân như nào 
- Bạn quyết thế nào:bỏ khóp đó đi cho vào outside
- Vì sao:vị trí ankle không có đủ thông tin để xác định chính xác, nếu cố đặt điểm sẽ dễ đặt sai vị trí thật của khớp.
- Nếu người khác quyết ngược lại thì model học sai cái gì:model có thể học vị trí ankle ở một vị trí không chính xác, dẫn đến khi gặp tư thế tương tự model dự đoán ankle sai vị trí.

### Ca 3 - ảnh `______`, người thứ `___`, khớp `______`

- Mơ hồ ở chỗ nào:chân và đầu gối của người bị con mèo che, nên không nhìn rõ vị trí thật của khớp right_knee.
- Bạn quyết thế nào:bỏ khớp đó đi, cho vào outside.
- Vì sao:không có đủ evidence để xác định chính xác vị trí đầu gối; đặt một điểm theo phỏng đoán có thể tạo nhãn sai.
- Nếu người khác quyết ngược lại thì model học sai cái gì:model có thể học một vị trí đầu gối không đúng với cấu trúc cơ thể, khiến khi gặp người bị vật thể che tương tự, model dự đoán right_knee lệch khỏi vị trí thực tế.

## 4. Sau khi so visibility report với bạn cùng nhóm

- Khớp lệch `%v=1` nhiều nhất: `______` (bạn `___%` / họ `___%`)
- Nguyên nhân là **guideline chưa rõ** hay **một trong hai bên gán sai**:
- Luật mới bổ sung vào mục 2 sau khi thống nhất:
