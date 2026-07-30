# ⚒️ VocabForge v3.0

**سازنده فلش‌کارت هوشمند برای [Leitner Pro](http://readner.eu.cc/)**

VocabForge ابزاری برای استخراج واژگان انگلیسی از فایل‌های PDF و DOCX (مانند Manhattan 500 GRE)، غنی‌سازی خودکار با تعاریف و مترادف‌ها، ترجمه فارسی، و خروجی JSON مستقیم برای ورود به برنامه مرور لایتنر است.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![No Server](https://img.shields.io/badge/No%20Server-100%25%20Client--Side-blue)
![License](https://img.shields.io/badge/License-MIT-green)

---

## ✨ ویژگی‌ها

### 📄 ورود داده
- **DOCX** — پشتیبانی کامل از ساختار Manhattan 500 (جدول ۶ ستونه + سطرهای Example/Context/Note)
- **PDF** — استخراج با محدوده صفحات، حداقل طول کلمه، حداکثر تعداد
- **متن خام** — paste مستقیم متن انگلیسی
- **لیست کلمات** — هر خط یک کلمه

### 🔍 غنی‌سازی خودکار
- **۳ منبع تعریف:**
  - [DictionaryAPI.dev](https://dictionaryapi.dev/) — تلفظ، POS، مترادف، متضاد
  - [Wiktionary REST API](https://en.wiktionary.org/) — پوشش گسترده لغات GRE/SAT
  - [Datamuse API](https://www.datamuse.com/) — روابط واژگانی
- **هوشمند:** تبدیل خودکار فرم‌های مشتق (`-ing`, `-ed`, `-tion`, `-ment`, `-ly`, ...)
- **پردازش موازی:** ۸ درخواست همزمان برای سرعت بالا

### 🌐 ترجمه فارسی
- **ترجمه بر اساس معنی انگلیسی** (نه کلمه به کلمه)
- **۲ منبع ترجمه:**
  - MyMemory API (اولویت اول)
  - Google Translate unofficial (fallback خودکار)
- **پردازش موازی:** ۸ درخواست همزمان

### 🃏 مدیریت کارت‌ها
- نمایش با فیلتر (کامل / ناقص / ترجمه‌شده)
- ویرایش هر فیلد (ترجمه، تعریف، مثال، مترادف، متضاد، یادداشت، نکته مهم)
- تلفظ 🔊
- ذخیره خودکار در localStorage

### 💾 خروجی لایتنر
- JSON با فرمت دقیق `importStateSnapshot`
- شامل تمام فیلدها: definitions, examples, synonyms, antonyms, coreMeaning, collocations, note, trap, FSRS fields
- مستقیماً در لایتنر بخش «بازیابی از پشتیبان» وارد کنید

---

## 🚀 نحوه استفاده

1. فایل `vocabforge.html` را در مرورگر باز کنید
2. از بخش **ورود داده**، فایل DOCX/PDF خود را انتخاب کنید
3. دکمه **🔍 استخراج** را بزنید
4. به بخش **غنی‌سازی** بروید و **🔍 همه** را بزنید
5. **🌐 همه** را برای ترجمه بزنید
6. از بخش **خروجی لایتنر** فایل JSON را دانلود کنید
7. در برنامه لایتنر → بخش خروج/پشتیبان → **بازیابی از پشتیبان** → فایل JSON را انتخاب کنید

---

## 📁 ساختار پروژه

```
VocabForge/
├── vocabforge.html    # کل برنامه (تک فایل، بدون نیاز به سرور)
└── README.md
```

---

## 🔧 پیش‌نیازها

- مرورگر مدرن (Chrome, Firefox, Edge, Safari)
- **بدون نیاز به سرور** — ۱۰۰٪ سمت کلاینت
- **بدون نیاز به نصب** — فقط فایل HTML را باز کنید

---

## 📊 API‌های استفاده‌شده

| API | منبع | محدودیت |
|-----|-------|---------|
| DictionaryAPI.dev | تعریف، تلفظ، مترادف | رایگان، بدون محدودیت |
| Wiktionary REST | تعریف لغات نادر | رایگان، بدون محدودیت |
| Datamuse | روابط واژگانی | رایگان، ۱۰۰K درخواست/روز |
| MyMemory | ترجمه فارسی | ۱۰۰۰ کلمه/روز (ناشناس) |
| Google Translate | ترجمه فارسی (fallback) | غیررسمی، محدودیت نامشخص |

---

## 🔗 ارتباط با لایتنر

VocabForge خروجی JSON تولید می‌کند که مستقیماً با تابع `importStateSnapshot` در لایتنر Pro سازگار است. فیلدهای خروجی:

```json
{
  "words": [
    {
      "id": "...",
      "word": "ephemeral",
      "translation": "زودگذر؛ موقتی",
      "ipa": "/ɪˈfɛm.ər.əl/",
      "partOfSpeech": "adjective",
      "definitions": ["Lasting for a very short time"],
      "examples": ["Fame is ephemeral..."],
      "synonyms": ["transient", "fleeting"],
      "antonyms": ["permanent", "enduring"],
      "coreMeaning": "Lasting for a very short time",
      "collocations": ["ephemeral beauty"],
      "note": "From Greek ephēmeros...",
      "trap": "≠ eternal (ابدی)",
      "box": 0,
      "fsrsState": "new",
      ...
    }
  ],
  "longTerm": [],
  "categories": ["VocabForge"],
  "_version": 1
}
```

---

## 📱 نویسنده

**محسن نیک‌سیرت**
- Telegram: [@mohsenniksirat](https://t.me/mohsenniksirat)

---

## 📄 مجوز

MIT License
