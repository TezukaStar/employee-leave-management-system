# 🗂️ เอกสาร ERD (Entity Relationship Diagram)

## 1️⃣ บทนำ
**ชื่อโครงการ**: ระบบจัดการการลาพนักงาน EdVISORY (Employee Leave Management System - EdLeave) 
**วันที่จัดทำ**: 14 มีนาคม 2025  
**ผู้รับผิดชอบ**: อนันดา วุฒวรรรณะ  

เอกสารนี้อธิบายโครงสร้างของฐานข้อมูลโดยใช้ **Entity Relationship Diagram (ERD)** สำหรับระบบจัดการการลาพนักงาน EdVISORY ซึ่งช่วยให้เข้าใจความสัมพันธ์ระหว่างข้อมูลในระบบ ✨

---

## 2️⃣ โครงสร้าง ERD
### 🏛️ **Entity และ Attribute**
1. **EMPLOYEES (พนักงาน)** 👤
   - `employee_id` (PK) - รหัสพนักงาน
   - `first_name` - ชื่อ
   - `last_name` - นามสกุล
   - `email` - อีเมล
   - `password` - รหัสผ่าน
   - `hire_date` - วันที่เริ่มงาน
   - `supervisor_id` (FK → EMPLOYEES.employee_id) - รหัส Supervisor
   - `department_id` (FK → DEPARTMENTS.department_id) - รหัสแผนก
   - `is_supervisor` - เป็น Supervisor
   - `is_department_head` - เป็นหัวหน้าแผนก
   - `is_hr` - เป็น HR
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

2. **DEPARTMENTS (แผนก)** 🏢
   - `department_id` (PK) - รหัสแผนก
   - `department_name` - ชื่อแผนก
   - `department_head_id` (FK → EMPLOYEES.employee_id) - รหัสหัวหน้าแผนก
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

3. **LEAVE_TYPES (ประเภทการลา)** 📝
   - `leave_type_id` (PK) - รหัสประเภทการลา
   - `leave_type_name` - ชื่อประเภทการลา
   - `description` - คำอธิบาย
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

4. **LEAVE_DURATION_TYPES (รูปแบบระยะเวลาการลา)** ⏱️
   - `duration_type_id` (PK) - รหัสรูปแบบระยะเวลา
   - `duration_name` - ชื่อรูปแบบระยะเวลา
   - `duration_value` - ค่าระยะเวลา
   - `description` - คำอธิบาย
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

5. **LEAVE_QUOTAS (โควต้าวันลา)** 🗓️
   - `quota_id` (PK) - รหัสโควต้า
   - `employee_id` (FK → EMPLOYEES.employee_id) - รหัสพนักงาน
   - `leave_type_id` (FK → LEAVE_TYPES.leave_type_id) - รหัสประเภทการลา
   - `year` - ปี
   - `total_days` - จำนวนวันทั้งหมด
   - `used_days` - จำนวนวันที่ใช้แล้ว
   - `remaining_days` - จำนวนวันคงเหลือ
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

6. **LEAVE_REQUESTS (คำขอลา)** 📋
   - `request_id` (PK) - รหัสคำขอลา
   - `employee_id` (FK → EMPLOYEES.employee_id) - รหัสพนักงาน
   - `leave_type_id` (FK → LEAVE_TYPES.leave_type_id) - รหัสประเภทการลา
   - `duration_type_id` (FK → LEAVE_DURATION_TYPES.duration_type_id) - รหัสรูปแบบระยะเวลา
   - `start_date` - วันที่เริ่มลา
   - `end_date` - วันที่สิ้นสุดการลา
   - `total_days` - จำนวนวันลาทั้งหมด
   - `reason` - เหตุผล
   - `requires_dept_head_approval` - ต้องการการอนุมัติจากหัวหน้าแผนก
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

7. **APPROVAL_STATUSES (สถานะการอนุมัติ)** ✅
   - `approval_id` (PK) - รหัสการอนุมัติ
   - `request_id` (FK → LEAVE_REQUESTS.request_id) - รหัสคำขอลา
   - `approver_id` (FK → EMPLOYEES.employee_id) - รหัสผู้อนุมัติ
   - `approver_role` - บทบาทผู้อนุมัติ
   - `status` - สถานะ
   - `comments` - ความคิดเห็น
   - `action_date` - วันที่ดำเนินการ
   - `created_at` - วันที่สร้าง
   - `updated_at` - วันที่อัปเดต

---

## 3️⃣ ความสัมพันธ์ของ Entity
- **EMPLOYEES** 1️⃣ ➝ 🔗 *ยื่น* 🔗 ➝ ♾️ **LEAVE_REQUESTS**
  - *พนักงานหนึ่งคนสามารถยื่นคำขอลาได้หลายรายการ*

