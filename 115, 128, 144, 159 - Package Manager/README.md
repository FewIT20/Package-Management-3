# Package Manager
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Package manager** คือเครื่องมือที่ทำให้กระบวนการจัดการ (การติดตั้ง การอัปเดต การกำหนดค่า และการถอดออก) ของโปรแกรมคอมพิวเตอร์บนระบบปฏิบัติการเป็นไปโดยอัตโนมัติ

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ในระบบปฎิบัติการ Linux, **แพ็คเกจ(Package)** คือ **ไฟล์เก็บถาวร**ที่มีแอปพลิเคชันซอฟต์แวร์ ไลบรารี และไฟล์ที่เกี่ยวข้องที่จำเป็นสำหรับการ**ติดตั้งและการจัดการซอฟต์แวร์บนระบบ** แพ็คเกจนำเสนอแนวทางที่เป็นมาตรฐานในการจัดการซอฟต์แวร์ จึงทำให้สะดวกสำหรับผู้ใช้ในการเพิ่มหรือลบแอปพลิเคชัน อย่างไรก็ตาม แพ็คเกจ Linux มีรูปแบบหลากหลาย บางส่วนที่ใช้ส่วนใหญ่ได้แก่:

**1. deb:** รูปแบบแพ็คเกจที่ถูกใช้โดย Ubuntu, Debian, Linux Mint และอื่น ๆ ในกลุ่มที่ใช้ Debian ไฟล์ .deb รวมไฟล์ที่เกี่ยวข้องทั้งหมดในรูปแบบไฟล์ .ar (archive format) ประกอบด้วยรายละเอียดซอฟต์แวร์ที่เกี่ยวข้องทั้งหมดที่เกี่ยวข้องกับเวอร์ชัน คำอธิบาย การขึ้นต่อกัน ใบอนุญาต ฯลฯ

**2. rpm:** รูปแบบนี้เดิมเรียกว่า Red Hat Package Manager และถูกใช้โดย Red Hat, Fedora, SUSE และอื่นๆ นอกจากนี้ยังมี configuration file metadata และเอกสารที่จำเป็นอื่นๆ เพื่อสร้างซอฟต์แวร์

**3.tar.xz :** Arch Linux ใช้รูปแบบแพ็คเกจนี้ และเป็นเพียง tarball ที่ถูกบีบอัด กล่าวอีกนัยหนึ่ง ไฟล์ tar.xz จะถูกคอมไพล์ไฟล์ไบนารี่ที่พร้อมใช้งานของแพ็คเกจซอฟต์แวร์
## Debian, Ubuntu Package management tools
### 1. dpkg

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dpkg เป็น Debian package manager ที่ติดตั้ง ลบ และกำหนดค่าแพ็คเกจด้วยนามสกุล .deb เพียงดาวน์โหลดเนื้อหาแพ็คเกจ DEB ไปยังระบบและแจ้งให้ทราบเกี่ยวกับการขึ้นต่อกันที่จำเป็น แต่ไม่ได้ติดตั้งหรือกำหนดค่าแพ็คเกจ .deb เนื่องจากขาดการขึ้นต่อกันเนื่องจากไม่สามารถเข้าถึงที่เก็บข้อมูลได้

