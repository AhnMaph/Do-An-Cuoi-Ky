# **About Decision Tree Pros and Cons**
> Ở trong bài báo cáo này trước hết em sẽ trình bày trước hết là về **Decision Tree** cơ sở của **Random Forest**. Mục đích là để thấy được các điểm như sau:

1. Nguyên lý hoạt động của Decision Tree
2. Tính đơn giản mà hiệu quả của Decision Tree
3. Hạn chế của Decision Tree  
## I. Nguyên lý hoạt động
> Trong bài báo cáo này em sẽ sử dụng dataset có sẵn Iris, đây là một dataset về phân loại (classification) các loài hoa.
> Để dễ dàng visualize em sẽ chỉ sử dụng 2 features và phân loại nếu cây này là cây **Iris-virginica** và **Iris-setosa**

Biểu diễn 2 features với tọa độ x là **sepal_length** và y là **petal_length**

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/0b3fed9b-0af0-4787-a63c-5c89250ed569)

Lúc này thì ta dễ dàng thấy threshold (best split) sẽ là như hình dưới:

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/d3aa6bb1-5aa9-4161-a179-413a8f584024)
