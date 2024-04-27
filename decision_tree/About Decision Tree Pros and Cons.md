# **About Decision Tree Pros and Cons**
> Ở trong bài báo cáo này trước hết em sẽ trình bày trước hết là về **Decision Tree** cơ sở của **Random Forest**. Mục đích là để thấy được các điểm như sau:

1. Nguyên lý hoạt động của Decision Tree
2. Tính đơn giản mà hiệu quả của Decision Tree
3. Hạn chế của Decision Tree  
## I. Nguyên lý hoạt động
>Em sẽ sử dụng dataset có sẵn Iris, đây là một dataset về phân loại (classification) các loài hoa.
> Để dễ dàng visualize em sẽ chỉ sử dụng 2 features và phân loại nếu cây này là cây **Iris-virginica** và **Iris-setosa**
#### 1. Ngưỡng (Threshold)
- Ta sẽ phân loại 2 loại cây với các samples đã biết trước là thông tin về 2 features **sepal_length** và **petal_length**. Decision tree sẽ dựa vào samples có sẵn để tìm ra cách phân loại dựa vào *ngưỡng* hay threshold tốt nhất. Minh họa ở các ví dụ ở dưới đây: 
 
Biểu diễn 2 features với tọa độ x là **sepal_length** và y là **petal_length**

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/0b3fed9b-0af0-4787-a63c-5c89250ed569)

Lúc này thì ta dễ dàng thấy ngưỡng (threshold) tốt nhất sẽ là như hình dưới:

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/d3aa6bb1-5aa9-4161-a179-413a8f584024)

    Tương tự với các features khác 

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/64559ad3-a8c4-47ba-96f2-24cdb1684f7e)



#### *Ngưỡng* nó thực sự hoạt động như thế nào?

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/f2297757-a840-40eb-a09c-95cc23d612d7)

  Các *decision node* sẽ là các *ngưỡng* (threshold) giúp ta phân loại các target. Nếu thõa mãn điều kiện chúng ta sẽ phân loại là *con* bên phải của nó, ngược lại là con bên trái. Nếu *con* là một *leaf node* thì nó đã được phân loại. 

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/dafa58de-4b59-4c3f-819d-474be9f94938)

#### **Nhận xét**
Ta nhận thấy decision tree sẽ tìm các ngưỡng tốt nhất để phân loại features, vậy dựa vào đâu mà máy tính biết được đó là ngưỡng tốt nhất ?

#### 2. Gini index/Entropy and Infomation gain

Entropy là thước đo sự hỗn loạn hoặc tạp chất trong một nút. Một nút chẳng hạn như có 2 *Đúng* và 2 *Sai* sẽ được coi là có Entropy cao hơn một nút chỉ *Đúng* hoặc chỉ *Sai*. Mức tối đa của entropy hoặc hỗn loạn là 1 và entropy tối thiểu là 0.

Một nút (lá) trong tất cả trường hợp đều thuộc một target thì sẽ có entropy bằng 0. Trong khi đó, entropy cho một nút trong đó có các tất cả target và được chia đều sẽ là 1.

Entropy tính bằng công thức: 

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/e1613164-0c5b-45c4-ae78-f9754f694fdc)

    Trong đó pi là xác suất chọn ngẫu nhiên một loại cây i. 

Vì vậy, entropy ban đầu của nút phụ thuộc vào xác suất nhận một feature trong các samples. Ví dụ trong tập dữ liệu, có 10 cây cây Iris-virginica và 20 cây Iris-setosa vậy xác suất p( Iris-virginica) trong công thức entropy tương ứng là:
  p( Iris-virginica) = 10/20 =0.5
Vậy làm sao để dựa vào entropy để xác định chúng ta có nên split tại vị trí nào đó hay không. Chúng ta sẽ sử dụng công thức tính Information Gain để tính xem ở ngưỡng (threshold) đó chúng ta có được bao nhiêu information cho một target feature. 

![image](https://github.com/AhnMaph/Do-An-Cuoi-Ky/assets/157342518/3aa5e51a-e1e4-4c44-b43a-0020b52712ec)

