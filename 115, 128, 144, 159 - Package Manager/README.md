# Package Manager
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Package manager** คือเครื่องมือที่ทำให้กระบวนการจัดการ (การติดตั้ง การอัปเดต การกำหนดค่า และการถอดออก) ของโปรแกรมคอมพิวเตอร์บนระบบปฏิบัติการเป็นไปโดยอัตโนมัติ

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ในระบบปฎิบัติการ Linux, **แพ็คเกจ(Package)** คือ **ไฟล์เก็บถาวร**ที่มีแอปพลิเคชันซอฟต์แวร์ ไลบรารี และไฟล์ที่เกี่ยวข้องที่จำเป็นสำหรับการ**ติดตั้งและการจัดการซอฟต์แวร์บนระบบ** แพ็คเกจนำเสนอแนวทางที่เป็นมาตรฐานในการจัดการซอฟต์แวร์ จึงทำให้สะดวกสำหรับผู้ใช้ในการเพิ่มหรือลบแอปพลิเคชัน อย่างไรก็ตาม แพ็คเกจ Linux มีรูปแบบหลากหลาย บางส่วนที่ใช้ส่วนใหญ่ได้แก่:

**1. deb:** รูปแบบแพ็คเกจที่ถูกใช้โดย Ubuntu, Debian, Linux Mint และอื่น ๆ ในกลุ่มที่ใช้ Debian ไฟล์ .deb รวมไฟล์ที่เกี่ยวข้องทั้งหมดในรูปแบบไฟล์ .ar (archive format) ประกอบด้วยรายละเอียดซอฟต์แวร์ที่เกี่ยวข้องทั้งหมดที่เกี่ยวข้องกับเวอร์ชัน คำอธิบาย การขึ้นต่อกัน ใบอนุญาต ฯลฯ

**2. rpm:** รูปแบบนี้เดิมเรียกว่า Red Hat Package Manager และถูกใช้โดย Red Hat, Fedora, SUSE และอื่นๆ นอกจากนี้ยังมี configuration file metadata และเอกสารที่จำเป็นอื่นๆ เพื่อสร้างซอฟต์แวร์

**3.tar.xz :** Arch Linux ใช้รูปแบบแพ็คเกจนี้ และเป็นเพียง tarball ที่ถูกบีบอัด กล่าวอีกนัยหนึ่ง ไฟล์ tar.xz จะถูกคอมไพล์ไฟล์ไบนารี่ที่พร้อมใช้งานของแพ็คเกจซอฟต์แวร์
## Debian, Ubuntu Package management tools
## 1. dpkg

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dpkg เป็น Debian package manager ที่ติดตั้ง ลบ และกำหนดค่าแพ็คเกจด้วยนามสกุล .deb เพียงดาวน์โหลดเนื้อหาแพ็คเกจ DEB ไปยังระบบและแจ้งให้ทราบเกี่ยวกับการขึ้นต่อกันที่จำเป็น แต่ไม่ได้ติดตั้งหรือกำหนดค่าแพ็คเกจ .deb เนื่องจากขาดการขึ้นต่อกันเนื่องจากไม่สามารถเข้าถึงที่เก็บข้อมูลได้

ข้อเสียที่สำคัญของ dpkg ก็คือ dpkg เป็นโปรแกรมในระดับล่างซึ่งไม่ได้ดูแลในเรื่องของการขึ้นต่อกันของแพคเกจ ผู้ใช้งานจำเป็นต้องติดตั้งแพคเกจที่จำเป็นเอง
| command | description|
|---------|------------|
|`` --help `` | finding out all the options |
| ``-i or --install`` | install package |
| ``-r or --remove`` | remove an installed package |
| ``-P or --purge`` | alternative way to remove an installed package (can be seen as the complete uninstallation) |
| ``-L`` | list all the files that were installed by a package |
### 1.1 installing a package
คำสั่ง dpkg ขั้นพื้นฐานที่สุดใน Ubuntu คือการติดตั้งแพ็คเกจ เราสามารถติดตั้งแพ็คเกจ deb ใน Ubuntu หรือ Debian ได้โดยใช้คำสั่ง

``
sudo dpkg -i [package name]
``
### 1.2 removing a package
เมื่อไม่ต้องการโปรแกรมหรือบริการบนระบบ ก็ไม่มีประโยชน์ที่จะเก็บไว้ เราสามารถถอนการติดตั้งโปรแกรมหรือบริการออกจากระบบของเราได้โดยใช้คำสั่ง

``
sudo dpkg -r [package name]
``
## 2. apt

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
| ``show``| display detailed information about a package |
