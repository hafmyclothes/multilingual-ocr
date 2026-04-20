# 🖼️ EasyOCR - Image OCR Support

**ไม่ต้อง Google Cloud Vision API!** ใช้ EasyOCR แทน

## ✨ Features

- ✅ PNG, JPG, JPEG, WEBP
- ✅ รองรับไทย + อังกฤษ
- ✅ ไม่ต้อง API key
- ✅ ทำงานบน Streamlit Cloud ได้
- ✅ ฟรี 100%

---

## 🚀 Setup

### Local Development

```bash
pip install easyocr
streamlit run app.py
```

### Streamlit Cloud

EasyOCR จะติดตั้งอัตโนมัติจาก `requirements.txt`

---

## ⏱️ Performance Notes

**ครั้งแรก:** ใช้เวลา 2-3 นาทีในการดาวน์โหลดโมเดล

**ครั้งต่อไป:** ใช้เวลา 5-15 วินาทีต่อภาพ (ขึ้นกับขนาด)

**Tips:**
- ใช้ภาพที่คมชัด จะ OCR ดีกว่า
- ลดขนาดภาพถ้า lag
- รูปที่โอเคฟี่: ~1000x1000 px

---

## 🆚 EasyOCR vs Google Cloud Vision

| | EasyOCR | Google Vision |
|---|---------|--------------|
| ค่าใช้ | ฟรี | $1.50/1000 images |
| Setup | ติดตั้ง 1 ครั้ง | ต้อง API key |
| Speed | 5-15 วิ/ภาพ | 1-3 วิ/ภาพ |
| Accuracy | ดี | ดีกว่า |
| Thai Support | ✅ | ✅ |

---

## 📝 Examples

### PDF + Thai/English Glossary
```
อัปโหลด PDF → สกัดข้อความ → ถอดศัพท์ → ดาวน์โหลด CSV
```

### PNG/JPG + Thai/English Glossary
```
อัปโหลดรูป → EasyOCR → สกัดข้อความ → ถอดศัพท์ → ดาวน์โหลด CSV
```

---

## 🐛 Troubleshooting

### "ModuleNotFoundError: No module named 'easyocr'"

```bash
pip install easyocr
```

### "OCR is slow / hanging"

- ครั้งแรกจะช้า (ดาวน์โหลดโมเดล)
- ครั้งต่อไปจะเร็ว
- ลดขนาดภาพ

### "Low accuracy on Thai text"

- ใช้รูปที่คมชัด
- หลีกเลี่ยงรูปที่ distorted/rotated
- ลองปรับแสง/contrast

---

## 📚 References

- [EasyOCR GitHub](https://github.com/JaidedAI/EasyOCR)
- [Supported Languages](https://github.com/JaidedAI/EasyOCR#supported-languages)
