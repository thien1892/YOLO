# YOLO

# Object Location:
- Từ trước, chúng ta đào tạo mô hình để xác định bức ảnh là gì (ví dụ là ô tô hay ko?), Với Object Location, ta trả lời 2 câu hỏi: Bức ảnh là gì? và cái đó ở đâu?
 <img src ='https://i.imgur.com/ykdhUBS.jpg'>

- Như vậy với location, trong phần outpot sau một mô hình CONV-Net ta thêm (bx, by, bw, bh) để xác định Object ở đâu: bx,by là điểm giữa của vật thể; bw là chiểu rộng vật thể; bh là chiều cao của vật thể.
 <img src = 'https://i.imgur.com/A27rrns.jpg'>

- Với mỗi nhãn bức ảnh (X, y), y sẽ có dạng sau, trong đó pc =0/1 trả lời câu hỏi liệu có vật thể hay ko? Nếu không có, không quan tâm các thành phần khác; sau pc là location của vật thể (px,py,pw,ph) và các vật thể khác:
<img src ='https://i.imgur.com/mAbZ3ME.jpg'>