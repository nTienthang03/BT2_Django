## BÀI TẬP 2

### Thông tin sinh viên
- Họ và tên: Nguyễn Tiến Thắng  
- MSSV: K225480106058  
- Lớp: K58KTP  

---

# Đề bài
# TỔ CHỨC CSDL CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ

- Viết tay sơ đồ CSDL ra giấy
  
<img width="594" height="763" alt="image" src="https://github.com/user-attachments/assets/3e974854-1972-469e-baf5-f1f6651087fa" />

- Dùng điện thoại chụp lại
- Upload ảnh lên GitHub
- Nội dung dựa trên các nghiệp vụ đã học trên lớp

---

# SỬ DỤNG DOCKER TRÊN UBUNTU

## MariaDB
- Dùng để chứa cơ sở dữ liệu của hệ thống

## PhpMyAdmin
- Dùng để xem cơ sở dữ liệu
- Không cần tạo bảng bằng PhpMyAdmin
- Django sẽ tự tạo bảng thông qua migration

## Django
- Build thành 1 Docker Container bằng `Dockerfile`
- Sử dụng Python + Django
- Mount thư mục source để dễ chỉnh sửa
- Chỉnh sửa file bằng:
--------
# 1. Mô tả chi tiết

---

# 👨‍💼 Bảng `Khach_Hang`

## Mục đích
Lưu thông tin người mang tài sản đến cầm cố tại tiệm.

## Các trường dữ liệu

| Tên trường    | Kiểu dữ liệu | Ý nghĩa                   |
| ------------- | ------------ | ------------------------- |
| id            | INT (PK)     | Mã khách hàng, khóa chính |
| ho_ten        | VARCHAR      | Họ và tên khách hàng      |
| so_dien_thoai | VARCHAR      | Số điện thoại liên hệ     |
| dia_chi       | TEXT         | Địa chỉ khách hàng        |

---

# 💎 Bảng `Mon_Do`

## Mục đích
Lưu thông tin các tài sản khách mang tới cầm.

## Các trường dữ liệu

| Tên trường | Kiểu dữ liệu | Ý nghĩa           |
| ---------- | ------------ | ----------------- |
| id         | INT (PK)     | Mã món đồ         |
| ten_mon_do | VARCHAR      | Tên món đồ        |
| mo_ta      | TEXT         | Mô tả chi tiết    |
| tinh_trang | VARCHAR      | Tình trạng món đồ |

## Ví dụ tên món đồ

- Điện thoại iPhone 13
- Laptop Dell
- Xe máy Vision

## Ý nghĩa trường `tinh_trang`

Dùng để quản lý trạng thái món đồ:

- Mới
- Cũ
- Trầy xước
- Hỏng nhẹ
- Đã chuộc

---

# 📄 Bảng `Hop_Dong`

## Mục đích
Lưu thông tin giao dịch cầm đồ giữa khách hàng và tiệm.

## Các trường dữ liệu

| Tên trường    | Kiểu dữ liệu | Ý nghĩa               |
| ------------- | ------------ | --------------------- |
| id            | INT (PK)     | Mã hợp đồng           |
| khach_hang_id | INT (FK)     | Tham chiếu khách hàng |
| mon_do_id     | INT (FK)     | Tham chiếu món đồ     |
| so_tien       | DECIMAL      | Số tiền cho vay       |
| ngay_cam      | DATE         | Ngày bắt đầu cầm      |
| ngay_het_han  | DATE         | Ngày hết hạn          |
| lai_suat      | FLOAT        | Lãi suất              |
| trang_thai    | VARCHAR      | Trạng thái hợp đồng   |

---

# 💰 Bảng `Thanh_Toan`

## Mục đích
Lưu lịch sử khách trả tiền cho hợp đồng.

## Các trường dữ liệu

| Tên trường      | Kiểu dữ liệu | Ý nghĩa             |
| --------------- | ------------ | ------------------- |
| id              | INT (PK)     | Mã thanh toán       |
| ngay_thanh_toan | DATE         | Ngày trả tiền       |
| so_tien         | DECIMAL      | Số tiền thanh toán  |
| ghi_chu         | TEXT         | Ghi chú             |
| hop_dong_id     | INT (FK)     | Tham chiếu hợp đồng |
# cấu trúc Thư mục 
pawnshop_project/
│
├── docker-compose.yml
│
├── templates/
│   └── home.html
│
└── django_app/
    │
    ├── Dockerfile
    ├── requirements.txt
    ├── manage.py
    │
    ├── pawnshop/
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── urls.py
    │   ├── asgi.py
    │   └── wsgi.py
    │
    └── management/
        ├── __init__.py
        ├── admin.py
        ├── apps.py
        ├── models.py
        ├── views.py
        ├── urls.py
        ├── tests.py
        │
        └── migrations/
            └── __init__.py

