# Kế hoạch thực hiện: Hướng dẫn sử dụng Sympy giải Cấp số nhân

## Định dạng kỹ thuật

Tài liệu và mã nguồn được biên soạn bằng **Jupyter Notebook (`.ipynb`)** kết hợp với **Markdown**, vì:

-   **Tính tương tác cao:** Cho phép người học vừa đọc lý thuyết (được định dạng đẹp bằng Markdown và LaTeX) vừa chạy thử mã Python (Sympy) ngay trong cùng một file.
-   **Hỗ trợ công thức Toán học:** Markdown trong Jupyter hỗ trợ tốt MathJax/LaTeX để gõ các công thức cấp số nhân ($u_n$, $S_n$, $q$).
-   **Trực quan hóa:** Kết quả của Sympy (biểu thức toán học) được in ra dưới dạng Unicode hoặc LaTeX rất dễ nhìn. Các biểu đồ từ `matplotlib` cũng hiển thị trực tiếp (inline).
-   **Quản lý dễ dàng:** Dễ dàng xuất ra PDF hoặc HTML để chia sẻ cho những người không cài sẵn môi trường Python.

## Cấu trúc thư mục dự kiến

```text
sympy-geometric-progression/
├── docs/
│   ├── 01-ly-thuyet-cap-so-nhan.md    # Lý thuyết toán học thuần túy
│   ├── 02-huong-dan-cai-dat.md        # Hướng dẫn setup môi trường
│   └── cong-thuc-cheat-sheet.pdf      # Tóm tắt công thức
├── notebooks/
│   ├── 00-gioi-thieu-sympy.ipynb      # Làm quen với symbols và equations
│   ├── 01-tim-so-hang-va-tong.ipynb   # Dạng 1: Thế số tính toán
│   ├── 02-giai-he-phuong-trinh.ipynb  # Dạng 2: Tìm u1, q từ hệ PT
│   └── 03-ung-dung-thuc-te.ipynb      # Dạng 3: CSN lùi vô hạn & Lãi suất
├── scripts/
│   ├── geometric_progression_solver.py # File Python đóng gói sẵn các hàm
│   └── test_solver.py                 # Unit tests cho các hàm giải toán
├── images/
│   └── growth_chart_example.png       # Hình ảnh minh họa lưu trữ
├── README.md
└── PLAN.md
```

## Quy ước kỹ thuật trong Lập trình & Soạn thảo

-   **Khai báo biến:** Thống nhất sử dụng tên biến `u1`, `q`, `n`, `un`, `Sn` cho các ký hiệu toán học trong Sympy để đồng bộ với sách giáo khoa Việt Nam.
-   **Output Toán học:** Luôn sử dụng `sp.init_printing()` ở đầu mỗi Notebook để đầu ra của Sympy được định dạng dưới dạng phân số/biểu thức toán học chuẩn (LaTeX style).
-   **Đồ thị:** Các đồ thị minh họa hàm mũ/sự tăng trưởng phải có đầy đủ nhãn trục (`xlabel`, `ylabel`), tiêu đề, và chú thích (legend).
-   **Giải quyết nghiệm phức:** Khi giải phương trình bậc cao tìm $q$, hàm phải có logic lọc bỏ nghiệm phức (`sp.I`) nếu bài toán chỉ yêu cầu nghiệm thực.

## Cài đặt & Môi trường

- **Yêu cầu hệ thống**: Python 3.9+
- **Cài đặt thư viện**:
  ```bash
  pip install sympy jupyter matplotlib
  ```
- **Khởi chạy môi trường**: Tại thư mục gốc của dự án, mở terminal và chạy:
  ```bash
  jupyter notebook
  ```

## Các giai đoạn thực hiện

### Giai đoạn 0 — Chuẩn bị hạ tầng 
-   [ ] Khởi tạo cấu trúc thư mục dự án (`docs`, `notebooks`, `scripts`).
-   [ ] Viết file `README.md` định hướng dự án.
-   [ ] Tạo file `PLAN.md` theo dõi tiến độ chi tiết.
-   [ ] Thiết lập Git repository, `.gitignore` (loại bỏ `.ipynb_checkpoints`).
-   [ ] Soạn thảo bản nháp lý thuyết toán học cơ bản (`docs/01-ly-thuyet-cap-so-nhan.md`).

