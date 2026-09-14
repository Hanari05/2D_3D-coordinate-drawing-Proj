# Đồ án Kỹ thuật đồ họa — Trực quan hóa 2D và 3D

Ứng dụng minh họa các nguyên lý đồ họa máy tính thông qua dựng hình 3D, phép chiếu và hoạt cảnh 2D.

Người dùng có thể nhập thông số hình học, lựa chọn phép chiếu, thay đổi góc nhìn và quan sát các đối tượng trên hệ tọa độ.

**[Mở demo](https://lanne-0402.github.io/Doan_Kythuatdohoa_N5_LanHanDiepUy/)**

> Demo được triển khai trên tài khoản của thành viên nhóm. Front-end sử dụng dịch vụ backend riêng để xử lý dữ liệu hình học và hoạt cảnh.

## Mục tiêu

* Vận dụng thuật toán hình học để tạo và biểu diễn đối tượng 3D.
* Minh họa phép chiếu từ không gian 3D lên mặt phẳng 2D.
* Thực hành vẽ, biến đổi hình học và xây dựng hoạt cảnh 2D.
* Kết hợp xử lý dữ liệu bằng Python với giao diện tương tác trên trình duyệt.

## Tính năng

### Dựng hình 3D

Hỗ trợ các đối tượng:

* Hình hộp chữ nhật.
* Hình lập phương.
* Hình trụ.
* Hình cầu.

Người dùng nhập tọa độ và kích thước để tạo hình. Dữ liệu hình học được biểu diễn bằng:

* **Vertices:** Các đỉnh.
* **Edges:** Các cạnh.
* **Faces:** Các mặt.

### Phép chiếu và góc nhìn

* Phép chiếu **Cabinet**, hệ số co chiều sâu bằng `1/2`.
* Phép chiếu **Cavalier**, hệ số co chiều sâu bằng `1`.
* Hiển thị trục tọa độ và lưới.
* Thay đổi góc nhìn bằng thao tác kéo chuột.
* Phóng to, thu nhỏ và đặt lại góc nhìn.
* Phân biệt cạnh thấy và cạnh khuất.

### Hoạt cảnh 2D

* Hoạt cảnh Pacman.
* Hoạt cảnh chú vịt.
* Các thành phần vẽ hình và biến đổi hình học.
* Hiển thị thông số, tọa độ đối tượng theo hoạt cảnh.

## Công nghệ

| Thành phần                  | Công nghệ             |
| --------------------------- | --------------------- |
| Xử lý hình học và hoạt cảnh | Python                |
| Web API                     | Flask, Flask-CORS     |
| Xử lý tính toán và hình ảnh | NumPy, Pillow, OpenCV |
| Giao diện                   | HTML, CSS, JavaScript |
| Hiển thị đồ họa             | HTML Canvas           |
| Triển khai front-end        | GitHub Pages          |
| Backend của bản demo        | Render                |

## Kiến trúc

Front-end tiếp nhận thông số do người dùng nhập và gửi yêu cầu đến backend. Backend tạo dữ liệu hình học, sau đó trả kết quả để giao diện thực hiện phép chiếu và hiển thị trên Canvas.

Đối với hoạt cảnh 2D, backend cung cấp nội dung hình ảnh và dữ liệu trạng thái để giao diện hiển thị.

| Đường dẫn               | Vai trò                            |
| ----------------------- | ---------------------------------- |
| `project.py`            | API tích hợp phần 2D và 3D         |
| `requirements.txt`      | Các thư viện Python                |
| `2D_project/`           | Engine vẽ và các hoạt cảnh 2D      |
| `3D_project/core/`      | Dữ liệu hình học và phép chiếu     |
| `3D_project/static/`    | Tài nguyên giao diện của module 3D |
| `3D_project/templates/` | Template của module 3D             |
| `site/`                 | Front-end dùng cho triển khai web  |
| `dist/`                 | Bản đóng gói có trong repository   |

## Sử dụng demo

1. Mở [trang demo](https://lanne-0402.github.io/Doan_Kythuatdohoa_N5_LanHanDiepUy/).
2. Chọn loại hình muốn dựng.
3. Nhập tọa độ và kích thước.
4. Chọn phép chiếu Cabinet hoặc Cavalier.
5. Nhấn **Vẽ**.
6. Kéo chuột để thay đổi góc nhìn hoặc dùng con lăn để zoom.
7. Chuyển sang phần hoạt cảnh 2D để xem Pacman hoặc chú vịt.

Bản web cần kết nối đến backend. Nếu dịch vụ backend không khả dụng, các chức năng tạo hình và hoạt cảnh phụ thuộc API sẽ không hoạt động đầy đủ.

## Chạy môi trường phát triển

### 1. Clone repository

```bash
git clone https://github.com/Hanari05/2D_3D-coordinate-drawing-Proj.git
cd 2D_3D-coordinate-drawing-Proj
```

### 2. Tạo môi trường Python

```bash
python -m venv .venv
```

Kích hoạt môi trường trên Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Trên macOS/Linux:

```bash
source .venv/bin/activate
```

Cài đặt thư viện:

```bash
python -m pip install -r requirements.txt
```

### 3. Chạy backend

```bash
python project.py
```

Backend chạy tại `http://127.0.0.1:5000`.

Đường dẫn `/` hiện trả về thông tin trạng thái API, không phải giao diện ứng dụng.

### 4. Kết nối front-end với backend local

Trong `site/static/script.js`, đổi địa chỉ API thành:

```javascript
const API_BASE_URL = "http://127.0.0.1:5000";
```

Nếu chạy front-end tại `http://localhost:8000`, thêm origin này vào danh sách `origins` trong cấu hình CORS của `project.py`:

```python
"http://localhost:8000",
```

Khởi động lại backend sau khi cập nhật cấu hình.

Mở terminal thứ hai tại thư mục gốc repository và chạy:

```bash
python -m http.server 8000 --directory site
```

Truy cập `http://localhost:8000` để mở giao diện.

> Địa chỉ và cổng truy cập front-end phải khớp với origin được khai báo trong CORS. Khi triển khai, cấu hình lại API URL và danh sách origin cho môi trường tương ứng.

## Nhóm thực hiện

* Nông Thị Hồng Lan.
* Nguyễn Ngọc Gia Hân.
* Bảo Diệp.
* Thạch Gia Uy.

**Phần phụ trách của Nguyễn Ngọc Gia Hân:** Phát triển module 3D, vận dụng thuật toán và thiết kế phần trực quan hóa trước khi tích hợp với phần 2D của nhóm.

## Phạm vi và giới hạn

* Dự án phục vụ học tập và minh họa nguyên lý đồ họa máy tính.
* Các đối tượng 3D tập trung vào hình cơ bản và biểu diễn hình học; không phải công cụ modeling chuyên nghiệp.
* Bản demo phụ thuộc vào kết nối giữa front-end và backend.
* Bản đóng gói trong `dist/` có thể khác với phiên bản mã nguồn mới nhất.

## Hướng phát triển

* [ ] Đưa cấu hình API URL ra khỏi mã nguồn giao diện.
* [ ] Bổ sung kiểm thử cho dữ liệu hình học và API.
* [ ] Hoàn thiện thông báo lỗi khi backend không khả dụng.
* [ ] Bổ sung ảnh minh họa và video thao tác.
* [ ] Chuẩn hóa quy trình đóng gói và phát hành phiên bản.

## Tài nguyên bên thứ ba

Các thư viện, font và hình ảnh sử dụng trong dự án tuân theo điều khoản của tác giả tương ứng.

Khi tái sử dụng, cần kiểm tra license của từng thành phần và giữ lại thông tin ghi nguồn theo yêu cầu.
