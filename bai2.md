## CÁC BƯỚC CÀI ĐẶT
### 1. Cập nhật hệ thống
Mở terminal và cập nhật danh sách gói
``` bash
sudo apt install -y git python3-pip
sudo pip3 install Adafruit_DHT
```
### 2. Cài đặt thư viện cho cảm biến DHT22
``` Bash
sudo apt install -y git python3-pip
sudo pip3 install Adafruit_DHT
```
### 3. Kích hoạt giao tiếp 1-Wire (nếu dùng DHT22)
Bật giao tiêp 1-Wire trên hệ thống
``` Bash
sudo raspi-config    		# Chọn: Interface Options >
		                    # 1-Wire > Enable
```
### 4. Kiểm tra Module đã được nhận
Sau khi bật 1-Wire. kiểm tra thiết bị
``` Bash
ls /sys/bus/w1/devices/    # Kết quả có dạng 28-xxxxxxx
```
### 5. Chạy thử chương trình đọc cảm biến 
Tải và chạy file Python mẫu
``` Bash
git clone https://github.com/adafruit/Adafruit_Python_DHT.git
cd Adafruit_Python_DHT/examples
```
```bash
python3 AdafruitDHT.py 22 4    # 22: DHT22, 4: GPIO pin
                               # Nhận kết quả độ ẩm và nhiệt độ
```
### 6. Tự động chạy khi khởi động (tuỳ chọn)
Thêm vào crontab để đọc dữ liệu định kì
``` Bash
crontab -e 				# Thêm dòng (ví dụ mỗi 5 phút): 
						# */5 * * * * python3 /home/pi/read_dht22.py
```
---
## 2. Sơ đồ kết nối
| **ĐHT22** | **Raspberry Pi (BCM)** |
|:---|:---:|
|🟥 VCC | 3.3V (Pin 1)|
|⬛ GND | GND (Pin 6)|
|🟨 DATA|GPIO4 (Pin 7)|
|🟩 NC|(Không kết nối)|

                     
                   
