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