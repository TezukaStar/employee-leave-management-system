#  Use Case Diagram - ระบบจัดการการลาพนักงาน EdVISORY

## 1️⃣ บทนำ
**ชื่อโครงการ**: ระบบจัดการการลาพนักงาน EdVISORY (Employee Leave Management System - EdLeave)  
**วันที่จัดทำ**: 13 มีนาคม 2025  
**ผู้รับผิดชอบ**: อนันดา วุฒวรรรณะ  

เอกสารนี้อธิบาย **Use Cases** ของระบบจัดการการลาพนักงาน EdVISORY เพื่อให้เข้าใจถึงการใช้งานระบบของผู้ใช้แต่ละประเภท

---

## 2️⃣ ผู้ใช้งานระบบ (Actors)
- **พนักงาน** - พนักงานทุกคนในองค์กร
- **Supervisor** - หัวหน้างานที่ดูแลพนักงาน
- **หัวหน้าแผนก** - ผู้บริหารระดับกลางที่ดูแลแผนก
- **ฝ่าย HR** - ทีมงานบริหารทรัพยากรบุคคล

---

## 3️⃣ แผนภาพ Use Case (Use Case Diagram)
![alt text](../diagrams/svg/use-case-diagram.svg)
---

## 4️⃣ รายละเอียด Use Cases

### UC-001: ตรวจสอบโควต้าวันลาคงเหลือ
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-001 |
| **Use Case Name** | ตรวจสอบโควต้าวันลาคงเหลือ |
| **Actor(s)** | พนักงาน |
| **Description** | พนักงานสามารถตรวจสอบจำนวนวันลาคงเหลือของแต่ละประเภท (ลาป่วย, ลากิจ, ลาพักร้อน) |
| **Preconditions** | 1. พนักงานต้องล็อกอินเข้าสู่ระบบแล้ว |
| **Basic Flow** | 1. พนักงานเลือกเมนู "ตรวจสอบวันลาคงเหลือ"<br>2. ระบบแสดงข้อมูลวันลาคงเหลือของพนักงานแยกตามประเภทการลา|
| **Alternative Flows** | N/A |
| **Postconditions** | พนักงานทราบจำนวนวันลาคงเหลือของตนเอง |
| **Business Rules** | 1. การแสดงผลโควต้าวันลาต้องถูกต้องตามนโยบายบริษัท<br>2. ข้อมูลควรอัปเดตแบบเรียลไทม์หลังจากการอนุมัติลาสุด |

### UC-002: ยื่นคำขอลา
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-002 |
| **Use Case Name** | ยื่นคำขอลา |
| **Actor(s)** | พนักงาน |
| **Description** | พนักงานสามารถยื่นคำขอลาโดยระบุประเภทและระยะเวลาการลา |
| **Preconditions** | 1. พนักงานต้องล็อกอินเข้าสู่ระบบแล้ว<br>2. พนักงานต้องมีวันลาคงเหลือเพียงพอ |
| Basic Flow | 1. พนักงานเลือกเมนู "ยื่นคำขอลา"<br>2. พนักงานเลือกประเภทการลา (ลาป่วย, ลากิจ, ลาพักร้อน)<br>3. พนักงานเลือกรูปแบบระยะเวลาการลา (ครึ่งวันเช้า, ครึ่งวันบ่าย, เต็มวัน)<br>4. พนักงานระบุวันที่ต้องการลา<br>5. พนักงานระบุเหตุผลในการลา<br>6. พนักงานกดส่งคำขอลา<br>7. ระบบบันทึกคำขอลาและส่งให้ Supervisor พิจารณา |
| **Alternative Flows** |1. วันลาคงเหลือไม่เพียงพอ ระบบแจ้งเตือนว่าวันลาไม่เพียงพอ<br>2. พนักงานสามารถยกเลิกหรือปรับเปลี่ยนคำขอลา |
| **Postconditions** | 1. คำขอลาถูกบันทึกในระบบ<br>2. คำขอลาถูกส่งให้ Supervisor พิจารณา |
| **Business Rules** | 1. การลาที่น้อยกว่า 5 วันขึ้นไปคำขอจะถูกส่งให้ Supervisor และ HR พิจารณา<br>2. การลาติดต่อกันตั้งแต่ 5 วันขึ้นไปคำขอจะถูกส่งให้ Supervisor, หัวหน้าแผนก และ HR พิจารณา|