# SỬ DỤNG DOCKER TRÊN UBUNTU CHO HỆ THỐNG QUẢN LÝ TIỆM CẦM ĐỒ


# 4. CÀI ĐẶT MÔI TRƯỜNG

## Cập nhật Ubuntu

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Cài Docker

```bash
sudo apt install docker.io -y
```


## Kiểm tra nhanh tất cả đã cài 

```bash
docker --version && docker compose version
```

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0e06bc83-8166-4583-9316-c39e4573205d" />

# 5. TẠO THƯ MỤC PROJECT

```bash
mkdir pawnshop_project
cd pawnshop_project
```

---

## Tạo thư mục Django

```bash
mkdir django_app
```

---

## Cấu trúc thư mục

```text
pawnshop_project/
│
├── docker-compose.yml
│
└── django_app/
    ├── Dockerfile
    └── requirements.txt
```

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/68405ea1-edcc-4cf2-afe9-ab15445dcaa7" />

# 6. TẠO Dockerfile

## Vào thư mục Django

```bash
cd django_app
```

## Tạo file

```bash
sudo nano Dockerfile
```

## Nội dung Dockerfile

```dockerfile
# Sử dụng Python 3.12 chính thức
FROM python:3.12

# Không tạo file pyc
ENV PYTHONDONTWRITEBYTECODE=1

# Hiển thị log realtime
ENV PYTHONUNBUFFERED=1

# Thư mục làm việc trong container
WORKDIR /app

# Copy requirements vào container
COPY requirements.txt .

# Cài thư viện Python
RUN pip install --no-cache-dir -r requirements.txt

# Copy toàn bộ source code
COPY . .

# Mở cổng Django
EXPOSE 8000

# Chạy Django server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

---

# 7. TẠO requirements.txt

## Tạo file

```bash
sudo nano requirements.txt
```

## Nội dung

```txt
# Framework web Django
django

# Driver kết nối MariaDB/MySQL
mysqlclient

# Thư viện hỗ trợ MySQL
PyMySQL
```

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/595b4772-f0bd-494a-a72c-13e914f4e089" />

# 8. TẠO docker-compose.yml
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c094f2fe-ab7b-40a8-a6d5-9cb6c30d3fc8" />

## Quay lại thư mục project

```bash
cd ..
```

## Tạo file

```bash
sudo nano docker-compose.yml
```

## Nội dung file

```yaml
services:

  mariadb:
    image: mariadb:11

    container_name: pawnshop_mariadb

    restart: always

    environment:
      MYSQL_ROOT_PASSWORD: root123
      MYSQL_DATABASE: pawnshop_db
      MYSQL_USER: pawn_user
      MYSQL_PASSWORD: pawn123

    ports:
      - "3307:3306"

    volumes:
      - mariadb_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin

    container_name: pawnshop_phpmyadmin

    restart: always

    ports:
      - "8080:80"

    environment:
      PMA_HOST: mariadb
      MYSQL_ROOT_PASSWORD: root123

    depends_on:
      - mariadb

  django:
    build: ./django_app

    container_name: pawnshop_django

    restart: always

    ports:
      - "8000:8000"

    volumes:
      - ./django_app:/app

    depends_on:
      - mariadb

volumes:
  mariadb_data:
```

---

# 9. BUILD VÀ CHẠY HỆ THỐNG

```bash
docker compose up --build -d
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6b3e2122-8fb4-4055-ad54-fea8a97d7a43" />


## Kiểm tra container

```bash
docker ps
```

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/06f4c71c-9471-47b9-8d11-611a47cc0866" />


# 10. TẠO DJANGO PROJECT

## Vào container Django

```bash
docker compose exec django bash
```

## Tạo project

```bash
django-admin startproject pawnshop .
```

## Tạo app

```bash
python manage.py startapp management
```

---

# 11. CẤU HÌNH DJANGO

## Mở file settings.py

```bash
nano pawnshop/settings.py
```

---

## Sửa ALLOWED_HOSTS

```python
ALLOWED_HOSTS = ['*']
```

---

## Thêm app management

```python
'management',
```

---

## Cấu hình DATABASES

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',

        'NAME': 'pawnshop_db',

        'USER': 'pawn_user',

        'PASSWORD': 'pawn123',

        'HOST': 'mariadb',

        'PORT': '3306',
    }
}
```

---

## Cấu hình Template

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',

        'DIRS': [BASE_DIR / 'templates'],

        'APP_DIRS': True,
    },
]
```

---

# 12. TẠO models.py

## Mở file

```bash
nano management/models.py
```

## Nội dung

