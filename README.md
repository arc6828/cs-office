# 📄 CS-Office: ระบบวิเคราะห์เอกสารหลักสูตรวิทยาการคอมพิวเตอร์
*(Computer Science Curriculum Document Analysis & Analytics)*

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Colab](https://img.shields.io/badge/Run%20in-Google%20Colab-orange.svg)](https://colab.research.google.com/)
[![Focus](https://img.shields.io/badge/Task-Document_Analysis_%26_NLP-green.svg)](#)

ชุดเครื่องมือและสคริปต์ภาษา Python (รองรับการทำงานบน Google Colab และ Local Jupyter Notebook) สำหรับการอ่าน สกัดข้อมูล ตรวจสอบ และวิเคราะห์เอกสารที่เกี่ยวข้องกับการบริหารจัดการหลักสูตรวิทยาการคอมพิวเตอร์

---

## 🎯 วัตถุประสงค์ (Objectives)

1. **สกัดและแปลงข้อมูลจากเอกสารหลักสูตร (Document Parsing & Extraction)**:
   - แปลงไฟล์เอกสารต่างๆ (PDF, Word `.docx`, Excel `.xlsx`) ของเล่มหลักสูตร (มคอ.2), ประมวลรายวิชา (Syllabus / มคอ.3), และรายงานผลรายวิชา (มคอ.5) ให้เป็นข้อมูลที่มีโครงสร้าง (Structured Data)
2. **วิเคราะห์ความสอดคล้องของผลลัพธ์การเรียนรู้ (Curriculum & OBE Alignment)**:
   - ตรวจสอบความเชื่อมโยงระหว่างผลการเรียนรู้ระดับหลักสูตร (PLOs) และระดับรายวิชา (CLOs)
   - วิเคราะห์ Curriculum Mapping ว่าครอบคลุมและกระจายตัวเหมาะสมตามเกณฑ์หรือไม่
3. **ตรวจสอบความสอดคล้องตามเกณฑ์มาตรฐาน (Compliance & QA Checking)**:
   - ตรวจสอบโครงสร้างหน่วยกิต, หมวดวิชา, เงื่อนไขวิชาบังคับก่อน (Prerequisites) ตามเกณฑ์มาตรฐานหลักสูตรระดับอุดมศึกษา
   - สนับสนุนการรวบรวมหลักฐานและวิเคราะห์ข้อมูลเพื่อการประกันคุณภาพ (AUN-QA / EdPEx)
4. **ใช้ประโยชน์จาก AI / NLP / LLM ในงานเอกสารหลักสูตร**:
   - ค้นหา เปรียบเทียบความซ้ำซ้อน และสรุปเนื้อหารายวิชาด้วย Natural Language Processing (NLP)
   - ใช้โมเดลภาษา (LLM) ในการตอบคำถาม ตรวจทาน และให้ข้อเสนอแนะในการปรับปรุงหลักสูตร

---

## 🔍 ฟังก์ชันการวิเคราะห์หลัก (Core Capabilities)

- **📄 Document Extraction**: ดึงข้อความ ตารางคำอธิบายรายวิชา และผลลัพธ์การเรียนรู้จากไฟล์ PDF / DOCX
- **🗺️ Curriculum Mapping Analysis**: วิเคราะห์เมทริกซ์ความรับผิดชอบ (ความรับผิดชอบหลัก/รอง) เชื่อมโยงรายวิชาสู่ PLOs
- **📊 Credit & Course Structure Check**: สรุปสัดส่วนหน่วยกิต แยกตามกลุ่มวิชาและชั้นปี
- **🔗 Prerequisite Chain Visualizer**: วิเคราะห์และสร้างผังความสัมพันธ์ของวิชาบังคับก่อน ป้องกันวงรอบที่ผิดพลาด (Circular Dependencies)
- **💬 Semantic Search & Topic Modeling**: ค้นหาความทับซ้อนของเนื้อหารายวิชา (Course Content Overlap) เพื่อการปรับปรุงหลักสูตร

---

## 📁 โครงสร้างโปรเจกต์ (Project Structure)

```text
cs-office/
├── data/
│   ├── raw/                  # ไฟล์เอกสารต้นฉบับ (PDF, DOCX, XLSX เล่มหลักสูตร/มคอ.)
│   ├── processed/            # ข้อมูลข้อความและตารางที่สกัดแล้ว (JSON, CSV)
│   └── reference/            # เกณฑ์อ้างอิง, รายการ PLOs, มาตรฐานหลักสูตร
├── notebooks/                # Jupyter / Google Colab Notebooks สำหรับการวิเคราะห์
│   ├── 01_extract_curriculum.ipynb    # สกัดข้อมูลจากเล่มหลักสูตร
│   ├── 02_analyze_mapping.ipynb       # วิเคราะห์ Curriculum Mapping (PLOs - CLOs)
│   ├── 03_prerequisites_graph.ipynb   # วิเคราะห์โครงข่ายวิชาบังคับก่อน
│   └── 04_content_similarity.ipynb    # วิเคราะห์ความซ้ำซ้อนและหัวข้อรายวิชา
├── src/                      # ฟังก์ชันและโมดูล Python
│   ├── parsers/              # โมดูลแยกข้อความและตารางจาก PDF/DOCX
│   ├── analyzers/            # การคำนวณสถิติ, ตรวจสอบเกณฑ์, วิเคราะห์ Mapping
│   ├── nlp/                  # การตัดคำภาษาไทย, Embedding, LLM Analysis
│   └── utils/                # ฟังก์ชันนำเข้า/ส่งออกข้อมูล และจัดการกราฟ
├── reports/                  # ผลลัพธ์การวิเคราะห์ (กราฟ, ตารางสรุป, Excel, HTML)
├── requirements.txt          # รายการไลบรารีที่จำเป็น
└── README.md
```

---

## 🛠️ เครื่องมือและไลบรารีที่ใช้ (Libraries & Tools)

- **การจัดการเอกสารและตาราง**:
  - `pypdf`, `pdfplumber`, `PyMuPDF (fitz)` สำหรับไฟล์ PDF
  - `python-docx` สำหรับเอกสาร Word
  - `pandas`, `openpyxl` สำหรับการประมวลผลตารางและ Excel
- **NLP และการวิเคราะห์ข้อความ**:
  - `pythainlp` การตัดคำและการประมวลผลข้อความภาษาไทย
  - `sentence-transformers` / `scikit-learn` สำหรับคำนวณ Text Similarity และ Clustering
  - `openai` / `google-generativeai` สำหรับการวิเคราะห์เชิงลึกด้วย LLM
- **การนำเสนอข้อมูล (Visualization)**:
  - `matplotlib`, `seaborn`, `networkx` สำหรับวาดกราฟโครงข่ายวิชาและ Heatmap

---

## 🚀 การเริ่มต้นใช้งาน (Getting Started)

### การใช้งานบน Google Colab
1. อัปโหลดโฟลเดอร์โปรเจกต์ไปยัง Google Drive
2. นำไฟล์เอกสารหลักสูตร (PDF หรือ DOCX) ไปวางไว้ใน `data/raw/`
3. เปิดสมุดงานในโฟลเดอร์ `notebooks/` ผ่าน Google Colab
4. สั่ง Mount Drive และรันขั้นตอนการวิเคราะห์ตามลำดับ

### การใช้งานบนเครื่อง Local
1. ติดตั้งไลบรารีที่จำเป็น:
   ```bash
   pip install -r requirements.txt
   ```
2. วางเอกสารที่ต้องการวิเคราะห์ใน `data/raw/`
3. รัน Jupyter Notebook หรือสคริปต์วิเคราะห์:
   ```bash
   jupyter notebook
   ```

---

## 📌 ผลลัพธ์ที่ได้จากการวิเคราะห์ (Expected Outputs)

- **ตารางสรุปรายวิชาและหน่วยกิต** ในรูปแบบ Excel / CSV
- **Heatmap เมทริกซ์ความรับผิดชอบ (Curriculum Mapping)** เพื่อดูช่องว่าง (Gaps) ของผลการเรียนรู้
- **ผังโครงข่ายวิชาบังคับก่อน (Prerequisite Graph)** แบบโต้ตอบได้
- **รายงานสรุปข้อสังเกตและข้อเสนอแนะ** สำหรับการปรับปรุงหลักสูตรในรอบถัดไป
