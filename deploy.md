## Kiểm tra phiên bản hệ điều hành Ubuntu:
lsb_release -a

## Cài đặt môi trường .NET
sudo apt-get update && sudo apt-get install -y dotnet-sdk-8.0.

`sudo apt-get update` để cập nhật tất cả các gói phần mềm có sẵn trên hệ thống.

## Cài đặt gói apt-transport-https để hỗ trợ truy cập HTTPS cho APT
sudo apt install apt-transport-https

## Pull source
git clone https://<username>:<token>@github.com/username/repository.git

## Tham khảo
https://sinhnx.dev/lap-trinh/asp-net-core-nginx-ubuntu

### Docker [Docker Install](https://azdigi.com/blog/linux-server/tools/huonng-dan-cai-dat-docker-tren-ubuntu-22-04/)
- Cài đặt gói hỗ trợ HTTPS.
  
   `sudo apt install apt-transport-https ca-certificates curl software-properties-common`
  
- Thêm khóa GPG của kho lưu trữ Docker.
  
  `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
  
- Thêm kho lưu trữ Docker của Ubuntu 22.04 ( jammy) vào các apt sources.
  
  `echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
  
- Cập nhật packages và thiết lập để cài đặt Docker từ kho lưu trữ chính thức.
  
  `sudo apt update`
  `sudo apt-cache policy docker-ce`
- Cài đặt Docker
  `sudo apt install docker-ce -y`
