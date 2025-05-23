# Activity Diagram - ระบบจัดการการลาพนักงาน EdVISORY

## 1️⃣ บทนำ
**ชื่อโครงการ**: ระบบจัดการการลาพนักงาน EdVISORY (Employee Leave Management System - EdLeave)  
**วันที่จัดทำ**: 14 มีนาคม 2025  
**ผู้รับผิดชอบ**: อนันดา วุฒวรรรณะ  

เอกสารนี้แสดง **Activity Diagram** ของระบบจัดการการลาพนักงาน EdVISORY เพื่อให้เข้าใจถึงขั้นตอนการทำงานและการไหลของข้อมูลในระบบ โดยแบ่งตามบทบาทของผู้ใช้งานแต่ละประเภท

---

## 2️⃣ ผู้ใช้งานระบบ (Actors in Swimlanes)
Activity Diagram นี้แบ่งเป็น 4 Swimlanes ตามบทบาทของผู้ใช้งานในระบบ:
- **พนักงาน** - ผู้ยื่นคำขอลาและตรวจสอบสถานะการลา
- **Supervisor** - ผู้อนุมัติคำขอลาขั้นต้น
- **หัวหน้าแผนก** - ผู้อนุมัติคำขอลาระยะยาว (5 วันขึ้นไป)
- **ฝ่าย HR** - ผู้อนุมัติคำขอลาขั้นสุดท้ายและจัดการโควต้าวันลา

---

## 3️⃣ Activity Diagram แบบ Swimlane
![alt text](../diagrams/svg/activity-diagram.svg)

---

## 4️⃣ คำอธิบายขั้นตอนการทำงาน

### ช่องพนักงาน (Employee Lane)
1. **เริ่มต้น** - จุดเริ่มต้นของกระบวนการลา
2. **ตรวจสอบโควต้าวันลา** - พนักงานตรวจสอบจำนวนวันลาคงเหลือ
3. **มีวันลาเพียงพอ?** - ตรวจสอบว่ามีโควต้าวันลาเพียงพอหรือไม่
   - ถ้า **ไม่** - จบกระบวนการ
   - ถ้า **ใช่** - ดำเนินการต่อ
4. **สร้างคำขอลา** - พนักงานเริ่มสร้างคำขอลาใหม่
5. **เลือกประเภทการลา** - พนักงานเลือกประเภทการลา (ลาป่วย/ลากิจ/ลาพักร้อน)
6. **เลือกรูปแบบระยะเวลาการลา** - พนักงานเลือกรูปแบบระยะเวลา (ครึ่งวันเช้า/ครึ่งวันบ่าย/เต็มวัน)
7. **เลือกวันที่ต้องการลา** - พนักงานระบุวันที่ต้องการลา
8. **ระบุเหตุผลในการลา** - พนักงานระบุเหตุผลหรือรายละเอียดเพิ่มเติมในการลา
9. **ส่งคำขอลา** - พนักงานยืนยันและส่งคำขอลา
10. **รอการอนุมัติ** - พนักงานรอผลการพิจารณา
11. **รับการแจ้งเตือนผล** - พนักงานได้รับการแจ้งเตือนผลการพิจารณา
12. **จบ** - จบกระบวนการ

### ช่อง Supervisor
1. **รับคำขอลา** - Supervisor ได้รับคำขอลาจากพนักงาน
2. **ตรวจสอบคำขอ** - Supervisor ตรวจสอบรายละเอียดคำขอลา
3. **อนุมัติ?** - Supervisor พิจารณาอนุมัติคำขอลา
   - ถ้า **ไม่** - ปฏิเสธคำขอ
   - ถ้า **ใช่** - ดำเนินการตรวจสอบต่อ
4. **ลา 5 วันขึ้นไป?** - ตรวจสอบว่าเป็นการลาระยะยาวหรือไม่
   - ถ้า **ไม่** - ส่งต่อ HR (กรณีลาน้อยกว่า 5 วัน)
   - ถ้า **ใช่** - ส่งต่อหัวหน้าแผนก (กรณีลา 5 วันขึ้นไป)
5. **ส่งต่อ HR** - ส่งคำขอไปยัง HR (กรณีลาน้อยกว่า 5 วัน)
6. **ส่งต่อหัวหน้าแผนก** - ส่งคำขอไปยังหัวหน้าแผนกเพื่อพิจารณาต่อ (กรณีลา 5 วันขึ้นไป)
7. **ปฏิเสธคำขอ** - Supervisor ปฏิเสธคำขอ
8. **ระบุเหตุผลที่ปฏิเสธ** - Supervisor ระบุเหตุผลในการปฏิเสธคำขอลา

### ช่องหัวหน้าแผนก
1. **รับคำขอลาระยะยาว** - หัวหน้าแผนกได้รับคำขอลาระยะยาวที่ผ่านการอนุมัติจาก Supervisor แล้ว
2. **ตรวจสอบคำขอ** - หัวหน้าแผนกตรวจสอบรายละเอียดคำขอ
3. **อนุมัติ?** - หัวหน้าแผนกพิจารณาอนุมัติคำขอ
   - ถ้า **ใช่** - ส่งต่อ HR
   - ถ้า **ไม่** - ปฏิเสธคำขอ
4. **ส่งต่อ HR** - ส่งคำขอที่อนุมัติแล้วให้ HR พิจารณาอนุมัติขั้นสุดท้าย
5. **ปฏิเสธคำขอ** - หัวหน้าแผนก ปฏิเสธคำขอ
6. **ระบุเหตุผลที่ปฏิเสธ** - หัวหน้าแผนก ระบุเหตุผลในการปฏิเสธคำขอลา