ข้อเสียที่สำคัญของ dpkg ก็คือ dpkg เป็นโปรแกรมในระดับล่างซึ่งไม่ได้ดูแลในเรื่องของการขึ้นต่อกันของแพคเกจ ผู้ใช้งานจำเป็นต้องติดตั้งแพคเกจที่จำเป็นเอง
| command | description|
|---------|------------|
|`` --help `` | finding out all the options |
| ``-i or --install`` | install package |
| ``-r or --remove`` | remove an installed package |
| ``--update-avail`` | update all packages to latest version |
| ``-P or --purge`` | alternative way to remove an installed package (can be seen as the complete uninstallation) |
| ``-l`` | list all the files that were installed by a package |
#### installing a package
คำสั่ง dpkg ขั้นพื้นฐานที่สุดใน Ubuntu คือการติดตั้งแพ็คเกจ เราสามารถติดตั้งแพ็คเกจ deb ใน Ubuntu หรือ Debian ได้โดยใช้คำสั่ง
```
sudo dpkg -i [package name].deb
```
#### removing a package
เมื่อไม่ต้องการโปรแกรมหรือบริการบนระบบ ก็ไม่มีประโยชน์ที่จะเก็บไว้ เราสามารถถอนการติดตั้งโปรแกรมหรือบริการออกจากระบบของเราได้โดยใช้คำสั่ง
```
sudo dpkg -r [package name]
```
#### update repositories
พื้นที่เก็บข้อมูล dpkg จะจัดเก็บแพ็คเกจทั้งหมดที่พร้อมใช้งานสำหรับการติดตั้งบน Ubuntu หรือ Debian Linux แต่เนื่องจากแพ็คเกจเหล่านี้ถูกจัดเก็บไว้ในเครื่อง ทำให้แพ็คเกจเวอร์ชันที่มีอยู่เก่าสำหรับโปรแกรมเมื่อมีการออกเวอร์ชันใหม่แล้ว ซึ่งทำให้จำเป็นต้องมีวิธีการอัพเดตที่เก็บข้อมูลโดยใช้คำสั่ง
```
sudo dpkg --update-avail
```
#### purging a package
หากต้องการลบแพ็คเกจและไฟล์การกำหนดค่าโดยใช้ dpkg ให้ใช้ตัวเลือก -P ตามด้วยชื่อแพ็คเกจ ตามคำสั่ง
```
sudo dpkg -P [package name]
```
#### list installed packages
หากต้องการแสดงรายการแพ็คเกจที่ติดตั้งทั้งหมดโดยใช้ dpkg ให้ใช้ตัวเลือก -l ตัวอย่างเช่น หากต้องการแสดงรายการแพ็คเกจที่ติดตั้งทั้งหมด คุณจะต้องใช้คำสั่ง
```
sudo dpkg -l
```
### 2. apt

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;apt คือ Advanced Package Tool ซึ่งจะมีโปรแกรมต่างๆ ที่ช่วยอำนวยความสะดวกในการจัดการแพคเกจ โดยปกติก็คือ โปรแกรมที่ขึ้นต้นด้วย apt- ทั้งหลาย เช่น apt-get, apt-cache