### UC-003: ติดตามสถานะการลา
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-003 |
| **Use Case Name** | ติดตามสถานะการลา |
| **Actor(s)** | พนักงาน |
| **Description** | พนักงานสามารถติดตามสถานะคำขอลาที่ยื่นไปแล้ว |
| **Preconditions** | 1. พนักงานต้องล็อกอินเข้าสู่ระบบแล้ว<br>2. พนักงานต้องมีคำขอลาที่ยื่นไปแล้ว |
| **Basic Flow** | 1. พนักงานเลือกเมนู "ติดตามสถานะการลา"<br>2. ระบบแสดงรายการคำขอลาทั้งหมดและสถานะปัจจุบัน (รออนุมัติ, อนุมัติแล้ว, ปฏิเสธ)<br>3. พนักงานสามารถเลือกดูรายละเอียดของแต่ละคำขอลา |
| **Alternative Flows** | N/A |
| **Postconditions** | พนักงานทราบสถานะปัจจุบันของคำขอลา |
| **Business Rules** | 1. ระบบต้องแสดงสถานะล่าสุดแบบเรียลไทม์ |

### UC-004: อนุมัติ/ปฏิเสธการลา
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-004 |
| **Use Case Name** | อนุมัติ/ปฏิเสธการลา |
| **Actor(s)** | Supervisor, ฝ่าย HR |
| **Description** | Supervisor และฝ่าย HR สามารถพิจารณาอนุมัติหรือปฏิเสธคำขอลาของพนักงาน |
| **Preconditions** | 1. ผู้ใช้ (Supervisor หรือ HR) ต้องล็อกอินเข้าสู่ระบบแล้ว<br>2. ต้องมีคำขอลาที่รอการพิจารณา |
| **Basic Flow** | 1. ผู้ใช้เลือกเมนู "พิจารณาคำขอลา"<br>2. ระบบแสดงรายการคำขอลาที่รอการพิจารณา<br>3. ผู้ใช้เลือกคำขอลาที่ต้องการพิจารณา<br>4. ระบบแสดงรายละเอียดของคำขอลา<br>5. ผู้ใช้เลือกอนุมัติหรือปฏิเสธคำขอ<br>6. หากปฏิเสธ ผู้ใช้ต้องระบุเหตุผล<br>7. ผู้ใช้กดยืนยันการพิจารณา<br>8. ระบบบันทึกผลการพิจารณาและแจ้งให้ผู้เกี่ยวข้องทราบ |
| **Alternative Flows** | **กรณีลา 5 วันขึ้นไป**<br>1. หากเป็น Supervisor ระบบจะส่งต่อให้หัวหน้าแผนกพิจารณา<br>2. หากเป็นหัวหน้าแผนก ระบบจะส่งต่อให้ฝ่าย HR พิจารณาเป็นขั้นตอนสุดท้าย |
| **Postconditions** | 1. ผลการพิจารณาถูกบันทึกในระบบ<br>2. พนักงานที่ยื่นคำขอได้รับการแจ้งเตือนเกี่ยวกับผลการพิจารณา |
| **Business Rules** | N/A |

### UC-005: อนุมัติ/ปฏิเสธการลา 5 วันขึ้นไป
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-005 |
| **Use Case Name** | อนุมัติ/ปฏิเสธการลา 5 วันขึ้นไป |
| **Actor(s)** | หัวหน้าแผนก |
| **Description** | หัวหน้าแผนกสามารถพิจารณาอนุมัติหรือปฏิเสธคำขอลา 5 วันขึ้นไปที่ผ่านการอนุมัติจาก Supervisor แล้ว |
| **Preconditions** | 1. หัวหน้าแผนกต้องล็อกอินเข้าสู่ระบบแล้ว<br>2. ต้องมีคำขอลา 5 วันขึ้นไปที่ผ่านการอนุมัติจาก Supervisor แล้ว |
| **Basic Flow** | 1. หัวหน้าแผนกเลือกเมนู "พิจารณาคำขอลา 5 วันขึ้นไป"<br>2. ระบบแสดงรายการคำขอลา 5 วันขึ้นไปที่รอการพิจารณา<br>3. หัวหน้าแผนกเลือกคำขอลาที่ต้องการพิจารณา<br>4. ระบบแสดงรายละเอียดของคำขอลา<br>5. หัวหน้าแผนกเลือกอนุมัติหรือปฏิเสธคำขอ<br>6. หากปฏิเสธ ผู้ใช้ต้องระบุเหตุผล<br>7. หัวหน้าแผนกกดยืนยันการพิจารณา<br>8. ระบบบันทึกผลการพิจารณาและส่งต่อให้ฝ่าย HR พิจารณาต่อไป (กรณีอนุมัติ) |
| **Alternative Flows** | N/A |
| **Postconditions** | 1. ผลการพิจารณาถูกบันทึกในระบบ<br>2. คำขอที่ได้รับการอนุมัติจะถูกส่งต่อให้ฝ่าย HR |
| **Business Rules** | N/A |