### Giai đoạn 1 — Nội dung cơ bản & Code khởi tạo 
-   [ ] Viết `notebooks/00-gioi-thieu-sympy.ipynb`: Khai báo `symbols`, `Eq`.
-   [ ] Viết `notebooks/01-tim-so-hang-va-tong.ipynb`: Ứng dụng `.subs()` và `.evalf()`.
-   [ ] Review mã nguồn: Đảm bảo code dễ hiểu cho người mới học Python.

### Giai đoạn 2 — Bài toán phức tạp & Ứng dụng 
-   [ ] Viết `notebooks/02-giai-he-phuong-trinh.ipynb`: Sử dụng `nonlinsolve` để giải hệ tìm $u_1, q$.
-   [ ] Viết `notebooks/03-ung-dung-thuc-te.ipynb`: Tính tổng lùi vô hạn (`sp.limit`) và bài toán lãi kép.
-   [ ] Tích hợp `matplotlib` để vẽ biểu đồ so sánh các cấp số nhân với $q$ khác nhau.

### Giai đoạn 3 — Đóng gói Script & Kiểm thử 
-   [ ] Trích xuất các đoạn code chạy tốt trong Notebook thành các hàm Python trong `scripts/geometric_progression_solver.py`.
-   [ ] Viết file test đơn giản (`test_solver.py`) đối chiếu kết quả của hàm với các bài tập có sẵn đáp án trong SGK.
-   [ ] Đổ dữ liệu và hoàn thiện các file Markdown giải thích.

### Giai đoạn 4 — Hoàn thiện xuất bản 
-   [ ] Rà soát lỗi chính tả, lỗi logic trong toàn bộ Notebooks.
-   [ ] Xuất các file Notebook ra định dạng PDF và HTML để lưu trữ tĩnh (vào thư mục `docs`).
-   [ ] Đóng gói release v1.0 trên GitHub.

## Theo dõi tiến độ từng Module

| # | Module / Notebook | Trạng thái | Đồ thị/Hình ảnh |
|---|---|---|---|
| 0 | Khởi tạo môi trường & Git | Hoàn thành | - |
| 1 | Lý thuyết Cấp số nhân cơ bản | Đang soạn thảo | - |
| 2 | Giới thiệu Sympy (00) | Đang soạn thảo | - |
| 3 | Giải dạng 1: Thay số tính tổng (01) | Chưa bắt đầu | - |
| 4 | Giải dạng 2: Hệ phương trình (02) | Chưa bắt đầu | - |
| 5 | Dạng 3: Thực tế & Lùi vô hạn (03) | Chưa bắt đầu | ✓ (Dự kiến 2 biểu đồ) |
| 6 | Đóng gói `solver.py` | Chưa bắt đầu | - |

**Quy trình trạng thái:** `Chưa bắt đầu` → `Đang soạn thảo` → `Đang test code` → `Hoàn thiện`.

## Công cụ hỗ trợ

-   **Jupyter Notebook / VS Code:** Soạn thảo code và xem trước kết quả Markdown tức thời.
-   **Git & GitHub:** Quản lý phiên bản, backup mã nguồn.
-   **Sympy Documentation:** Tra cứu cú pháp các hàm giải tích ký hiệu.

## Rủi ro cần lưu ý

-   **Đa nghiệm & Nghiệm phức:** Giải hệ phương trình phi tuyến với Sympy (`nonlinsolve`) có thể trả về các nghiệm phức hoặc biểu thức quá phức tạp chưa được rút gọn. **Giải pháp:** Cần hướng dẫn người dùng cách dùng `sp.simplify()` và lọc nghiệm thực (`.is_real`).
-   **Trường hợp $q = 1$:** Công thức $S_n$ chia cho $(1-q)$ sẽ gây lỗi ZeroDivisionError. **Giải pháp:** Cần thêm câu lệnh điều kiện `if/else` để xử lý riêng trường hợp $q=1$ trong mã nguồn.