apt-get ไม่สามารถจัดการไฟล์ .deb โดยตรงเหมือนกับ dpkg ได้ เมื่อจะติดตั้งแพคเกจ apt-get จะทำการดาวน์โหลดไฟล์ .deb ที่จำเป็น (รวมทั้งแพคเกจอื่นๆ ที่จำเป็นด้วย) จากแหล่งต่างๆ ที่กำหนดไว้ในไฟล์ /etc/apt/sources.list แล้วเรียกใช้คำสั่ง dpkg อีกต่อหนึ่ง
| command | description|
|---------|------------|
| ``update``  | update repositories |
| ``upgrade`` | upgrade all currently installed packages to latest version |
| ``install [package name]`` | install a package |
| ``remove [package name]`` | uninstall package from the system |
| ``autoremove`` | uninstall a package with all its dependencies |
| ``purge [package name]`` | remove package along with its configuration files |
| ``clean`` | clean up the local repository |
| ``search`` | search for package |
| ``list --installed``| list all packages that have been installed |
#### updating package lists
ก่อนที่จะติดตั้งแพ็คเกจใดๆ บนระบบ Linux สิ่งสำคัญคือต้องอัพเดตรายการแพ็คเกจ Apt ใช้รายการแพ็กเกจเพื่อทราบว่ามีแพ็คเกจใดบ้างสำหรับการติดตั้ง โดยใช้คำสั่ง
```
sudo apt update
```
#### upgrading packages
หากต้องการอัพเกรดแพ็คเกจที่ติดตั้งบนระบบ Linux คำสั่งนี้จะดาวน์โหลดและติดตั้งแพ็คเกจเวอร์ชันล่าสุดที่ติดตั้งไว้แล้วบนระบบ โดยใช้คำสั่ง
```
sudo apt upgrade
```
#### installing packages
ในการติดตั้งแพ็คเกจต้องใช้คำสั่ง apt install ตามด้วยชื่อแพ็คเกจที่ต้องการติดตั้ง โดย
```
sudo apt install [package name]
```
#### removing packages
หากคุณต้องการลบแพ็คเกจออกจากระบบ Linux ใช้คำสั่ง
```
sudo apt remove [package name]
```
#### autoremove packages
บางครั้ง เมื่อลบแพ็คเกจออกจากระบบ Linux อาจจะทิ้งการขึ้นต่อกันบางอย่างไว้ และไม่จำเป็นอีกต่อไป สามารถลบออกได้โดยใช้คำสั่ง apt autoremove หากต้องการลบการพึ่งพาที่ไม่จำเป็นออกให้ใช้คำสั่ง
```
sudo apt autoremove
```
#### purging packages
หากต้องการลบแพ็คเกจออกจากระบบ ของอย่างสมบูรณ์ รวมถึง configuration file ให้ใช้คำสั่ง apt purge ตามด้วยชื่อแพ็คเกจ
```
sudo apt purge [package name]
```
#### cleaning up
เมื่อติดตั้งหรือลบแพ็คเกจบนระบบ, apt จะเก็บไฟล์แพ็คเกจที่ดาวน์โหลดไว้ในแคช ซึ่งอาจใช้พื้นที่ดิสก์ได้มากเมื่อเวลาผ่านไป หากต้องการล้างแคชให้ใช้คำสั่ง apt clean คำสั่งนี้จะลบไฟล์แพ็คเกจที่ดาวน์โหลดทั้งหมดออกจากแคช
```
sudo apt clean
```
#### searching for packages
หากต้องการค้นหาแพ็คเกจ ให้ใช้คำสั่ง apt search ตามด้วยชื่อแพ็คเกจที่ต้องการค้นหา คำสั่งนี้จะค้นหาที่เก็บแพ็กเกจและแสดงผลลัพธ์
```
sudo apt search [package name]
```
#### listing installed packages
หากต้องการแสดงรายการแพ็คเกจทั้งหมดที่ติดตั้งบนระบบ ให้ใช้คำสั่ง apt list คำสั่งนี้จะแสดงรายการแพ็คเกจที่ติดตั้งทั้งหมดพร้อมกับหมายเลขเวอร์ชัน
```
sudo apt list --installed
```
## RPM package management tool
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;RPM คือโปรแกรมโอเพนซอร์สสำหรับระบบที่ใช้ในการติดตั้ง, ถอนการติดตั้ง, อัปเดต, และจัดการซอฟต์แวร์บนระบบปฏิบัติการ Linux ระบบ RPM ถูกพัฒนาขึ้นบนพื้นฐานของ Linux Standard Base (LSB)
#### การติดตั้ง Package โดยใช้ RPM
ดาวน์โหลด Package:
* ค้นหา Package ที่ต้องการติดตั้งจากแหล่งที่เชื่อถือได้ เช่น เว็บไซต์ของผู้พัฒนาซอฟต์แวร์ หรือคลังซอฟต์แวร์ของ distribution ที่ใช้
* ดาวน์โหลดไฟล์ Package ที่มีนามสกุล .rpm
```bash
sudo rpm -i package.rpm
```
ปัญหาที่อาจเกิดขึ้น:
* การพึ่งพาที่ไม่ตรงกัน: Package ที่ต้องการติดตั้งอาจต้องการ Package อื่น ๆ ที่ยังไม่ได้ติดตั้ง
* ความขัดแย้งกับ Package อื่น: Package ที่ต้องการติดตั้งอาจมีไฟล์ที่ขัดแย้งกับ Package อื่นที่ติดตั้งอยู่
#### การลบ Package โดยใช้ RPM
```bash
sudo rpm -e package_name
```
ปัญหาที่อาจเกิดขึ้น:
* Package ที่ไม่พบ: Package ที่ต้องการลบอาจไม่พบ
* Package ที่มีการพึ่งพา: Package ที่ต้องการลบอาจมี Package อื่น ๆ ที่พึ่งพา
#### การอัพเดท Software โดยใช้ RPM
```bash
sudo rpm -U package-new-version.rpm
```
ปัญหาที่อาจเกิดขึ้น:
* การพึ่งพาที่ไม่ตรงกัน: เวอร์ชันใหม่ของซอฟต์แวร์อาจต้องการ Package อื่น ๆ ที่ยังไม่ได้ติดตั้ง
* ความขัดแย้งกับ Package อื่น: เวอร์ชันใหม่ของซอฟต์แวร์อาจมีไฟล์ที่ขัดแย้งกับ Package อื่นที่ติดตั้งอยู่
#### การค้นหาข้อมูลเกี่ยวกับ Software โดยใช้ RPM
```bash
rpm -q package.rpm
```
## YUM

