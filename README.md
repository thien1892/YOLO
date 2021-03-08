# YOLO

# Object Location:
- Từ trước, chúng ta đào tạo mô hình để xác định bức ảnh là gì (ví dụ là ô tô hay ko?), Với Object Location, ta trả lời 2 câu hỏi: Bức ảnh là gì? và cái đó ở đâu?
 <img src ='https://i.imgur.com/ykdhUBS.jpg'>

- Như vậy với location, trong phần outpot sau một mô hình CONV-Net ta thêm (bx, by, bw, bh) để xác định Object ở đâu: bx,by là điểm giữa của vật thể; bw là chiểu rộng vật thể; bh là chiều cao của vật thể.
 <img src = 'https://i.imgur.com/A27rrns.jpg'>

- Với mỗi nhãn bức ảnh (X, y), y sẽ có dạng sau, trong đó pc =0/1 trả lời câu hỏi liệu có vật thể hay ko? **Nếu không có, không quan tâm các thành phần khác**; sau pc là location của vật thể (px,py,pw,ph) và các vật thể khác; tính hàm mất mát được chia ra 2 nhánh như dưới tùy thuộc vào pc:
<img src ='https://i.imgur.com/mAbZ3ME.jpg'>

# Landmark detetion:
- Để xác định một vật thể ta xác định các điểm trên vật thể đặc trưng cho nó. Ví dụ: Xác định 1 khuôn mặt, ta muốn biết điểm chỉ khóe mắt ở đâu? điểm chỉ vùng ngoài của mặt ở đâu?...; Hoặc với 1 người ta muốn biết điểm chỉ đầu ở đâu, khuỷu tay ở đâu?... để phục vụ cho việc xem người đó đang chạy hay đi bộ,.... Do đó, output của mô hình ConvNet sẽ tùy thuộc và số điểm landmark chúng ta muốn lấy.
<img src ='https://i.imgur.com/axs7Huq.jpg'>

# Sliding object detetion:
- Để xác định 1 đối tượng trong 1 bức ảnh, ý tưởng là lấy 1 ô vuông nhỏ (xem như là cửa sổ) và đặt nó lên các vị trí của bức ảnh và áp dụng ConvNet xem có vật thể trong phần ô vuông này không?
<img src ='https://i.imgur.com/4iZ5T0W.jpg'>

- **Câu hỏi đặt ra:** Với việc đặt rất nhiều ô vuông lên bức ảnh, việc áp dụng ConvNet lên từng phần này sẽ tăng chi phí tính toán (ví dụ đặt 9 lần sẽ tăng lên 9 lần), có cách nào tối ưu hóa việc tính toán hay ko?

# Áp dụng Conv với Sliding Window
- Chuyển FC layer thành Conv layer, ví dụ với input: 14x14x3, output: 1x1x4:
<img src ='https://i.imgur.com/3uW0oal.jpg'>

- Ta thấy với mỗi phần 14x14x3 trong bức ảnh lớn 16x16x3 khi áp dụng cùng 1 mô hình ConvNet thì sẽ dùng lại các tính toán--> Khi đó ta có output sẽ là 2x2x4 sẽ tương ứng với từng phần 14x14x3 trong 16x16x3. Do đó việc áp dụng toàn bức ảnh trong 1 mô hình ConvNet sẽ cho đầu ra cung lúc mà không cần áp dụng ConvNet lên từng phần cửa số làm gia tăng chi phí tính toán!!
<img src ='https://i.imgur.com/wBpO0gH.jpg'>

# Bounding Box Prediction
- Vấn đề đặt ra là: khi ta chia bức ảnh thành 3x3 hay 19x19 thì vật thể không chỉ ở 1 cửa sổ mà có thể ở nhiều cửa sổ. --> Do đó để tối ưu hóa việc trainning --> ta gắn nhãn vật thể pc=1 ở cửa sổ mà chứa tâm của vật thể, hay nói cách khác (px, py) là 1 điểm thuộc cửa sổ --> khi đó chỉ có 1 ô cửa sổ pc=1 và các ô khác pc =0. **(Đây là một phần của thuật toán YOLO - You only look once!)**
<img src ='https://i.imgur.com/jqkkhC8.jpg'>