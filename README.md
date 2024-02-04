# Package Management (Group 3)
Computer Organization and Operating System - Self-study Assignment in part 2

นำเสนอ ผู้ช่วยศาสตราจารย์ ดร. สุเมธ ประภาวัต อาจารย์ประจำคณะเทคโนโลยีสารสนเทศ สถาบันเทคโนโลยีพระจอมเกล้าเจ้าคุณทหารลาดกระบัง

## Overview
Package Managment ระบบจัดการแพ็กเกจ คือ ระบบการจัดการซอฟต์แวร์ที่ช่วยทำให้ติดตั้ง, อัปเดต, และลบซอฟต์แวร์ได้อย่างสะดวกสบาย โดยไม่ต้องไป compile โค้ดเอง มีหลากหลายซอร์ฟแวร์ให้เลือกใช้งานไม่ว่าจะโปรแกรมซอร์ฟเวอร์ เช่น Brave, FileZila หรือ Library ของโปรแกรม เช่น mhwd, mhwd-db เป็นต้น

Repository คือที่เก็บรวบรวมแพกเกจของซอฟต์แวร์ทั้งหมด ในทุกๆ Linux จะมาพร้อมกับตัวจัดการแพกเกจ (Package Manager) เสมอ โดยที่พวก Package Manager นั้นจะทำงานอยู่บนพื้นฐานของ Repository เสมอ เหล่าผู้ใช้ Linux สามารถติดตั้งซอฟต์แวร์ได้อย่างง่าย

## Contributor
| Student ID | Name | Topic | Profile |
|--|--|--|--|
| 65070115 | นางสาวนภสร ศรีวิโรจน์ | Pacakge Manger | ![65070115](assets/image/65070115.jpg)|
| 65070121 | นางสาวนิโลบล  ตรีสุคนธรัตน์ | Respository Setup |  |
| 65070128 | นางสาวปภาดา รุกขรังษี | Pacakage Manager |  |
| 65070142 | นายพงศกร นพรัตยาภรณ์ | Respository Setup |  |
| 65070144 | นางสาวพรพัฒน์ ธนทัตธาดา | Package Manager |  |
| 65070159 | นายพีรณัฐ หมัดสอ | Package Manager | ![65070159](assets/image/65070159.jpg)  |
| 65070171 | นายภัทร์สรรพ์พร นครานุรักษ์ | Respository Setup |  |

## contents
- [Package Manager](#Package Manager)
  - [Ubuntu & Debian](#Ubuntu & Debian)
  - [CentOS, Fedora, RHEL](#CentOS, Fedora, RHEL)
  - [Arch Linux, Packman](#Arch Linux, Packman)
- [Respository setup](#Respository setup)
## Source
* Package Management in Ubuntu - https://ubuntu.com/server/docs/package-management
* Linux Package Management command cheat sheet - https://www.linuxteck.com/linux-package-management-command-cheat-sheet/
* Package Management in Linux - https://linuxsimply.com/linux-basics/package-management/
* Repository Configuration in Linux - https://linuxsimply.com/linux-basics/package-management/repository-configuration/
* Restore Default Debian and Ubuntu Repositories - https://www.baeldung.com/linux/default-repositories-debian-ubuntu
* initial push to a remote Git repository - https://stackoverflow.com/questions/2337281/how-do-i-do-an-initial-push-to-a-remote-repository-with-git
* add-apt-repository - https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/
* source for learning about managing YUM repositories - https://access.redhat.com/documentation/th-th/red_hat_enterprise_linux/6/html/deployment_guide/sec-managing_yum_repositories
* source for information related to using Nginx within Docker containers - https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/
