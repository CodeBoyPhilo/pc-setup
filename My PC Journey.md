# Installing NVIDIA driver on Ubuntu24.04
```bash
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```
find out available driver:
```bash
ubuntu-drivers devices
```
install:
```bash
sudo apt purge 'nvidia*'
sudo apt autoremove --purge
sudo apt install nvidia-driver-570-open
```
# Installing CUDA Toolkit on Ubuntu24.04
```bash
wget [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1).1-1_all.deb

sudo dpkg -i cuda-keyring_1.1-1_all.deb

sudo apt-get update
sudo apt-get install cuda-toolkit -y 
sudo apt-get install nvidia-gds -y

sudo reboot
```
# Installing Docker & Container Toolkit on Ubuntu24.04
install docker:
```bash
sudo apt-get install curl apt-transport-https ca-certificates software-properties-common -y

curl -fsSL [https://download.docker.com/linux/ubuntu/gpg](https://download.docker.com/linux/ubuntu/gpg) | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update sudo apt-get install docker-ce -y

sudo usermod -aG docker $USER
```
install container toolkit:
```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
  && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list | \
    sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
    sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list

sudo apt-get update
sudo apt-get install nvidia-container-toolkit -y

sudo systemctl restart docker  
```