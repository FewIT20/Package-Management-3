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
สร้าง Local Repository:
```
mkdir my_project
cd my_project
git init
```
เพิ่มไฟล์และ Commit:
```
touch README.md
git add README.md
git commit -m "Initial commit"
```
### 2. การใช้ APT (Advanced Package Tool) ใน Ubuntu/Debian:
เพิ่ม Repository:
```
sudo add-apt-repository <repository_URL>
```
อัปเดตรายการแพคเกจ:
```
sudo apt update
```
### 3. การใช้ YUM (Yellowdog Updater, Modified) ใน CentOS/Fedora:
เพิ่ม Repository:
```
sudo yum-config-manager --add-repo=<repository_URL>
```
อัปเดตรายการแพคเกจ:
```
sudo yum update
```
### 4. การใช้ Docker เพื่อสร้าง Containerized Repository:
สร้าง Dockerfile:
```
FROM nginx:latest
COPY . /usr/share/nginx/html
```
Build และรัน Docker Container:
```
docker build -t my-repo .
docker run -p 8080:80 my-repo
```