### UC-006: จัดการโควต้าวันลา
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-006 |
| **Use Case Name** | จัดการโควต้าวันลา |
| **Actor(s)** | ฝ่าย HR |
| **Description** | ฝ่าย HR สามารถจัดการโควต้าวันลาของพนักงานแต่ละคน |
| **Preconditions** | 1. ผู้ใช้ฝ่าย HR ต้องล็อกอินเข้าสู่ระบบแล้ว |
| **Basic Flow** | 1. ฝ่าย HR เลือกเมนู "จัดการโควต้าวันลา"<br>2. ระบบแสดงรายชื่อพนักงานทั้งหมดพร้อมโควต้าวันลาคงเหลือ<br>3. ฝ่าย HR เลือกพนักงานที่ต้องการจัดการโควต้า<br>4. ระบบแสดงข้อมูลโควต้าวันลาแยกตามประเภท<br>5. ฝ่าย HR สามารถเพิ่มหรือลดจำนวนวันลาแต่ละประเภท<br>6. ฝ่าย HR กดบันทึกการเปลี่ยนแปลง<br>7. ระบบบันทึกการเปลี่ยนแปลงและแจ้งให้พนักงานทราบ |
| **Alternative Flows** | **การตั้งค่าโควต้าวันลาประจำปี**<br>1. ฝ่าย HR สามารถตั้งค่าโควต้าวันลาประจำปีให้พนักงานทั้งหมดพร้อมกัน<br>2. ระบบจะปรับปรุงโควต้าวันลาของพนักงานทุกคนตามการตั้งค่า |
| **Postconditions** | 1. โควต้าวันลาของพนักงานถูกปรับปรุง<br>2. ระบบบันทึกประวัติการเปลี่ยนแปลงโควต้าวันลา |
| **Business Rules** | N/A |

### UC-007: ดูข้อมูลการลาของพนักงาน
| หัวข้อ | รายละเอียด |
|-------|-----------|
| **Use Case ID** | UC-007 |
| **Use Case Name** | ดูข้อมูลการลาของพนักงาน |
| **Actor(s)** | Supervisor, หัวหน้าแผนก, ฝ่าย HR |
| **Description** | ผู้ใช้สามารถดูข้อมูลและประวัติการลาของพนักงาน |
| **Preconditions** | 1. ผู้ใช้ต้องล็อกอินเข้าสู่ระบบแล้ว |
| **Basic Flow** | 1. ผู้ใช้เลือกเมนู "ข้อมูลการลาของพนักงาน"<br>2. ระบบแสดงรายชื่อพนักงานตามสิทธิ์การเข้าถึง (Supervisor ดูได้เฉพาะลูกทีม, หัวหน้าแผนกดูได้ทั้งแผนก, HR ดูได้ทั้งองค์กร)<br>3. ผู้ใช้เลือกพนักงานที่ต้องการดูข้อมูล<br>4. ระบบแสดงข้อมูลการลาทั้งหมดของพนักงาน |
| **Alternative Flows** | N/A|
| **Postconditions** | ผู้ใช้ได้รับข้อมูลการลาของพนักงานตามที่ต้องการ |
| **Business Rules** | 1. การเข้าถึงข้อมูลต้องเป็นไปตามระดับสิทธิ์ของผู้ใช้ |

---

📌 **หมายเหตุ**:  Use Case Diagram นี้ใช้เป็นแนวทางในการพัฒนาระบบจัดการการลาพนักงาน EdVISORY และอาจมีการปรับเปลี่ยนตามความเหมาะสมระหว่างการพัฒนา 