### ช่องฝ่าย HR
1. **รับคำขอลา** - HR ได้รับคำขอลาที่ผ่านการอนุมัติตามลำดับขั้น
   - จาก Supervisor (กรณีลาน้อยกว่า 5 วัน)
   - จากหัวหน้าแผนก (กรณีลา 5 วันขึ้นไป)
2. **ตรวจสอบคำขอ** - HR ตรวจสอบรายละเอียดคำขอ
3. **อนุมัติ?** - HR พิจารณาอนุมัติคำขอขั้นสุดท้าย
   - ถ้า **ใช่** - อนุมัติคำขอ
   - ถ้า **ไม่** - ปฏิเสธคำขอ
4. **อนุมัติคำขอ** - HR อนุมัติคำขอลา
5. **ปฏิเสธคำขอและให้เหตุผล** - HR ปฏิเสธคำขอ
6. **ระบุเหตุผลที่ปฏิเสธ** - HR ระบุเหตุผลในการปฏิเสธคำขอลา
6. **ปรับปรุงโควต้าวันลา** - HR ปรับปรุงโควต้าวันลาของพนักงานโดยอัตโนมัติหลังอนุมัติ
7. **แจ้งผลการอนุมัติ** - HR แจ้งผลการพิจารณาให้พนักงานทราบ

---

## 5️⃣ ลำดับขั้นการอนุมัติคำขอลา

### 1. กรณีลาน้อยกว่า 5 วัน
```
พนักงาน → Supervisor → HR → พนักงาน (รับผลการอนุมัติ)
```
- พนักงานส่งคำขอลา
- Supervisor พิจารณาอนุมัติขั้นต้น
  - หากไม่อนุมัติ: แจ้งผลปฏิเสธกลับไปยังพนักงาน
  - หากอนุมัติ: ส่งต่อไปยัง HR
- HR พิจารณาอนุมัติขั้นสุดท้าย
  - หากอนุมัติ: ปรับปรุงโควต้าวันลาและแจ้งผลอนุมัติ
  - หากไม่อนุมัติ: แจ้งผลปฏิเสธกลับไปยังพนักงาน

### 2. กรณีลา 5 วันขึ้นไป
```
พนักงาน → Supervisor → หัวหน้าแผนก → HR → พนักงาน (รับผลการอนุมัติ)
```
- พนักงานส่งคำขอลา
- Supervisor พิจารณาอนุมัติขั้นต้น
  - หากไม่อนุมัติ: แจ้งผลปฏิเสธกลับไปยังพนักงาน
  - หากอนุมัติ: ส่งต่อไปยังหัวหน้าแผนก
- หัวหน้าแผนกพิจารณาอนุมัติขั้นกลาง
  - หากไม่อนุมัติ: แจ้งผลปฏิเสธกลับไปยังพนักงาน
  - หากอนุมัติ: ส่งต่อไปยัง HR
- HR พิจารณาอนุมัติขั้นสุดท้าย
  - หากอนุมัติ: ปรับปรุงโควต้าวันลาและแจ้งผลอนุมัติ
  - หากไม่อนุมัติ: แจ้งผลปฏิเสธกลับไปยังพนักงาน

---

## 6️⃣ การไหลของข้อมูลระหว่าง Swimlanes

### การส่งคำขอและผลการพิจารณา
1. **พนักงาน → Supervisor**
   - คำขอลาถูกส่งจากพนักงานไปยัง Supervisor เพื่อพิจารณาอนุมัติขั้นแรก

2. **Supervisor → หัวหน้าแผนก**
   - คำขอลาระยะยาว (5 วันขึ้นไป) ที่ผ่านการอนุมัติจาก Supervisor แล้วถูกส่งต่อไปยังหัวหน้าแผนก

3. **Supervisor → ฝ่าย HR**
   - คำขอลาน้อยกว่า 5 วันที่ผ่านการอนุมัติจาก Supervisor แล้วถูกส่งต่อไปยังฝ่าย HR

4. **หัวหน้าแผนก → ฝ่าย HR**
   - คำขอลาระยะยาว (5 วันขึ้นไป)ที่ผ่านการอนุมัติจากหัวหน้าแผนกแล้วถูกส่งต่อไปยังฝ่าย HR

5. **ฝ่าย HR → พนักงาน**
   - ผลการพิจารณาสุดท้ายถูกส่งจากฝ่าย HR ไปยังพนักงาน

6. **Supervisor/หัวหน้าแผนก → พนักงาน**
   - การปฏิเสธคำขอจาก Supervisor หรือหัวหน้าแผนกถูกแจ้งกลับไปยังพนักงาน โดยไม่มีการพิจารณาในขั้นถัดไป

---

## 7️⃣ ข้อกำหนดพิเศษ
1. **การอนุมัติตามลำดับขั้น** - คำขอลาต้องได้รับการอนุมัติตามลำดับขั้นเสมอ ไม่สามารถข้ามลำดับได้
2. **การยกเลิกกระบวนการเมื่อถูกปฏิเสธ** - หากคำขอถูกปฏิเสธในขั้นตอนใด จะไม่มีการส่งต่อไปยังขั้นตอนถัดไป
3. **การปรับปรุงโควต้าอัตโนมัติ** - ระบบต้องปรับปรุงโควต้าวันลาโดยอัตโนมัติเมื่อคำขอได้รับการอนุมัติจาก HR

---

📌 **หมายเหตุ**: Activity Diagram นี้ใช้เป็นแนวทางในการพัฒนาระบบจัดการการลาพนักงาน EdVISORY และอาจมีการปรับเปลี่ยนตามความเหมาะสมระหว่างการพัฒนา 