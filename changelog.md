# 📝 Changelog

## Version 2.0 - Multilingual OCR Support (2026-04-19)

### ✨ New Features

#### 1. รองรับไฟล์รูปภาพ
- ✅ PNG, JPG, JPEG, WEBP
- ✅ OCR ด้วย Google Cloud Vision API
- ✅ คุณภาพการอ่านดีกว่า Tesseract มาก

#### 2. รองรับภาษาอังกฤษ
- ✅ สกัดคำศัพท์ภาษาอังกฤษ
- ✅ แยก glossary ตามภาษา (ไทย / อังกฤษ)
- ✅ แสดงผลแบบ tabs

#### 3. Google Cloud Vision Integration
- ✅ รองรับ Streamlit Secrets
- ✅ ทำงานทั้ง local และ Streamlit Cloud
- ✅ แสดงสถานะ API ใน sidebar

#### 4. UI/UX Improvements
- ✅ Tabs สำหรับ glossary (ทั้งหมด/ไทย/อังกฤษ)
- ✅ สถิติเพิ่มเติม (คำไทย/อังกฤษที่พบบ่อย)
- ✅ แสดงสถานะ dependencies ใน sidebar
- ✅ คำแนะนำชัดเจนกว่า

### 🔧 Technical Changes

**Dependencies:**
- เพิ่ม `google-cloud-vision>=3.4.0`
- เพิ่ม `Pillow>=10.0.0`

**Files Added:**
- `STREAMLIT_SECRETS.md` - วิธีตั้งค่า Google Cloud Vision

**Files Modified:**
- `app.py` - เพิ่ม OCR, multilingual support
- `requirements.txt` - เพิ่ม google-cloud-vision
- `.gitignore` - ป้องกัน commit credentials

### 📊 Glossary Format Change

**เดิม:**
```csv
Term (TH), Frequency, Translation, Notes
```

**ใหม่:**
```csv
Term, Language, Frequency, Translation, Notes
```

### 🚀 Migration Guide

#### จาก v1 → v2:

1. **Update requirements:**
   ```bash
   pip install -r requirements.txt
   ```

2. **ตั้งค่า Google Cloud Vision** (ถ้าต้องการ OCR รูปภาพ):
   - ดู `CLOUD_SETUP.md`
   - ดู `STREAMLIT_SECRETS.md` (สำหรับ Streamlit Cloud)

3. **ไม่มีการเปลี่ยนแปลง breaking changes** สำหรับ PDF extraction

---

## Version 1.0 - Initial Release

### Features
- PDF text extraction (PyMuPDF)
- Thai text normalization
- Segment splitting
- Glossary extraction (Thai only)
- CAT-ready CSV export
- Streamlit UI
