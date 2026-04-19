# 🔑 Google Cloud Vision API Setup for Streamlit Cloud

## สำหรับ Streamlit Cloud Deployment

### Step 1: สร้าง Service Account Key

1. ไปที่ https://console.cloud.google.com
2. เปิด Project ของคุณ
3. **IAM & Admin** → **Service Accounts**
4. เลือก service account
5. **Keys** → **Add Key** → **Create new key** → **JSON**
6. ดาวน์โหลดไฟล์ JSON

### Step 2: เพิ่ม Secrets ใน Streamlit Cloud

1. ไปที่ Streamlit Cloud dashboard
2. เลือก app ของคุณ
3. **Settings** → **Secrets**
4. เพิ่ม secrets ดังนี้:

```toml
# .streamlit/secrets.toml
[gcp_service_account]
type = "service_account"
project_id = "YOUR_PROJECT_ID"
private_key_id = "YOUR_PRIVATE_KEY_ID"
private_key = "-----BEGIN PRIVATE KEY-----\nYOUR_PRIVATE_KEY\n-----END PRIVATE KEY-----\n"
client_email = "YOUR_SERVICE_ACCOUNT_EMAIL"
client_id = "YOUR_CLIENT_ID"
auth_uri = "https://accounts.google.com/o/oauth2/auth"
token_uri = "https://oauth2.googleapis.com/token"
auth_provider_x509_cert_url = "https://www.googleapis.com/oauth2/v1/certs"
client_x509_cert_url = "YOUR_CERT_URL"
```

**วิธีหาค่า:**
- เปิดไฟล์ JSON ที่ดาวน์โหลด
- Copy ค่าทั้งหมดไปใส่ใน secrets

### Step 3: อัปเดต Code (ถ้าจำเป็น)

app.py ปัจจุบันจะใช้ `GOOGLE_APPLICATION_CREDENTIALS` environment variable

สำหรับ Streamlit Cloud ให้เพิ่มโค้ดนี้ด้านบนของ app.py:

```python
import streamlit as st
import json
import os

# Load Google credentials from Streamlit secrets
if "gcp_service_account" in st.secrets:
    # Create credentials file from secrets
    gcp_credentials = st.secrets["gcp_service_account"]
    credentials_dict = dict(gcp_credentials)
    
    # Save to temporary file
    with open("gcp-credentials.json", "w") as f:
        json.dump(credentials_dict, f)
    
    # Set environment variable
    os.environ["GOOGLE_APPLICATION_CREDENTIALS"] = "gcp-credentials.json"
```

---

## สำหรับ Local Development

### Option 1: Environment Variable

```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/your-key.json"
streamlit run app.py
```

### Option 2: Streamlit Secrets (Local)

สร้างไฟล์ `.streamlit/secrets.toml` ในโปรเจกต์:

```toml
[gcp_service_account]
type = "service_account"
project_id = "..."
# ... (เหมือนด้านบน)
```

---

## 🧪 ทดสอบ

```python
from google.cloud import vision

def test_vision_api():
    client = vision.ImageAnnotatorClient()
    print("✅ Google Cloud Vision API configured successfully!")

test_vision_api()
```

---

## 💡 Tips

- ✅ **ไม่ควร commit** ไฟล์ credentials (.json) เข้า Git
- ✅ เพิ่ม `*.json` และ `.streamlit/secrets.toml` ใน `.gitignore`
- ✅ ใช้ Streamlit Secrets สำหรับ production
- ✅ ใช้ environment variable สำหรับ local dev

---

## 📚 อ้างอิง

- [Streamlit Secrets Management](https://docs.streamlit.io/streamlit-community-cloud/deploy-your-app/secrets-management)
- [Google Cloud Vision API](https://cloud.google.com/vision/docs)
