# 🚀 Streamlit Cloud - Quick Start

## ✅ ทำงานได้เลย (PDF รองรับโดยค่าเริ่มต้น)

1. Deploy app ไป Streamlit Cloud ตามปกติ
2. เลือกอัปโหลด **PDF ที่เป็น text-based** (ไม่ใช่ scanned)
3. สกัดข้อความ + Glossary ได้ทันที

---

## 🖼️ เพิ่มสนับสนุน OCR รูปภาพ (PNG/JPG)

### Step 1: ตั้งค่า Google Cloud Vision API

ดู `CLOUD_SETUP.md` และ `STREAMLIT_SECRETS.md`

### Step 2: ใน Streamlit Cloud

1. ไปที่ app settings
2. **Secrets** → เพิ่ม credentials
3. App จะรองรับ PNG/JPG โดยอัตโนมัติ

---

## 📝 File Formats

### ✅ PDF
- ✅ text-based PDF (มีข้อความ)
- ❌ scanned PDF (รูปภาพ) - ต้องมี Google Vision API

### ✅ Images
- ✅ PNG, JPG, JPEG, WEBP (ต้องมี Google Vision API)

---

## 💡 Tips

**ไม่ต้องตั้งค่า Google Vision?**
- ใช้ PDF text-based แทน
- ได้ผลลัพธ์เหมือนกัน ไม่ต้อง API key

**ต้องการ PNG/JPG?**
- ตั้งค่า Google Cloud Vision API
- ยอม 1 นาทีสำหรับเซตอัป
- ใช้ได้จากนั้น

---

## 🔗 Links

- [CLOUD_SETUP.md](./CLOUD_SETUP.md) - ตั้งค่า Google Vision
- [STREAMLIT_SECRETS.md](./STREAMLIT_SECRETS.md) - Streamlit Cloud secrets
- [README.md](./README.md) - Full documentation
