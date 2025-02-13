# 🔗 เอกสารสเปค API (API Specification)

## 1️⃣ บทนำ
**ชื่อโครงการ**: [ระบุชื่อโครงการ]  
**วันที่จัดทำ**: [ระบุวันที่]  
**ผู้รับผิดชอบ**: [ชื่อผู้จัดทำ]  

เอกสารนี้อธิบาย API ที่ใช้ในระบบ รวมถึงโครงสร้าง คำร้องขอ คำตอบ และแนวทางการใช้งาน ✨

---

## 2️⃣ โครงสร้าง API
| Method | Endpoint | คำอธิบาย |
|--------|---------|----------|
| GET | `/api/resource` | ดึงข้อมูลทรัพยากร |
| POST | `/api/resource` | สร้างทรัพยากรใหม่ |
| PUT | `/api/resource/{id}` | อัปเดตทรัพยากร |
| DELETE | `/api/resource/{id}` | ลบทรัพยากร |

---

## 3️⃣ รายละเอียด API
### 🟢 **1. GET /api/resource**
**คำอธิบาย**: ใช้สำหรับดึงข้อมูลทรัพยากรทั้งหมด

**Request:**
```http
GET /api/resource HTTP/1.1
Host: [Base URL]
Authorization: Bearer [token]
```

**Response:**
```json
{
  "status": "success",
  "data": [ {...} ]
}
```

---

### 🟢 **2. POST /api/resource**
**คำอธิบาย**: ใช้สำหรับสร้างทรัพยากรใหม่

**Request:**
```http
POST /api/resource HTTP/1.1
Host: [Base URL]
Content-Type: application/json
Authorization: Bearer [token]

{
  "name": "Example",
  "description": "รายละเอียดของทรัพยากร"
}
```

**Response:**
```json
{
  "status": "success",
  "data": {...}
}
```

---

## 4️⃣ การจัดการข้อผิดพลาด (Error Handling)
| Status Code | ความหมาย | คำอธิบายเพิ่มเติม |
|------------|---------|----------------|
| 200 | OK | คำขอสำเร็จ |
| 400 | Bad Request | ข้อมูลไม่ถูกต้อง |
| 401 | Unauthorized | ไม่มีสิทธิ์เข้าถึง |
| 404 | Not Found | ไม่พบทรัพยากร |
| 500 | Internal Server Error | ข้อผิดพลาดภายในระบบ |

---

📌 **หมายเหตุ**: API อาจมีการเปลี่ยนแปลงตามความต้องการของระบบ 🚀