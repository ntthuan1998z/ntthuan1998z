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

### Docker [Docker Install](https://docs.docker.com/engine/install/ubuntu/)
1. Uninstall all conflicting packages:
```sh
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
2. Set up Docker's apt repository:
```sh
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
3. Install the Docker packages.
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
4. Verify
```sh
sudo docker run hello-world
```