## Arch Linux package management tool
## Pacman
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Pacman คือตัวจัดการแพ็กเกจสำหรับ Arch Linux และระบบปฏิบัติการ Linux ที่ใช้ Arch เป็นฐาน สามารถใช้ไฟล์บีบอัดเป็นรูปแบบแพ็กเกจและเก็บรักษาฐานข้อมูลแพ็กเกจในรูปแบบข้อความ Pacman ช่วยให้ระบบอัปเดตอยู่เสมอโดยการ Synchronize รายการแพ็กเกจกับเซิร์ฟเวอร์หลัก Pacman สามารถติดตั้งแพ็กเกจจากฐานข้อมูลอย่างเป็นทางการหรือแพ็กเกจที่สร้างขึ้นเองได้

#### การติดตั้ง Package โดยใช้ Pacman
```bash
sudo pacman -S package1 package2 package3
```
จากนั้น Pacman จะแสดงขนาดการดาวน์โหลดและติดตั้งของ Package และถามว่าต้องการดำเนินการต่อหรือไม่ หากต้องการให้ดำเนินการต่อให้พิมพ์ `y` ลงไปที่ console ของตัวเอง, Pacman แบ่งแพ็กเกจที่ติดตั้งออกเป็นสองประเภท

* ติดตั้งโดยตรง (Implicitly Installed): แพ็กเกจที่ติดตั้งโดยใช้ตัวเลือก -S หรือ -U
* แพ็กเกจที่จำเป็น (Dependencies): แพ็กเกจที่ติดตั้งเนื่องจากแพ็กเกจอื่นต้องการ

#### การลบ Package โดยใช้ Pacman
หากไม่ต้องการแพ็กเกจนั้นอีกต่อไป สามารถใช้คำสั่งต่อไปนี้เพื่อลบแพ็กเกจพร้อมกับการลบแพ็กเกจที่จำเป็นทั้งหมด (dependencies) ซึ่งไม่ได้ถูกใช้โดยแพ็กเกจอื่น
```bash
sudo pacman -Rs package1
```
* โดยที่ package1 คือชื่อของแพ็กเกจที่ต้องการลบ
  
หากต้องการลบ Package โดยไม่ลบ Package ที่จำเป็น (dependencies)
```bash
sudo pacman -R package1
```
* โดยที่ package1 คือชื่อของแพ็กเกจที่ต้องการลบ

#### (เสริม) หากต้องการลบ dependencies ที่ไม่ได้ใช้อีกต่อไป
```bash
pacman -Qdtq |  pacman -Rs -
```

