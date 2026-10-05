# Dự án nghiên cứu: Hướng dẫn sử dụng Sympy để giải các bài tập liên quan Cấp số nhân

## 📌 1. Thông Tin Chung
* **Chủ đề:** Ứng dụng thư viện Sympy trong Python để tự động hóa và giải quyết các bài toán về Cấp số nhân.
* **Mục tiêu:** Cung cấp hướng dẫn chi tiết, từ cơ sở lý thuyết đến thực hành mã hóa, giúp người học dùng Sympy để tìm số hạng tổng quát, tính tổng, giải hệ phương trình tìm công bội, số hạng đầu, tính giới hạn và mô hình hóa bài toán thực tế.
* **Định dạng đầu ra:** Tài liệu hướng dẫn dạng LaTeX (PDF), Markdown, Jupyter Notebook kèm mã nguồn Python minh họa có thể chạy trực tiếp.

---

## 🗺️ 2. Đề Cương Chi Tiết Dự Án (Cập nhật theo `main.tex`)

> **Kim chỉ nam:** "Tự động hóa các tính toán đại số với Sympy không chỉ giúp tiết kiệm thời gian, hạn chế sai sót tính toán thủ công mà còn mở ra cách tiếp cận toán học hiện đại thông qua lăng kính lập trình."

### Mở Đầu: Đặt Vấn Đề & Cơ Sở Lý Thuyết
* **0.1. Nhắc lại lý thuyết Cấp số nhân:** Khái niệm $u_1, q, u_n, S_n$, tính chất ba số hạng liên tiếp, và cấp số nhân lùi vô hạn.
* **0.2. SymPy là gì? Vì sao dùng SymPy để giải toán?** So sánh tính toán số học (numeric) và ký hiệu (symbolic). Ưu điểm của CAS (Computer Algebra System).
* **0.3. Lộ trình tài liệu:** Giới thiệu tổng quan 9 chương và độ khó tăng dần.

### Chương 1: Cài đặt môi trường và khai báo biến ký hiệu
* **1.1. Cài đặt môi trường làm việc:** Cài đặt `sympy`, `jupyter`, `matplotlib` qua pip.
* **1.2. Nạp thư viện và quy ước đặt tên:** Quy ước `import sympy as sp`, bảng ánh xạ biến Toán học sang Python.
* **1.3. Khai báo biến ký hiệu với `symbols()`:** Các cách khai báo, ràng buộc miền giá trị (`real=True`, `positive=True`).
* **1.4. Định dạng hiển thị đẹp với `init_printing()`**.
* **1.5. Thiết lập công thức CSN dưới dạng SymPy:** Biểu thức `un_formula` và `Sn_formula`.

### Chương 2: Các lệnh SymPy cơ bản
* **2.1. Thay giá trị -- `.subs()`:** Thay số cho nhiều biến cùng lúc bằng dictionary.
* **2.2. Chuyển sang số thực -- `.evalf()`:** Ép kiểu số thập phân, độ chính xác tùy chỉnh.
* **2.3. Rút gọn, khai triển, phân tích nhân tử:** `simplify()`, `expand()`, `factor()`.
* **2.4. Phát biểu phương trình -- `Eq()`:** Phân biệt `==` trong Python và `sp.Eq()` trong SymPy.
* **2.5. Giải phương trình -- `solve()`**.

### Chương 3: Giải các dạng toán Cấp số nhân cơ bản
* **3.1. Dạng 1 -- Tìm số hạng thứ $n$ khi biết $u_1, q$:** Áp dụng `.subs()`.
* **3.2. Dạng 2 -- Tính tổng $S_n$ khi biết $u_1, q$:** Áp dụng `.subs()` và lưu ý về phân số chính xác.
* **3.3. Ví dụ tổng hợp -- kết quả dạng phân số:** Xử lý số liệu không nguyên.
* **3.4. Trường hợp đặc biệt $q = 1$:** Xử lý lỗi chia cho 0 (ZeroDivisionError) bằng hàm `tinh_Sn` tùy chỉnh.

### Chương 4: Dạng toán nâng cao -- Giải hệ phương trình tìm $u_1, q$
* **4.1. Bài toán đặt vấn đề:** Tìm $u_1, q$ từ mối liên hệ giữa các số hạng.
* **4.2. Thiết lập hệ phương trình:** Tạo các biểu thức `u2, u3, u4, u5` và `sp.Eq()`.
* **4.3. Giải hệ với `solve()`:** Trích xuất danh sách bộ nghiệm.
* **4.4. Giải hệ với `nonlinsolve()`:** Xử lý hệ phi tuyến.
* **4.5. Lọc nghiệm hợp lệ -- loại nghiệm phức:** Sử dụng list comprehension và thuộc tính `.is_real`.
* **4.6. Ví dụ phức tạp hơn -- ba số hạng có tích và tổng.**
* **4.7. Rút gọn nghiệm phức tạp với `simplify()`**.

