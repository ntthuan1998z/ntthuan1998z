# Deployment Notes

Ghi chú cài đặt .NET 8 và Docker trên Ubuntu, lấy mã nguồn từ GitHub và tài liệu triển khai ASP.NET Core với Nginx.

[← Về profile](README.md) · [Developer notes](dev-notes.md)

## Mục lục

- [Kiểm tra Ubuntu](#kiểm-tra-ubuntu)
- [Cài đặt .NET 8](#cài-đặt-net-8)
- [Lấy mã nguồn](#lấy-mã-nguồn)
- [Docker Engine](#docker-engine)
- [Tài liệu tham khảo](#tài-liệu-tham-khảo)

## Kiểm tra Ubuntu

Xem phiên bản hệ điều hành trước khi chọn hướng dẫn cài đặt:

```bash
lsb_release -a
```

### HTTPS cho APT

Ghi chú bổ sung về gói `apt-transport-https`:

```bash
sudo apt install apt-transport-https
```

## Cài đặt .NET 8

Chọn nguồn gói phù hợp với phiên bản Ubuntu theo [hướng dẫn của Microsoft](https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu-install) trước khi cài SDK:

```bash
sudo apt-get update && sudo apt-get install -y dotnet-sdk-8.0
```

`sudo apt-get update` cập nhật danh mục gói từ các repository để APT tra cứu phiên bản có sẵn.

Kiểm tra SDK sau khi cài đặt:

```bash
dotnet --list-sdks
```

## Lấy mã nguồn

Thay `username/repository` bằng owner và tên repo:

```bash
git clone https://github.com/username/repository.git
```

Với repo private, nhập username và personal access token khi Git yêu cầu xác thực. Xem [xác thực HTTPS với GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github#https).

## Docker Engine

Tham khảo [hướng dẫn cài Docker Engine trên Ubuntu](https://docs.docker.com/engine/install/ubuntu/) cho phiên bản hệ điều hành đang dùng.

### 1. Gỡ các gói xung đột

```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do
  sudo apt-get remove "$pkg"
done
```

### 2. Thiết lập repository APT của Docker

Thêm GPG key chính thức:

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

Thêm repository vào danh sách nguồn của APT:

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### 3. Cài các gói Docker

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 4. Kiểm tra cài đặt

```bash
sudo docker run hello-world
```

## Tài liệu tham khảo

| Chủ đề | Tài liệu |
| :--- | :--- |
| ASP.NET Core + Nginx trên Ubuntu | [Hướng dẫn triển khai — sinhnx.dev](https://sinhnx.dev/lap-trinh/asp-net-core-nginx-ubuntu) |
| Cài .NET trên Ubuntu | [Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu-install) |
| Cài Docker Engine trên Ubuntu | [Docker Docs](https://docs.docker.com/engine/install/ubuntu/) |
| Xác thực Git qua HTTPS | [GitHub Docs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github#https) |
