# 🩺 First Aid Dataset

![Banner](https://github.com/alaaels1/first-aid-dataset/blob/main/banner_1.png?raw=true)

## 📌 Overview

This repository contains a structured, production-ready **First Aid dataset** designed to support mobile and desktop applications that provide emergency medical guidance.

The dataset is built to be:

- ⚡ Fast and lightweight for offline use
- 🧠 Structured for smart matching and chatbot systems
- 🌍 Bilingual (Arabic + English keywords support)
- 👶 Includes adult and child instructions

---
## 📁 Dataset Structure

```
FIRST-AID-DATASET/
├── assets/
│   └── images/
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
│   ├── arabic/
│   │   ├── emergency_numbers/
│   │   ├── first_aid_kit/
│   │   └── first_aid_data/
│   │
│   └── english/
│
├── banner_1.png
├── LICENSE
├── README.md
└── .gitattributes
```

---

### 📌 Structure Notes

* **assets/images/**
  Contains all visual assets grouped by medical category for easy access and scalability.

* **data/arabic/**
  The main data source for the application, written بالكامل باللغة العربية.

* **first_aid_data.json**
  يحتوي على الحالات الطبية، التعليمات، الكلمات المفتاحية، وروابط الفيديو.

* **emergency_numbers/**
  أرقام الطوارئ للدول العربية لسهولة الوصول السريع.

* **first_aid_kit/**
  بيانات تجهيز حقيبة الإسعافات الأولية.

* **data/english/**
  مخصص لإضافة نسخة إنجليزية مستقبلًا بدون التأثير على الهيكل الحالي.

---

### 💡 Design Philosophy

* Organized by **category-first structure** for scalability
* Supports **offline usage** بالكامل
* Easy to extend (إضافة حالات أو لغات جديدة بدون تعديل كبير)
* Optimized for **fast lookup and search using keywords**