- **EMPLOYEES** 1️⃣ ➝ 🔗 *มี* 🔗 ➝ ♾️ **LEAVE_QUOTAS**
  - *พนักงานหนึ่งคนมีโควต้าวันลาได้หลายรายการ (แยกตามประเภทการลาและปี)*

- **EMPLOYEES** ♾️ ➝ 🔗 *สังกัด* 🔗 ➝ 1️⃣ **DEPARTMENTS**
  - *พนักงานหลายคนสังกัดอยู่ในแผนกเดียวกันได้*

- **EMPLOYEES** ♾️ ➝ 🔗 *รายงานต่อ* 🔗 ➝ 1️⃣ **EMPLOYEES**
  - *พนักงานหลายคนสามารถรายงานต่อ Supervisor คนเดียวกันได้*

- **DEPARTMENTS** 1️⃣ ➝ 🔗 *มีหัวหน้า* 🔗 ➝ 1️⃣ **EMPLOYEES**
  - *แผนกแต่ละแผนกมีหัวหน้าแผนกได้หนึ่งคน (ซึ่งก็คือพนักงานคนหนึ่ง)*

- **LEAVE_REQUESTS** 1️⃣ ➝ 🔗 *เป็นประเภท* 🔗 ➝ 1️⃣ **LEAVE_TYPES**
  - *คำขอลาแต่ละรายการต้องเป็นประเภทการลาประเภทใดประเภทหนึ่ง*

- **LEAVE_REQUESTS** 1️⃣ ➝ 🔗 *ใช้* 🔗 ➝ 1️⃣ **LEAVE_DURATION_TYPES**
  - *คำขอลาแต่ละรายการต้องใช้รูปแบบระยะเวลาการลาแบบใดแบบหนึ่ง*

- **LEAVE_REQUESTS** ♾️ ➝ 🔗 *มี* 🔗 ➝ ♾️ **APPROVAL_STATUSES**
  - *คำขอลาหนึ่งรายการสามารถมีสถานะการอนุมัติได้หลายรายการ (ตามลำดับขั้นการอนุมัติ)*

---

## 4️⃣ แผนภาพ ERD
![alt text](svg/er-diagram.svg)

---

## 5️⃣ รายละเอียดเพิ่มเติม

### การออกแบบตาราง EMPLOYEES
- **การใช้ boolean flags**: เลือกใช้ฟิลด์ boolean (is_supervisor, is_department_head, is_hr) เพื่อระบุบทบาทของพนักงานแทนที่จะสร้างตารางแยก เพื่อความยืดหยุ่น ความเรียบง่าย และประสิทธิภาพในการค้นหา
- **Self-referencing relationship**: ใช้ FK supervisor_id ที่อ้างอิงกลับมาที่ตาราง EMPLOYEES เพื่อจัดเก็บโครงสร้างการรายงานผลในองค์กร

### การออกแบบตาราง LEAVE_QUOTAS
- แยกเก็บโควต้าตามประเภทการลาและปี เพื่อให้สามารถกำหนดโควต้าแตกต่างกันได้ตามนโยบายบริษัท
- เก็บทั้งจำนวนวันลาทั้งหมด (total_days), จำนวนที่ใช้ไปแล้ว (used_days) และจำนวนคงเหลือ (remaining_days) เพื่อความสะดวกในการคำนวณและแสดงผล

### การออกแบบตาราง LEAVE_REQUESTS
- มีฟิลด์ requires_dept_head_approval เพื่อระบุว่าเป็นคำขอลาที่ต้องผ่านการอนุมัติจากหัวหน้าแผนกหรือไม่ (กรณีลา 5 วันขึ้นไป)
- เก็บทั้งวันที่เริ่มและวันที่สิ้นสุดการลา ร่วมกับจำนวนวันลาทั้งหมด เพื่อความสะดวกในการคำนวณและตรวจสอบ

### การออกแบบตาราง APPROVAL_STATUSES
- ใช้ตารางแยกเก็บประวัติการอนุมัติทั้งหมด เพื่อให้สามารถติดตามลำดับขั้นตอนการอนุมัติได้
- มีฟิลด์ approver_role เพื่อระบุว่าผู้อนุมัติมีบทบาทใดในกระบวนการอนุมัติ (Supervisor, หัวหน้าแผนก, HR)

---

📌 **หมายเหตุ**: ERD นี้ครอบคลุมฟังก์ชันการทำงานและข้อมูลที่จำเป็นสำหรับระบบจัดการการลาพนักงานตามที่ระบุไว้ในเอกสาร SRS และ Use Case 🚀