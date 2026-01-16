README – Công nghệ sử dụng
Trong bài này mình thử nghiệm một số thao tác xử lý ảnh cơ bản bằng Python các thư viện mình dùng gồm
OpenCV cv2 dùng để đọc ảnh, đổi màu, flip, crop, rotate, vẽ hình, ghi chữ
NumPy: hỗ trợ làm việc với ma trận ảnh
Matplotlib: hiển thị ảnh cho dễ quan sát
Ngoài ra, một số ảnh mẫu cat, lenna, baboon được tải trực tiếp bằng lệnh wget để tiện thử nghiệm

Cách hoạt động của từng phần
Đọc ảnh và hiển thị
Mình dùng cv2.imread() để đọc ảnh, sau đó chuyển BGR -> RGB vì OpenCV dùng BGR nhưng matplotlib hiển thị theo RGB
Kiểm tra copy và tham chiếu
Mình kiểm tra thử
A = baboon → A trỏ tới cùng vùng nhớ, sửa baboon thì A cũng đổi
B = baboon.copy() → bản sao độc lập, sửa ảnh gốc thì B vẫn giữ nguyên
Phần này giúp hiểu rõ cách NumPy quản lý bộ nhớ của mảng ảnh
Lật ảnh flip
Thử với
flipcode = 0: lật dọc
flipcode = 1: lật ngang
flipcode = -1: lật cả hai chiều
Dùng cv2.flip image, flipcode và xem trực quan bằng matplotlib
Quay ảnh rotate
OpenCV hỗ trợ các giá trị
cv2.ROTATE_90_CLOCKWISE
cv2.ROTATE_90_COUNTERCLOCKWISE
cv2.ROTATE_180
Mình chạy vòng lặp và hiển thị để so sánh trực tiếp với ảnh gốc
Crop ảnh
Mình cắt ảnh theo chỉ số dòng – cột
Crop trên–dưới: image[upper:lower, :, :]
Crop trái–phải: image[:, left:right, :]
Cách này dựa vào cấu trúc mảng NumPy height width channels
Làm đen một vùng ảnh
Tạo bản sao ảnh rồi gán vùng [upper:lower, left:right, :] = 0
Cách làm đơn giản nhưng rất trực quan về việc thao tác pixel.
Vẽ hình chữ nhật và viết chữ
Dùng
cv2.rectangle() để đánh dấu khung vùng crop
cv2.putText() để thêm chữ vào ảnh
Phần này cho thấy OpenCV xử lý các overlay rất nhanh gọn

Kết quả thu được
Sau khi chạy toàn bộ notebook
Mình quan sát được sự khác nhau giữa tham chiếu và copy ảnh trong NumPy
Thực hành được các thao tác cơ bản của OpenCV: flip rotate crop draw putText
Nhìn trực quan được từng bước ảnh thay đổi qua matplotlib
Hiểu rõ hơn cách ảnh được biểu diễn dưới dạng ma trận và cách truy cập pixel
Toàn bộ quá trình giống như thử nghiệm từng tính năng nhỏ của OpenCV để làm quen xem ảnh thay đổi thế nào, từ đó hình thành nền tảng cho các kỹ thuật phức tạp hơn như augmentation filtering hay object detection sau này