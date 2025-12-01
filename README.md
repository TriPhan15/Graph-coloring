#  Graph Coloring Algorithm 

> **Môn học:** Trí tuệ Nhân tạo (Artificial Intelligence)  
> **Sinh viên:** [Phan Thanh Trí]  
> **MSSV:** [2001230977]

##  Giới thiệu (Overview)
Dự án này cài đặt **Thuật toán Tô màu Đồ thị (Graph Coloring Algorithm)** sử dụng chiến lược tham lam (Greedy) kết hợp với **kỹ thuật giảm bậc động (Dynamic Degree Reduction)**.
Mục tiêu là tô màu các đỉnh của đồ thị sao cho không có hai đỉnh kề nhau nào cùng màu, đồng thời sử dụng ít màu nhất có thể.
Dự án bao gồm tính năng đọc dữ liệu từ file văn bản và trực quan hóa kết quả đồ thị bằng hình ảnh.

##  Tính năng (Features)
* **Đọc dữ liệu linh hoạt:** Hỗ trợ đọc ma trận kề từ file `.txt`.
* **Thuật toán tối ưu:**
    * Ưu tiên chọn đỉnh có bậc (degree) cao nhất.
    * Cập nhật lại bậc của các đỉnh kề sau khi một đỉnh được tô màu (Logic giảm bậc).
* **Trực quan hóa (Visualization):** Vẽ đồ thị minh họa kết quả tô màu bằng thư viện `NetworkX` và `Matplotlib`.
* **Chi tiết từng bước:** In ra log quá trình chọn đỉnh, tô màu và giảm bậc để dễ dàng theo dõi (Trace log).

##  Công nghệ sử dụng (Tech Stack)
* **Ngôn ngữ:** Python 3.x
* **Thư viện:**
    * `networkx`: Xử lý và vẽ cấu trúc đồ thị.
    * `matplotlib`: Hiển thị hình ảnh đồ họa.
    * `numpy`: Xử lý ma trận.

##  Cấu trúc file Input (`input.txt`)
File đầu vào là một **Ma trận kề (Adjacency Matrix)** đại diện cho đồ thị.
* `1`: Có đường nối giữa hai đỉnh.
* `0`: Không có đường nối.
**Ví dụ:**
```text
0 1 1 0 1 0
1 0 1 1 0 1
1 1 0 1 1 0
0 1 1 0 0 1
1 0 1 0 0 1
0 1 0 1 1 0
