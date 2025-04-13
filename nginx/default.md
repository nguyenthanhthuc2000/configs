# Hướng dẫn cài đặt Nginx, PHP 8.3 và PHP-FPM 8.3 trên Ubuntu

## 🧩 Bước 1: Cập nhật hệ thống

```bash
sudo apt update
sudo apt upgrade -y
```

---

## 📦 Bước 2: Thêm repository PHP 8.3

> Sử dụng PPA `ondrej/php` để có các phiên bản PHP mới nhất:

```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

---

## 🌐 Bước 3: Cài đặt Nginx

```bash
sudo apt install nginx -y
```

---

## ⚙️ Bước 4: Cài đặt PHP 8.3 và PHP-FPM

```bash
sudo apt install php8.3 php8.3-fpm -y
```

Cài thêm các extension phổ biến:

```bash
sudo apt install php8.3-cli php8.3-mbstring php8.3-xml php8.3-mysql php8.3-curl php8.3-zip -y
```

---

## 🔍 Bước 5: Kiểm tra PHP-FPM đã hoạt động chưa

```bash
sudo systemctl status php8.3-fpm
```

Nếu chưa chạy, dùng lệnh sau để kích hoạt:

```bash
sudo systemctl start php8.3-fpm
sudo systemctl enable php8.3-fpm
```

---

## 🔁 Bước 6: Khởi động lại Nginx

```bash
sudo systemctl restart nginx
```

---

## 📌 Ghi chú

Trong file cấu hình Nginx, PHP-FPM 8.3 sử dụng socket:

```
fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
```

> Điều này cho phép Nginx giao tiếp với PHP-FPM thông qua Unix socket (hiệu suất tốt hơn `localhost:9000`).

---