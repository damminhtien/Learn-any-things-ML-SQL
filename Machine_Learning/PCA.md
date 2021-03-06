# Principal Component Analysis (PCA)
![PCA](https://chrisalbon.com/images/machine_learning_flashcards/Principal_Component_Analysis_print.png)
* PCA tức phân tích thành phần chính, là phương pháp đơn giản nhất trong các thuật toán **Dimensionality Reduction** dựa trên mô hình tuyến tính
* PCA dưa trên quan sát rằng dữ liệu thường không phân bố ngẫu nhiên trong không gian mà thường phân bố gần các đường / mặt đặc biệt nào đó.
* PCA xem xét một trường hợp đặc biệt khi các mặt đó có dạng tuyến tính là các không gian con (sub space)
* Các đơn giản nhất để giảm từ D chiều về K chiều là chỉ giữ lại K phần tử quan trọng nhất
* **Problem**: nếu các phần tử có mức tương đồng vè thông tin -> loại bỏ thông tin sẽ gây mất mát thông tin
* PCA đi tìm một hệ cơ sở mới sao cho thông tin tập trung ở một vài tọa độ và phần còn lại chỉ chứa một lượng nhỏ thông tin => **PCA sẽ tìm một hệ trực chuẩn mới để làm cơ sở**
* Các bước PCA
1. Tính vector kì vọng của toàn bộ dữ liệu (Find mean vector)
    
   <a href="https://www.codecogs.com/eqnedit.php?latex=\bar{x}&space;=&space;\frac{1}{N}\sum_{n=1}^{N}x_{n}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\bar{x}&space;=&space;\frac{1}{N}\sum_{n=1}^{N}x_{n}" title="\bar{x} = \frac{1}{N}\sum_{n=1}^{N}x_{n}" /></a>

2. Trừ mỗi điểm dữ liệu đi vector kì vọng của toàn bộ dữ liệu (Subtract mean)

   <a href="https://www.codecogs.com/eqnedit.php?latex=\hat{\mathbf{x}}_n&space;=&space;\mathbf{x}_n&space;-&space;\bar{\mathbf{x}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\hat{\mathbf{x}}_n&space;=&space;\mathbf{x}_n&space;-&space;\bar{\mathbf{x}}" title="\hat{\mathbf{x}}_n = \mathbf{x}_n - \bar{\mathbf{x}}" /></a>

3. Tính ma trận hiệp phương sai (Compute corvariance matrix)

   <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{S}&space;=&space;\frac{1}{N}\hat{\mathbf{X}}\hat{\mathbf{X}}^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{S}&space;=&space;\frac{1}{N}\hat{\mathbf{X}}\hat{\mathbf{X}}^T" title="\mathbf{S} = \frac{1}{N}\hat{\mathbf{X}}\hat{\mathbf{X}}^T" /></a>

4. Tính các trị riêng và vector riêng có norm băng 1 của ma trận naỳ, sắp xếp chúng theo thứ tự giảm dần của trị riêng (Compute eigenvalues and eigenvectors of S)
5. Chọn K vector riêng với trị riêng lớn nhất để xây dựng ma trận có các cột tạo thành một hệ trực giao. K vector này, còn được gọi là các thành phần chính (principal component) tạo thành một không gian con gần với phân bố của dữ liệu ban đầu đã chuẩn hóa (Pick K eigenvector w. Highest eigenvalues) 
6. Chiếu dữ liệu ban đầu đã chuẩn hóa xuống không gian con tìm được (Project dât to selected eigenvectors)
7. Dữ liệu mới chính là toạ độ trên không gian mới (Obtain projected points in low dimension)

   <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{Z}&space;=&space;\mathbf{U}_K^T\hat{\mathbf{X}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{Z}&space;=&space;\mathbf{U}_K^T\hat{\mathbf{X}}" title="\mathbf{Z} = \mathbf{U}_K^T\hat{\mathbf{X}}" /></a>
   
   Dữ liệu ban đầu xấp xỉ:
   
   <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}&space;\approx&space;\mathbf{U}_K\mathbf{Z}&space;&plus;&space;\bar{\mathbf{x}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}&space;\approx&space;\mathbf{U}_K\mathbf{Z}&space;&plus;&space;\bar{\mathbf{x}}" title="\mathbf{x} \approx \mathbf{U}_K\mathbf{Z} + \bar{\mathbf{x}}" /></a>

![Các bước thực hiện PCA](https://machinelearningcoban.com/assets/27_pca/pca_procedure.png)
