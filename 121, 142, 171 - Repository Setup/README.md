# Respoitory Setup

Repository คือที่เก็บรวบรวมแพกเกจของซอฟต์แวร์ทั้งหมด ในทุกๆ Linux จะมาพร้อมกับตัวจัดการแพกเกจ (Package Manager) เสมอ โดยที่พวก Package Manager นั้นจะทำงานอยู่บนพื้นฐานของ Repository เสมอ ผู้ใช้ Linux สามารถติดตั้งซอฟต์แวร์ได้อย่างง่าย
และ นักพัฒนาซอฟต์แวร์ใน Linux นั้นสามารถเอาซอฟต์แวร์ของตัวเองไปไว้ใน Repository ได้ เพื่อให้ทุกคนสามารถติดตั้งโปรแกรมได้ง่่าย

## Where are Linux default repositories located?
โดยปกติใน Debian-based Linux ไฟล์ repository จะอยู่ในไฟล์ที่มีชื่อว่า `/etc/apt/sources.list` โดยถ้าเกิดเราลอง `cat` เพื่อดูข้อมูลที่อยู่ในไฟล์นี้ออกมาเราจะเจอหน้าตาประมาณนี้
```
#deb cdrom:[Official Debian GNU/Linux Live 2023-06-26T06:56:00Z]/ bookworm main non-free-firmware

deb http://deb.debian.org/debian stable main
deb-src http://deb.debian.org/debian stable main

deb http://deb.debian.org/debian-security/ stable-security main
deb-src http://deb.debian.org/debian-security/ stable-security main

deb http://deb.debian.org/debian stable-updates main
deb-src http://deb.debian.org/debian stable-updates main
```

### Inside `/etc/apt/sources.list`
```
Types: deb deb-src
URIs: uri
Suites: suite
Components: [component1] [component2] [...]
option1: value1
option2: value2
```

## How to bring your own repository?
การสร้างหรือเพิ่ม repository เข้าไปในระบบปฏิบัติการ Linux ขึ้นอยู่กับการจัดการแพคเกจ (package management) ที่ระบบปฏิบัติการนั้น ๆ ใช้ ดังนั้นจึงมีหลายวิธี
### 1. การสร้าง Local Git Repository:
คำสั่ง git init จะสร้าง Git repository ในไดเรกทอรีปัจจุบันและเริ่มต้นการติดตามการเปลี่ยนแปลง:
```
mkdir my_project
cd my_project
git init
```
การใช้ git add เพื่อเพิ่มไฟล์ในสถานะ "Staged" และ git commit เพื่อบันทึกการเปลี่ยนแปลงที่ถูก Staged:
```
touch README.md
git add README.md
git commit -m "Initial commit"
```
### 2. การใช้ APT (Advanced Package Tool) ใน Ubuntu/Debian:
คำสั่งนี้ใช้เพื่อเพิ่มแหล่งที่มาของแพคเกจในไฟล์การกำหนดค่าของ APT:
```
sudo add-apt-repository <repository_URL>
```
คำสั่งนี้ใช้เพื่ออัปเดตรายการแพคเกจที่มีในระบบ:
```
sudo apt update
```
### 3. การใช้ YUM (Yellowdog Updater, Modified) ใน CentOS/Fedora:
คำสั่งนี้ใช้เพื่อเพิ่ม repository ใน YUM configuration:
```
sudo yum-config-manager --add-repo=<repository_URL>
```
คำสั่งนี้ใช้เพื่ออัปเดตรายการแพคเกจในระบบ:
```
sudo yum update
```
### 4. การใช้ Docker เพื่อสร้าง Containerized Repository:
Dockerfile นี้ใช้ Nginx เป็น Base Image และคัดลอกไฟล์จาก Directory ปัจจุบันไปยัง /usr/share/nginx/html ใน Container:
```
FROM nginx:latest
COPY . /usr/share/nginx/html
```
คำสั่ง docker build ใช้สร้าง Docker Image จาก Dockerfile และ docker run ใช้เริ่มต้น Container จาก Image ที่สร้างขึ้น:
```
docker build -t my-repo .
docker run -p 8080:80 my-repo
```
