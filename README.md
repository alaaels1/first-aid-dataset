# 🩺 First Aid Dataset

![Banner](https://github.com/alaaels1/first-aid-dataset/blob/main/banner.png?raw=true)

## 📌 Overview

This repository contains a structured, production-ready **First Aid dataset** designed to support mobile and desktop applications that provide emergency medical guidance.

The dataset is built to be:

- ⚡ Fast and lightweight for offline use
- 🧠 Structured for smart matching and chatbot systems
- 🌍 Bilingual (Arabic + English keywords support)
- 👶 Includes adult and child instructions

---

### 📁 Dataset Structure

```bash
FIRST-AID-DATASET/
├── assets/
│   └── images/                          # كل الصور الخاصة بالإسعافات الأولية
│       ├── allergies_skin/
│       ├── burns/
│       ├── cpr/
│       ├── diabetes/
│       ├── digestive/
│       ├── emergency/
│       ├── environmental/
│       ├── eye_injury/
│       ├── general_illness/
│       ├── musculoskeletal/
│       ├── neurological/
│       ├── poisoning/
│       ├── respiratory/
│       ├── stings/
│       └── wounds_bleeding/
│
├── data/
│   ├── arabic/                          # البيانات باللغة العربية
│   │   ├── emergency_numbers/
│   │   │   └── arab_countries_emergency_numbers.json
│   │   │
│   │   ├── first_aid_kit/
│   │   │   └── first_aid_kit.json
│   │   │
│   │   └── first_aid_data/
│   │       └── first_aid_data.json
│   │
│   └── english/                         # (فارغ حالياً - للنسخة الإنجليزي)
│
├── banner_1.png
├── LICENSE
├── README.md
└── .gitattributes
```