```python
from django.db import models


class Khach_Hang(models.Model):

    ho_ten = models.CharField(max_length=100)

    so_dien_thoai = models.CharField(max_length=20)

    dia_chi = models.TextField()

    def __str__(self):
        return self.ho_ten


class Mon_Do(models.Model):

    ten_mon_do = models.CharField(max_length=200)

    mo_ta = models.TextField()

    tinh_trang = models.CharField(max_length=100)

    def __str__(self):
        return self.ten_mon_do


class Hop_Dong(models.Model):

    khach_hang = models.ForeignKey(
        Khach_Hang,
        on_delete=models.CASCADE
    )

    mon_do = models.ForeignKey(
        Mon_Do,
        on_delete=models.CASCADE
    )

    so_tien = models.DecimalField(
        max_digits=15,
        decimal_places=2
    )

    ngay_cam = models.DateField()

    ngay_het_han = models.DateField()

    lai_suat = models.DecimalField(
        max_digits=5,
        decimal_places=2
    )

    trang_thai = models.CharField(
        max_length=50,
        default='Đang cầm'
    )

    def __str__(self):
        return f"HD-{self.id}"


class Thanh_Toan(models.Model):

    hop_dong = models.ForeignKey(
        Hop_Dong,
        on_delete=models.CASCADE
    )

    ngay_thanh_toan = models.DateField()

    so_tien = models.DecimalField(
        max_digits=15,
        decimal_places=2
    )

    ghi_chu = models.TextField(blank=True)

    def __str__(self):
        return f"TT-{self.id}"
```

---

# 13. TẠO DATABASE

## Tạo migration

```bash
docker compose exec django python manage.py makemigrations
```

## Apply migration

```bash
docker compose exec django python manage.py migrate
```

---

# 14. TẠO DJANGO ADMIN

## Mở file

```bash
nano management/admin.py
```

## Nội dung

```python
from django.contrib import admin

from .models import *

admin.site.register(Khach_Hang)
admin.site.register(Mon_Do)
admin.site.register(Hop_Dong)
admin.site.register(Thanh_Toan)
```

---

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b48786c8-ee20-4490-8bc0-5a15676d9b3a" />


# 15. TẠO TÀI KHOẢN ADMIN

```bash
docker compose exec django python manage.py createsuperuser
```

---
TK: admin 
mail : admin @gmail.com
pass :123456
#  Tạo Dữ Liệu ảo 
 1 Tạo Khách hàng 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/991773d4-07ca-414c-9c89-c19fae4e02ed" />
 2 Tạo hợp đồng cho khách 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dcb38609-bac6-400d-bcb7-909e1f57f69d" />

 

# 16. DJANGO ADMIN

## Truy cập

```text
http://IP_SERVER:8000/admin
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/66b733b1-3415-4769-beac-c0298a35b10a" />

## Chức năng

- Đăng nhập admin
- Thêm dữ liệu
- Sửa dữ liệu
- Xóa dữ liệu
- Quản lý khóa ngoại bằng text

---

# 17. PHPMYADMIN

## Truy cập

```text
http://IP_SERVER:8080
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/32bb0a25-4a14-46d4-a006-d07a3ae9f71e" />

## Kiểm tra

- Dữ liệu bảng
- Foreign Key
- khach_hang_id
- hop_dong_id

---

# 18. SSH VÀ NANO

## SSH vào server

```bash
ssh user@IP_SERVER
```

## Chỉnh sửa file

```bash
sudo nano ten_file
```

---

# 19. TEMPLATE HTML + JINJA2

## Tạo thư mục templates

```bash
mkdir templates
```

## Tạo file home.html

```bash
sudo nano templates/home.html
```

## Nội dung home.html

```html
<!DOCTYPE html>
<html>
<head>
    <title>Danh sách con nợ</title>
</head>
<body>

<h1>Danh sách con nợ đến hạn</h1>

<table border="1">

    <tr>
        <th>Khách hàng</th>
        <th>Món đồ</th>
        <th>Số tiền</th>
        <th>Ngày hết hạn</th>
    </tr>

    {% for item in debts %}

    <tr>
        <td>{{ item.khach_hang.ho_ten }}</td>
        <td>{{ item.mon_do.ten_mon_do }}</td>
        <td>{{ item.so_tien }}</td>
        <td>{{ item.ngay_het_han }}</td>
    </tr>

    {% endfor %}

</table>

</body>
</html>
```

---

## Tạo views.py

```bash
sudo nano management/views.py
```

## Nội dung views.py

```python
from django.shortcuts import render
from .models import Hop_Dong
from datetime import date


def home_page(request):

    debts = Hop_Dong.objects.filter(
        ngay_het_han__lt=date.today(),
        trang_thai='Đang cầm'
    )

    return render(request, 'home.html', {
        'debts': debts
    })
```

---

## Tạo urls.py

```bash
sudo nano management/urls.py
```

## Nội dung urls.py

