
# Phân loại CIFAR-10 bằng ResNet-18

## 1. Giới thiệu

Dự án này sử dụng mô hình ResNet-18 đã được huấn luyện trước (pretrained) để phân loại các hình ảnh trong bộ dữ liệu CIFAR-10. Mục tiêu là điều chỉnh (fine-tuning) mô hình ResNet-18 cho bài toán 10 lớp của CIFAR-10 và đánh giá hiệu năng của nó.

## 2. Bộ dữ liệu

- **Dataset**: CIFAR-10
  - CIFAR-10 bao gồm 60,000 hình ảnh màu kích thước 32x32, được chia thành 10 lớp (ví dụ: T-shirt/top, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle Boot).
- Bộ dữ liệu được tải tự động thông qua `torchvision.datasets.CIFAR10`.

## 3. Cài đặt

Yêu cầu:
- Python 3.7+
- Các thư viện: PyTorch, torchvision, matplotlib, seaborn, numpy

Cài đặt các thư viện cần thiết (nếu chưa cài):
```bash
pip install torch torchvision matplotlib seaborn numpy
```

## 4. Mô hình

- **ResNet-18** được tải từ torchvision với trọng số pretrained.
- Lớp cuối cùng được thay đổi để phù hợp với 10 lớp của CIFAR-10.
- Mô hình được chuyển sang thiết bị tính toán (GPU nếu có, ngược lại CPU).

## 5. Huấn luyện

- **Dữ liệu huấn luyện** được tải từ CIFAR-10 với các biến đổi: chuyển thành tensor và chuẩn hóa.
- Sử dụng optimizer SGD với learning rate 0.001 và momentum 0.9.
- Hàm mất mát sử dụng CrossEntropyLoss.
- Vòng lặp huấn luyện được thực hiện qua nhiều epoch (trong ví dụ có chạy 2 epoch và sau đó 5 epoch huấn luyện lại) với in ra loss sau mỗi 2000 batch.

## 6. Đánh giá

- Sau khi huấn luyện, mô hình được đánh giá trên tập test của CIFAR-10.
- Độ chính xác trên tập test được tính bằng cách so sánh nhãn dự đoán với nhãn thật.
- Ngoài ra, mô hình còn được kiểm thử thông qua việc tính toán ma trận nhầm lẫn, trực quan hóa bằng heatmap.

## 7. Lưu mô hình

- Mô hình đã được lưu lại dưới dạng file `full_model.pth` trên Google Drive để có thể sử dụng lại sau này.

## 8. Cách chạy

1. **Mount Google Drive** (nếu sử dụng Google Colab):
    ```python
    from google.colab import drive
    drive.mount('/content/drive')
    ```
2. **Chạy toàn bộ Notebook**:  
   Mở file notebook và chạy các cell từ phần xử lý dữ liệu, huấn luyện đến đánh giá mô hình.
3. **Theo dõi quá trình huấn luyện**:  
   Loss được in ra sau mỗi 2000 batch và đồ thị loss theo epoch được vẽ ra để theo dõi quá trình huấn luyện.
4. **Đánh giá kết quả**:  
   Sau khi huấn luyện, độ chính xác trên tập test được in ra và một số ảnh mẫu cùng nhãn dự đoán được hiển thị.

## 9. Hướng phát triển

- Thử nghiệm với các kỹ thuật tăng cường dữ liệu (data augmentation) để cải thiện hiệu năng.
- Tinh chỉnh các siêu tham số (learning rate, momentum, số epoch, batch size) để đạt được kết quả tốt hơn.
- So sánh với các kiến trúc mạng khác (CNN, ResNet khác, VGG, v.v.).
- Áp dụng mô hình vào các bài toán phân loại hình ảnh khác.

## 10. Liên hệ

Nếu có bất kỳ thắc mắc hoặc góp ý nào, vui lòng mở issue trên GitHub hoặc liên hệ qua email: thanh.van19062004@gmail.com

```

---

### Hướng dẫn sử dụng README này

1. Tạo file `README.md` trong repository của bạn.
2. Sao chép và dán nội dung trên vào file.
3. Điều chỉnh các thông tin (ví dụ: đường dẫn, email liên hệ, tên repository) cho phù hợp với dự án của bạn.
4. Commit và push file `README.md` lên GitHub.