### Chương 5: Dạng toán 3 -- Cấp số nhân lùi vô hạn và giới hạn
* **5.1. Nhắc lại lý thuyết.**
* **5.2. Tính giới hạn bằng `limit()`:** Xử lý kết quả `zoo` khi SymPy chưa biết điều kiện $|q| < 1$.
* **5.3. Hàm tổng quát tính tổng CSN lùi vô hạn:** Viết hàm kiểm tra điều kiện hội tụ.
* **5.4. Ví dụ tổng hợp -- bài toán chữ.**

### Chương 6: Ứng dụng thực tế
* **6.1. Bài toán lãi suất kép:** Mô hình $T_n = A(1+r)^n$.
* **6.2. So sánh lãi đơn và lãi kép.**
* **6.3. Bài toán tăng trưởng vi khuẩn:** So sánh hai tốc độ tăng trưởng.
* **6.4. Bài toán dân số:** Dự báo dân số với tỉ lệ tăng phần trăm.

### Chương 7: Trực quan hóa với Matplotlib
* **7.1. Vẽ đồ thị so sánh các cấp số nhân:** Sử dụng `sp.lambdify` để chuyển biểu thức ký hiệu thành hàm numpy.
* **7.2. Đồ thị hàm mũ liên tục và dãy rời rạc:** So sánh trực quan.

### Chương 8: Đóng gói thành thư viện -- từ Notebook đến `.py`
* **8.1. Module `solver.py` hoàn chỉnh:** Đóng gói các hàm `tinh_un`, `tinh_Sn`, `tong_lui_vo_han`, `giai_he_tim_u1_q`.
* **8.2. File kiểm thử `test_solver.py`:** Viết các unit test cơ bản để kiểm tra logic.

### Chương 9: Kết luận
* **Tổng kết hành trình:** Điểm lại các cột mốc kiến thức.
* **Đánh giá hiệu quả:** Giá trị của SymPy trong giải toán.
* **Lưu ý và hạn chế:** Nghiệm phức, $q=1$, điều kiện $|q|<1$, `sp.Rational()`.
* **Hướng mở rộng:** CLI với `argparse`, Web app với `Streamlit`, xuất LaTeX/PDF.

### Phụ Lục (Appendices)
* **Phụ lục A:** Bảng tra cứu nhanh các lệnh SymPy.
* **Phụ lục B:** Một số lỗi thường gặp và cách khắc phục.
* **Phụ lục C:** Bài tập tổng hợp (Dạng cơ bản, trung bình, nâng cao).

---

## 📈 3. Kế Hoạch & Tiến Độ Thực Hiện

* **[Ngày 1-4]:** Thu thập lý thuyết CSN, cài đặt môi trường, viết khung tài liệu (Mở đầu + Chương 1, 2).
* **[Ngày 5-9]:** Lập trình các đoạn mã Sympy cơ bản (Chương 3, 4). Xử lý hệ phương trình và lọc nghiệm.
* **[Ngày 10-15]:** Xử lý các bài toán nâng cao (Chương 5, 6): Cấp số nhân lùi vô hạn, lãi suất, vi khuẩn.
* **[Ngày 16-19]:** Kết hợp `matplotlib` để vẽ biểu đồ (Chương 7), đóng gói module `solver.py` (Chương 8), viết Phụ lục.
* **[Ngày 20-21]:** Rà soát lỗi logic, đối chiếu kết quả Sympy với đáp án tính tay, tinh chỉnh định dạng LaTeX và hoàn tất dự án.

---

## 📚 4. Tài Liệu Tham Khảo (Dự Kiến)
1. Sách giáo khoa Đại số và Giải tích (Chuyên đề Dãy số - Cấp số nhân).
2. Tài liệu hướng dẫn sử dụng chính thức của Sympy (Sympy Official Documentation).
3. Tài liệu chính thức của Matplotlib và Jupyter Notebook.
4. Các nguồn bài tập Toán học ứng dụng trực tuyến.

---

## 🛠️ 5. Cấu Trúc Kho Lưu Trữ
* `/`: Bản thảo nội dung lý thuyết và hướng dẫn dạng `.md` và `.pdf` (bao gồm file `main.tex`).
* `/notebooks`: Các file Jupyter Notebook (`.ipynb`) chứa mã nguồn hướng dẫn từng bước và kết quả chạy thử.
* `/scripts`: File Python chứa các hàm giải toán cấp số nhân được đóng gói sẵn (`geometric_progression_solver.py` và `test_solver.py`).
* `/images`: Các biểu đồ trực quan hóa tốc độ tăng trưởng của cấp số nhân lưu dưới dạng `.png` hoặc `.jpg`.