#### การอัปเกรดแพคเกจ
ใน Arch Linux สามารถอัปเกรดระบบทั้งหมดได้ด้วยคำสั่งเดียวโดยใช้ Pacman เท่านั้น
```bash
sudo pacman -Suy
```
ให้เข้าใจความหมายของคำสั่งนี้ 
* คำว่า S บอก pacman ให้ข้อมูลภายในเครื่องกับฐานข้อมูลหลัก
* คำว่า u บอก pacman ให้อัปเกรด Package และ y คือการอัปเดตแคชข้อมูลภายในเครื่องในระบบ

#### การค้นหา package 
การค้นหา package ในฐานข้อมูลของ pacman ในการค้นหา query ในชื่อและคำอธิบายของแพคเกจในฐานข้อมูล
```bash
sudo pacman -Ss <query1> <query2>
```

#### ในการค้นหาใน package ที่ติดตั้งแล้วในระบบ
```bash
sudo pacman -Qs <query1> <query2>
```

#### ในการค้นหา query ในฐานข้อมูลในเครื่อง
```bash
sudo pacman -F <query1> <query2>
```

#### การล้างแคช pacakge
เมื่อ pacman ดาวน์โหลดแพคเกจ มันจะเก็บ package ไว้ที่ `/var/cache/pacman/pkg/` และขณะถอนการติดตั้ง package pacman จะไม่ลบไฟล์เหล่านี้, Pacman ใช้ไฟล์เหล่านี้เพื่อ downgrade แพคเกจหรือติดตั้ง Package, แต่มันอาจใช้พื้นที่มากในการเก็บ package เหล่านี้. เพื่อลบ package ที่เก็บไว้
```bash
sudo pacman -Sc
```
เพื่อลบแพคเกจทั้งหมดที่เก็บไว้และล้างแคช, ให้ใช้คำสั่งต่อไปนี้:
```
sudo pacman -Scc
```

#### การติดตั้งแพคเกจท้องถิ่น
pacman สามารถติดตั้งแพคเกจนอกเหนือจากที่มีในคลังหลักของ Arch Linux ให้ใช้คำสั่งต่อไปนี้เพื่อติดตั้ง Package

สำหรับ Package ภายในเครื่อง:
```bash
sudo pacman -U path_to_file.pkg.tar.xz
```
สำหรับ Package บนออนไลน์:
```bash
sudo pacman -U http://www.example.com/repo/example.pkg.tar.xz
```

#### การแก้ปัญหา
บางครั้งในการติดตั้ง package ด้วย pacman อาจพบเจอข้อผิดพลาดบางประการ ต่อไปนี้คือข้อผิดพลาดที่พบบ่อยร่วมกับ pacman

ข้อผิดพลาดที่เกี่ยวกับไฟล์ที่ขัดแย้ง: ข้อผิดพลาดนี้เกิดจากการมีแพคเกจที่ขัดแย้งกันอยู่ในคลัง. ในการแก้ไขข้อผิดพลาดนี้, สามารถเปลี่ยนชื่อไฟล์ด้วยตนเองหรือใช้คำสั่งเพื่อบังคับการเขียนทับไฟล์
```bash
pacman -S --overwrite glob package
```
ข้อผิดพลาดเกี่ยวกับแพคเกจที่ไม่ถูกต้อง: ข้อผิดพลาดนี้สามารถเกิดจากการติดตั้งแพคเกจบางส่วนเท่านั้น. สามารถแก้ไขข้อผิดพลาดนี้โดยการลบไฟล์ .part ใน `/var/cache/pacman/pkg/`
```bash
rm /var/cache/pacman/pkg/*.part
```
ข้อผิดพลาดที่เกี่ยวกับการล็อคฐานข้อมูล: ข้อผิดพลาดนี้เกิดขึ้นเมื่อ pacman ถูกขัดจังหวะในขณะที่กำลังอัปเดตฐานข้อมูล. ในการแก้ไขข้อผิดพลาดนี้, ลบไฟล์ `/var/lib/pacman/db.lock` และอัปเดตฐานข้อมูล
```bash
rm /var/lib/pacman/db.lock
```