```python
from django.urls import path

from .views import home_page

urlpatterns = [
    path('', home_page),
]
```

---

## Sửa pawnshop/urls.py

```bash
sudo nano pawnshop/urls.py
```

## Nội dung

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('management.urls')),
]
```

---

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/148bc5f4-800b-4a98-b63e-03d050619c11" />

# 20. Public Website Django bằng Cloudflare Tunnel

## Bước 1: Download Cloudflared

```bash
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
```

---

# Bước 2: Cài đặt Cloudflared

```bash
sudo dpkg -i cloudflared-linux-amd64.deb
```

---

# Bước 3: Kiểm tra phiên bản

```bash
cloudflared --version
```

Nếu hiện version là cài thành công.

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/30515081-5359-4160-bd6b-88cf13184bf4" />

# Bước 4: Đăng nhập Cloudflare

```bash
cloudflared tunnel login
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/31801a6e-e6b9-4d31-a7c9-4ba4c9a9f3f6" />

Ubuntu sẽ hiện link dạng:

```text
https://dash.cloudflare.com/argotunnel?aud=...
```

Copy link và mở trên trình duyệt.

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c6085fa2-24f6-4cc9-8172-9a0afdd6bc20" />

# Bước 5: Authorize Cloudflare

Cloudflare sẽ hỏi:

```text
Authorize Cloudflared
```

- Chọn domain
- Nhấn `Authorize`

Nếu thành công Ubuntu sẽ hiện:

```text
You have successfully logged in.
```

---

# Bước 6: Tạo Tunnel

```bash
cloudflared tunnel create pawnshop
```

Kết quả sẽ hiện:

```text
Tunnel credentials written to:
/home/USERNAME/.cloudflared/xxxxxxxx.json
```
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f1de6ec6-c12c-4659-bbad-5f36b5d15900" />

Copy lại:

```text
Tunnel ID
```

---

# Bước 7: Tạo thư mục config

```bash
mkdir -p ~/.cloudflared
```

---

# Bước 8: Tạo file config.yml

```bash
nano ~/.cloudflared/config.yml
```

---

# Nội dung config.yml

```yaml
tunnel: 97d48e9c-e471-4a69-9c68-5479e0b57adc

credentials-file: /home/nguyentienthang/.cloudflared/97d48e9c-e471-4a69-9c68-5479e0b57adc.json

ingress:
  - hostname: pawnshop.nthangi.id.vn
    service: http://localhost:8000

  - service: http_status:404
```

---


# Bước 9: Kiểm tra file config

```bash
cat ~/.cloudflared/config.yml
```

---

# Bước 10: Tạo DNS

```bash
cloudflared tunnel route dns pawnshop pawnshop.nthangi.id.vn
```

Kết quả:

```text
Added CNAME pawnshop.nthangi.id.vn which will route to this tunnel
```

---

# Bước 11: Chạy Tunnel

```bash
cloudflared tunnel run pawnshop
```

Nếu thành công sẽ hiện:

```text
Registered tunnel connection
```

---

# Bước 12: Kiểm tra kết quả

Mở website:

```text
https://pawnshop.nthangi.id.vn
```

Nếu website Django hiển thị là thành công.

---

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9fdaa5b7-cd2d-497c-bea3-ded591863d10" />

# Lưu ý

- Không được tắt Terminal Ubuntu
- Nếu tắt Terminal:
  
```text
Tunnel sẽ dừng
Website sẽ offline
```

# Kết luận

Qua bài thực hành này, đã xây dựng thành công hệ thống quản lý tiệm cầm đồ sử dụng:

- Ubuntu
- Docker
- Docker Compose
- Django
- MariaDB
- PhpMyAdmin
- Cloudflare Tunnel

Hệ thống đã:

- Tổ chức cơ sở dữ liệu đúng mô hình quan hệ SQL
- Kết nối Django với MariaDB thành công
- Tạo các bảng dữ liệu bằng Django Models
- Thực hiện migrate dữ liệu tự động
- Sử dụng Django Admin để thêm, sửa, xoá dữ liệu
- Hiển thị dữ liệu bằng Template HTML và Jinja2
- Hiển thị danh sách con nợ đến hạn
- Kiểm tra được dữ liệu và khoá ngoại bằng PhpMyAdmin
- Đóng gói toàn bộ hệ thống bằng Docker
- Public website thành công bằng Cloudflare Tunnel

Qua bài này đã hiểu được:

- Cách triển khai ứng dụng Django bằng Docker
- Cách hoạt động của MariaDB và Foreign Key
- Cách sử dụng Docker Compose quản lý nhiều service
- Cách render dữ liệu bằng Django Template
- Cách public website nội bộ ra internet bằng Cloudflare Tunnel

Website đã hoạt động ổn định trên local và truy cập được từ internet thông qua sub-domain Cloudflare.
