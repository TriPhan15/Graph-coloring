#  Graph Coloring Algorithm 

> **Môn học:** Thực hành Trí tuệ Nhân tạo (Artificial Intelligence)  
> **Sinh viên thực hiện:** Phan Thanh Trí  
> **MSSV:** 2001230977  

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![NetworkX](https://img.shields.io/badge/Library-NetworkX-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

---

##  Giới thiệu (Introduction)

Dự án này cài đặt **Thuật toán Tô màu Đồ thị (Graph Coloring)**, một bài toán kinh điển trong lớp các bài toán thỏa mãn ràng buộc (Constraint Satisfaction Problems - CSP).

Chương trình được thiết kế để tìm lời giải tô màu cho các đỉnh của đồ thị sao cho **không có hai đỉnh kề nhau nào cùng màu**, đồng thời tối ưu hóa số lượng màu sử dụng (Sắc số - Chromatic Number) dựa trên chiến lược tham lam (Greedy) kết hợp heuristic về bậc của đỉnh .

---

##  Cơ sở lý thuyết (Theoretical Basis)

### 1. Bài toán Thỏa mãn Ràng buộc (CSP)
Bài toán được định nghĩa bởi bộ 3 yếu tố $(X, D, C)$ :
* **Biến (X):** Tập hợp các đỉnh của đồ thị $V = \{v_1, v_2, ..., v_n\}$.
* **Miền giá trị (D):** Tập hợp các màu sắc có thể sử dụng.
* **Ràng buộc (C):** Nếu có cạnh nối giữa $v_i$ và $v_j$, thì $Màu(v_i) \neq Màu(v_j)$.

### 2. Giải thuật Tô màu (Dynamic Degree Heuristic)
[cite_start]Chương trình áp dụng chiến lược ưu tiên đỉnh có ràng buộc chặt nhất (Most Constrained Variable) theo các bước sau:

1.  **Chọn đỉnh:** Tại mỗi bước, chọn đỉnh có **bậc (degree) cao nhất** trong số các đỉnh chưa tô màu (ưu tiên đỉnh khó trước).
2.  **Gán màu:** Chọn màu đầu tiên hợp lệ trong danh sách màu cho đỉnh đó.
3.  **Lan truyền ràng buộc (Hạ bậc):**
    * Đỉnh vừa tô coi như loại bỏ khỏi đồ thị.
    * Giảm bậc của tất cả các đỉnh kề với đỉnh vừa tô đi 1 đơn vị.
    * Cập nhật lại miền giá trị màu cho các đỉnh kề (loại bỏ màu vừa dùng).
4.  **Lặp lại:** Quay lại bước 1 cho đến khi tất cả các đỉnh đều có màu.

---

##  Tính năng nổi bật (Key Features)

* **Google Colab Integration:** Tích hợp tính năng upload file trực tiếp, tối ưu cho môi trường chạy đám mây.
* **Input Linh hoạt:** Hỗ trợ đọc dữ liệu Ma trận kề từ file `.csv` hoặc `.txt`.
* **Robust Algorithm:** Sử dụng thuật toán tham lam động (Dynamic Greedy) giúp giảm thiểu sắc số tốt hơn so với tham lam tĩnh.
* **Visualization:** Trực quan hóa đồ thị kết quả với các nút được tô màu tương ứng, hiển thị rõ ràng các kết nối bằng thư viện `NetworkX` và `Matplotlib`.
* **Validation:** Tự động kiểm tra lại tính đúng đắn của lời giải (Verify function) để đảm bảo không vi phạm ràng buộc.

---

##  Cấu trúc mã nguồn

Mã nguồn Python bao gồm các module chính:

1.  `upload_matrix_csv()`: Xử lý upload file, làm sạch dữ liệu và chuyển đổi thành file `input.txt` chuẩn.
2.  `read_matrix()`: Đọc ma trận kề từ file văn bản vào cấu trúc list 2 chiều.
3.  `graph_coloring_algorithm()`: **Core Logic** thực hiện tô màu theo lý thuyết đã nêu.
4.  `verify_coloring()`: Hàm kiểm chứng kết quả (Test unit).
5.  `draw_graph()`: Vẽ đồ thị màu minh họa.

---

##  Hướng dẫn sử dụng (How to Run)

### Bước 1: Chuẩn bị dữ liệu
Tạo một file `.csv` hoặc `.txt` chứa ma trận kề (Adjacency Matrix).
* Số `1`: Có cạnh nối.
* Số `0`: Không có cạnh nối.
* **Lưu ý:** Không cần tiêu đề cột/hàng.

**Ví dụ (`input.csv`):**
```text
0,1,1,0,1,0
1,0,1,1,0,1
1,1,0,1,1,0
0,1,1,0,0,1
1,0,1,0,0,1
0,1,0,1,1,0
