# Chapter 42: PDF Tools in Termux

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  📄 CHAPTER 42: PDF TOOLS IN TERMUX                                          ║
║  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  ║
║                                                                               ║
║  📑 Merge & Split | 📝 Text Extraction | 🔐 Password Protect | 🗜️ Compress   ║
║  🖼️ PDF ↔ Images | 🔄 Format Convert | 📊 Professional Results               ║
║                                                                               ║
║  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          ║
║  │   Module 7  │  │  Chapter    │  │  Duration   │  │  Difficulty │          ║
║  │  Utilities  │  │  42 of 61   │  │  15-20 Min  │  │  ⭐⭐ Inter. │          ║
║  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘          ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

> **Module:** 7 - Utilities  
> **Chapter:** 42 of 61  
> **Duration:** 15-20 Minutes  
> **Difficulty:** ⭐⭐ Intermediate  

---

## 📋 Chapter Overview

| Section | Content |
|---------|---------|
| Video Script | Complete Hindi narration with timestamps |
| Technical Guide | PDF manipulation tools in Termux |
| Tools Covered | pdftk, qpdf, poppler-utils, PyPDF2 |
| Operations | Merge, split, convert, compress, protect |
| Commands Reference | 25+ PDF commands |
| Practice Exercises | Hands-on PDF tasks |
| Troubleshooting | Common PDF issues |
| Video Assets | Thumbnail, description, tags |

---

## 🎬 VIDEO SCRIPT (Complete Hindi Narration)

```
═══════════════════════════════════════════════════════════════════════════════
TERMUX FULL COURSE - CHAPTER 42
Title: PDF Tools in Termux | Complete PDF Manipulation Guide | T3rmuxk1ng
Duration: 15-20 Minutes
═══════════════════════════════════════════════════════════════════════════════

[INTRO - 0:00 to 0:45]
─────────────────────────────────────────────────────────────────────────────

Namaskar Dosto! Welcome back to Termux Full Course by T3rmuxk1ng!

Main aapka host hoon aur aaj hum seekhenge ek bahut hi useful topic -
PDF Manipulation in Termux!

Sabhi ko PDF files se waasta padta hai - documents, reports, e-books,
forms, certificates. Lekin kya aap jante ho ki aapke Android phone se
bhi aap PDF files ko fully control kar sakte ho?

Haan! Termux mein bahut saare powerful PDF tools available hain - 
merge karna, split karna, compress karna, password lagana, text 
extract karna - sab kuch possible hai!

Aur sabse best baat? Kisi bhi paid software ki zarurat nahi.
Sab kuch FREE mein, command line se.

To chaliye shuru karte hain! Video like karein, subscribe karein,
aur notification bell on karein.

---

[SECTION 1: PDF TOOLS OVERVIEW - 0:45 to 3:00]
─────────────────────────────────────────────────────────────────────────────

Termux mein PDF ke liye hum use karenge mainly 4 tools:

┌─────────────────────────────────────────────────────────────────────────┐
│                    TERMUX PDF TOOLS OVERVIEW                            │
├──────────────────────┬──────────────────────────────────────────────────┤
│ Tool                 │ Purpose                                         │
├──────────────────────┼──────────────────────────────────────────────────┤
│ pdftk                │ PDF Toolkit - merge, split, rotate, encrypt     │
│ qpdf                 │ Linearize, encrypt, decrypt, inspect PDFs      │
│ poppler-utils        │ PDF to text, HTML, images conversion           │
│ ImageMagick          │ Images to PDF, PDF to images                   │
│ PyPDF2 (Python)      │ Programmatic PDF manipulation                  │
└──────────────────────┴──────────────────────────────────────────────────┘

Har tool ka apna specialization hai:

pdftk - Ye Swiss Army Knife hai PDF ka. Merge, split, rotate, encrypt,
decrypt, watermark - sab kar sakta hai. Sabse commonly used tool.

qpdf - Ye structure-preserving operations ke liye best hai. Linearization,
encryption, optimization mein expert.

poppler-utils - Ye conversion ke liye hai. PDF ko text mein, HTML mein,
ya images mein convert karna ho to ye use karein.

PyPDF2 - Agar aap Python developer hain, to programmatically PDF 
manipulate kar sakte ho scripts likh ke.

Sabse pehle in tools ko install karte hain.

---

[SECTION 2: INSTALLATION - 3:00 to 5:00]
─────────────────────────────────────────────────────────────────────────────

Sabse pehle Termux ko update karein:

    pkg update && pkg upgrade -y

Ab PDF tools install karein:

[INSTALL PDFTK]

    pkg install pdftk

pdftk install ho gaya. Check karein:

    pdftk --version

[INSTALL QPDF]

    pkg install qpdf

qpdf bhi install. Check karein:

    qpdf --version

[INSTALL POPPLER-UTILS]

    pkg install poppler

Ye package pdftotext, pdftohtml, pdfimages tools deta hai.

Check karein:

    pdftotext -v

[INSTALL IMAGEMAGICK]

    pkg install imagemagick

Ye images ko PDF mein convert karne ke liye chahiye.

Check karein:

    convert --version

[INSTALL PYTHON PyPDF2]

Agar Python installed nahi hai:

    pkg install python -y

Ab PyPDF2 install karein:

    pip install PyPDF2

Check karein:

    python -c "import PyPDF2; print(PyPDF2.__version__)"

Saare tools ready hain! Ab real operations start karte hain.

---

[SECTION 3: PDF MERGE - 5:00 to 7:00]
─────────────────────────────────────────────────────────────────────────────

Sabse common operation - Multiple PDFs ko ek mein combine karna.

[SCENARIO: Do PDF files ko merge karna]

Maan lijiye aapke paas do PDF files hain:
- file1.pdf
- file2.pdf

Inhe merged.pdf mein combine karna hai.

[METHOD 1: Using pdftk]

    pdftk file1.pdf file2.pdf cat output merged.pdf

Samjhein command ko:
- pdftk: Tool ka naam
- file1.pdf file2.pdf: Input files
- cat: Concatenate operation
- output merged.pdf: Output file name

[METHOD 2: Using qpdf]

    qpdf --empty --pages file1.pdf file2.pdf -- merged.pdf

[METHOD 3: Multiple files with wildcard]

Agar bahut saare PDFs hain:

    pdftk *.pdf cat output all_merged.pdf

Ya specific order mein:

    pdftk chapter1.pdf chapter2.pdf chapter3.pdf cat output book.pdf

[METHOD 4: Selective page merge]

    pdftk A=file1.pdf B=file2.pdf cat A1-3 B2-5 output merged.pdf

Ye command:
- File1 se page 1-3 le raha hai
- File2 se page 2-5 le raha hai
- Combined output de raha hai

Bahut powerful feature hai ye!

---

[SECTION 4: PDF SPLIT - 7:00 to 9:00]
─────────────────────────────────────────────────────────────────────────────

Abulta operation - Ek bade PDF ko multiple files mein todna.

[SCENARIO: 100 page PDF ko alag files mein split karna]

[METHOD 1: Split into individual pages]

    pdftk large.pdf burst output page_%d.pdf

Ye command har page ke liye alag file banayegi:
- page_1.pdf
- page_2.pdf
- ... and so on

[METHOD 2: Extract specific pages]

Sirf page 5-10 extract karna hai:

    pdftk input.pdf cat 5-10 output extracted.pdf

[METHOD 3: Extract multiple ranges]

    pdftk input.pdf cat 1-5 10-15 20-end output selected.pdf

[METHOD 4: Extract single page]

    pdftk input.pdf cat 5 output page5.pdf

[METHOD 5: Split using qpdf]

    qpdf --split-pages input.pdf output_page_%d.pdf

[SCENARIO: Chapter-wise split]

Maan lijiye aapko ek PDF hai jisme 5 chapters hain, har chapter 20 pages:

    pdftk book.pdf cat 1-20 output chapter1.pdf
    pdftk book.pdf cat 21-40 output chapter2.pdf
    pdftk book.pdf cat 41-60 output chapter3.pdf
    pdftk book.pdf cat 61-80 output chapter4.pdf
    pdftk book.pdf cat 81-100 output chapter5.pdf

---

[SECTION 5: PDF TO TEXT - 9:00 to 10:30]
─────────────────────────────────────────────────────────────────────────────

Kabhi kabhi PDF se text extract karna padta hai - data extraction,
copy paste, analysis ke liye.

[METHOD 1: Using pdftotext]

    pdftotext input.pdf output.txt

Ye command PDF ka text extract karke output.txt mein save karegi.

[METHOD 2: View in terminal]

Bina file create kiye direct terminal mein dekhein:

    pdftotext input.pdf -

Dash (-) ka matlab stdout - output screen pe.

[METHOD 3: Preserve layout]

    pdftotext -layout input.pdf output.txt

-layout flag original formatting preserve karta hai.

[METHOD 4: Specific pages]

    pdftotext -f 1 -l 5 input.pdf output.txt

-f: first page
-l: last page

Matlab page 1 se 5 tak ka text extract karega.

[METHOD 5: Extract from encrypted PDF]

    pdftotext -upw password input.pdf output.txt

-upw: user password

[METHOD 6: Using Python PyPDF2]

    python -c "
import PyPDF2
with open('input.pdf', 'rb') as f:
    reader = PyPDF2.PdfReader(f)
    for page in reader.pages:
        print(page.extract_text())
"

Ye Python se text extraction ka tareeka hai.

---

[SECTION 6: PDF TO IMAGES & IMAGES TO PDF - 10:30 to 12:30]
─────────────────────────────────────────────────────────────────────────────

[PDF TO IMAGES]

PDF ke pages ko images mein convert karna:

[METHOD 1: Using pdftoppm]

    pdftoppm input.pdf output -png

Ye command banayegi:
- output-1.png
- output-2.png
- ...

[METHOD 2: JPEG format]

    pdftoppm input.pdf output -jpeg

[METHOD 3: Specific page to image]

    pdftoppm -f 1 -l 1 input.pdf output -png

Sirf first page image mein convert hoga.

[METHOD 4: High resolution]

    pdftoppm -r 300 input.pdf output -png

-r 300: 300 DPI resolution

[IMAGES TO PDF]

Ab ulta - images ko PDF mein:

[METHOD 1: Using ImageMagick]

    convert image1.jpg image2.jpg output.pdf

[METHOD 2: All images in folder]

    convert *.jpg combined.pdf

[METHOD 3: With compression]

    convert -quality 80 image.jpg output.pdf

-quality 80: 80% quality, smaller file size

[METHOD 4: Multiple images with specific order]

    convert page1.png page2.png page3.png document.pdf

---

[SECTION 7: PDF COMPRESSION - 12:30 to 14:00]
─────────────────────────────────────────────────────────────────────────────

Bade PDF files ko compress karna bahut common requirement hai.

[METHOD 1: Using qpdf]

    qpdf --compress-streams=yes input.pdf compressed.pdf

[METHOD 2: Using Ghostscript]

    gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=compressed.pdf input.pdf

Ye command file size significantly reduce karti hai.

[METHOD 3: Different compression levels]

Screen quality (72dpi, smallest):
    gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=small.pdf input.pdf

Ebook quality (150dpi, medium):
    gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=medium.pdf input.pdf

Printer quality (300dpi, large):
    gs -sDEVICE=pdfwrite -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile=print.pdf input.pdf

[METHOD 4: Using pdftk with compression]

    pdftk input.pdf output compressed.pdf compress

[COMPARISON]

┌─────────────────────────────────────────────────────────────────────────┐
│                    COMPRESSION COMPARISON                               │
├──────────────────────┬──────────────────┬───────────────────────────────┤
│ Method               │ Quality          │ Size Reduction               │
├──────────────────────┼──────────────────┼───────────────────────────────┤
│ /screen              │ Low              │ 70-90% smaller               │
│ /ebook               │ Medium           │ 50-70% smaller               │
│ /printer             │ High             │ 20-40% smaller               │
│ pdftk compress       │ Original         │ 10-30% smaller               │
└──────────────────────┴──────────────────┴───────────────────────────────┘

---

[SECTION 8: PDF PASSWORD PROTECTION - 14:00 to 16:00]
─────────────────────────────────────────────────────────────────────────────

PDF files ko password se protect karna sensitive documents ke liye important hai.

[METHOD 1: Using pdftk - Add password]

    pdftk input.pdf output protected.pdf user_pw MyPassword

user_pw: User password - PDF khulne ke liye chahiye

[METHOD 2: Owner password (restrictions)]

    pdftk input.pdf output protected.pdf user_pw UserPass owner_pw OwnerPass

owner_pw: Owner password - permissions change karne ke liye

[METHOD 3: With permissions]

    pdftk input.pdf output protected.pdf user_pw MyPassword allow AllFeatures

Specific permissions:

    pdftk input.pdf output protected.pdf user_pw MyPassword \
        allow printing copy modifyannotations

allow options:
- printing: Print allowed
- copy: Copy text allowed
- modifyannotations: Annotations modify allowed
- AllFeatures: Everything allowed

[METHOD 4: Using qpdf]

    qpdf --encrypt userpass ownerpass 256 -- input.pdf output.pdf

256-bit encryption - very secure!

128-bit encryption:

    qpdf --encrypt userpass ownerpass 128 -- input.pdf output.pdf

---

[SECTION 9: PDF PASSWORD REMOVAL - 16:00 to 17:30]
─────────────────────────────────────────────────────────────────────────────

[IMPORTANT NOTE]

Sirf apne documents ke liye use karein. Doosron ki files
password remove karna illegal ho sakta hai!

[METHOD 1: Using pdftk]

Agar aap password jante hain:

    pdftk protected.pdf input_pw MyPassword output unprotected.pdf

[METHOD 2: Using qpdf]

    qpdf --password=MyPassword --decrypt protected.pdf output.pdf

[METHOD 3: Using Ghostscript]

    gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=output.pdf protected.pdf

Ye method sometimes bina password ke bhi kaam karta hai
agar PDF weak encryption use kar raha hai.

[METHOD 4: Python script for known password]

    python -c "
import PyPDF2
reader = PyPDF2.PdfReader('protected.pdf')
if reader.is_encrypted:
    reader.decrypt('MyPassword')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    writer.add_page(page)
with open('unprotected.pdf', 'wb') as f:
    writer.write(f)
"

---

[SECTION 10: PDF ROTATION - 17:30 to 18:30]
─────────────────────────────────────────────────────────────────────────────

Kabhi kabhi PDF pages ulte hot hain - rotation fix karna padta hai.

[METHOD 1: Rotate all pages]

    pdftk input.pdf cat 1-endright output rotated.pdf

Rotation options:
- right: 90 degrees clockwise
- left: 90 degrees counter-clockwise
- down: 180 degrees

[METHOD 2: Rotate specific page]

    pdftk input.pdf cat 1 2right 3-end output rotated.pdf

Ye command:
- Page 1: No rotation
- Page 2: Rotate right (90°)
- Pages 3-end: No rotation

[METHOD 3: Rotate using qpdf]

    qpdf input.pdf output.pdf --rotate=+90:1,2,3

+90: Rotate 90° clockwise
-90: Rotate 90° counter-clockwise
+180: Rotate 180°
:1,2,3: Apply to pages 1, 2, 3

[METHOD 4: Rotate all pages]

    qpdf input.pdf output.pdf --rotate=+90

---

[SECTION 11: PYTHON PyPDF2 SCRIPTING - 18:30 to 19:30]
─────────────────────────────────────────────────────────────────────────────

Python se advanced PDF operations automate kar sakte ho.

[EXAMPLE 1: Get PDF info]

    python -c "
import PyPDF2
with open('document.pdf', 'rb') as f:
    reader = PyPDF2.PdfReader(f)
    print(f'Pages: {len(reader.pages)}')
    print(f'Info: {reader.metadata}')
"

[EXAMPLE 2: Merge PDFs using Python]

    python << 'EOF'
import PyPDF2
merger = PyPDF2.PdfMerger()
merger.append('file1.pdf')
merger.append('file2.pdf')
merger.write('merged.pdf')
merger.close()
EOF

[EXAMPLE 3: Split PDF using Python]

    python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('large.pdf')
for i, page in enumerate(reader.pages):
    writer = PyPDF2.PdfWriter()
    writer.add_page(page)
    with open(f'page_{i+1}.pdf', 'wb') as f:
        writer.write(f)
EOF

[EXAMPLE 4: Add watermark]

    python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('input.pdf')
watermark = PyPDF2.PdfReader('watermark.pdf')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    page.merge_page(watermark.pages[0])
    writer.add_page(page)
with open('watermarked.pdf', 'wb') as f:
    writer.write(f)
EOF

---

[SECTION 12: SUMMARY & CONCLUSION - 19:30 to 21:00]
─────────────────────────────────────────────────────────────────────────────

To dosto, Chapter 42 complete! Let's summarize:

┌─────────────────────────────────────────────────────────────────────────┐
│                    CHAPTER 42 - KEY TAKEAWAYS                           │
├─────────────────────────────────────────────────────────────────────────┤
│ ✅ PDF Tools Installation - pdftk, qpdf, poppler, imagemagick          │
│ ✅ PDF Merge - Multiple files ko combine karna                         │
│ ✅ PDF Split - Pages extract karna, separate files banana              │
│ ✅ PDF to Text - Text extraction for data analysis                     │
│ ✅ PDF to Images - Pages ko PNG/JPEG mein convert karna                │
│ ✅ Images to PDF - Photos ko document mein banana                       │
│ ✅ PDF Compression - File size reduce karna                            │
│ ✅ Password Protection - Security add karna                            │
│ ✅ Password Removal - Encryption remove karna                          │
│ ✅ PDF Rotation - Pages ko correct orientation mein karna              │
│ ✅ Python PyPDF2 - Programmatic PDF manipulation                       │
└─────────────────────────────────────────────────────────────────────────┘

Important Commands yaad rakhein:

┌─────────────────────────────────────────────────────────────────────────┐
│                    QUICK COMMAND REFERENCE                              │
├─────────────────────────────────────────────────────────────────────────┤
│ pdftk f1.pdf f2.pdf cat output merged.pdf    │ Merge PDFs              │
│ pdftk input.pdf burst                        │ Split into pages        │
│ pdftotext input.pdf output.txt               │ Extract text            │
│ pdftoppm input.pdf out -png                  │ PDF to images           │
│ convert *.jpg output.pdf                     │ Images to PDF           │
│ qpdf --compress-streams=yes i.pdf o.pdf      │ Compress                │
│ pdftk i.pdf output o.pdf user_pw pass        │ Add password            │
│ pdftk i.pdf input_pw pass output o.pdf       │ Remove password         │
│ pdftk i.pdf cat 1-endright output o.pdf      │ Rotate pages            │
└─────────────────────────────────────────────────────────────────────────┘

Next Chapter 43 mein hum seekhenge:
- Task Automation in Termux
- Cron jobs setup
- Automated backup scripts
- Scheduled tasks

Agar ye video helpful lagi, to:
👍 Like button press karein
🔔 Subscribe karein, notification bell on karein
💬 Koi sawal ho to comment mein poochein
📤 Share karein friends ke saath

Main har comment ka reply karta hoon.

Thank you for watching! See you in Chapter 43!

═══════════════════════════════════════════════════════════════════════════════
```

---

## 📖 TECHNICAL GUIDE

### 1. PDF Tools Architecture in Termux

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PDF TOOLS ECOSYSTEM IN TERMUX                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    PDF MANIPULATION LAYER                        │   │
│   │                                                                   │   │
│   │   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐       │   │
│   │   │  pdftk   │  │   qpdf   │  │ poppler  │  │imagemagick│      │   │
│   │   │          │  │          │  │          │  │          │       │   │
│   │   │ • Merge  │  │ • Linear │  │ • ToText │  │ • ToPDF  │       │   │
│   │   │ • Split  │  │ • Encrypt│  │ • ToHTML │  │ • ToImg  │       │   │
│   │   │ • Rotate │  │ • Optimize│ │ • ToImg  │  │ • Resize │       │   │
│   │   │ • Encrypt│  │ • Inspect│  │ • Extract│  │ • Convert│       │   │
│   │   └──────────┘  └──────────┘  └──────────┘  └──────────┘       │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    PROGRAMMING LAYER                             │   │
│   │                                                                   │   │
│   │   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │   │
│   │   │   PyPDF2     │  │   reportlab  │  │   pypdf      │         │   │
│   │   │   (Python)   │  │   (Python)   │  │   (Python)   │         │   │
│   │   └──────────────┘  └──────────────┘  └──────────────┘         │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                   │                                      │
│                                   ▼                                      │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                    BACKEND LIBRARIES                             │   │
│   │                                                                   │   │
│   │   libjpeg, libpng, zlib, freetype, ghostscript                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2. Tool Comparison

| Feature | pdftk | qpdf | poppler | ImageMagick |
|---------|-------|------|---------|-------------|
| Merge PDFs | ✅ | ✅ | ❌ | ❌ |
| Split PDFs | ✅ | ✅ | ❌ | ❌ |
| Encrypt | ✅ | ✅ | ❌ | ❌ |
| Decrypt | ✅ | ✅ | ❌ | ❌ |
| Rotate | ✅ | ✅ | ❌ | ✅ |
| Compress | ✅ | ✅ | ❌ | ✅ |
| Text Extract | ❌ | ❌ | ✅ | ❌ |
| HTML Convert | ❌ | ❌ | ✅ | ❌ |
| Image Extract | ❌ | ❌ | ✅ | ✅ |
| PDF to Image | ❌ | ❌ | ✅ | ✅ |
| Image to PDF | ❌ | ❌ | ❌ | ✅ |
| Watermark | ✅ | ❌ | ❌ | ✅ |

### 3. PDF Encryption Levels

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PDF ENCRYPTION LEVELS                                │
├────────────────┬────────────────────────────────────────────────────────┤
│ Encryption     │ Description                                            │
├────────────────┼────────────────────────────────────────────────────────┤
│ 40-bit RC4     │ Weak, easily breakable (PDF 1.3)                       │
│ 128-bit RC4    │ Better, common in older PDFs (PDF 1.4)                 │
│ 128-bit AES    │ Good security (PDF 1.5)                                │
│ 256-bit AES    │ Strong, recommended (PDF 1.6+)                         │
└────────────────┴────────────────────────────────────────────────────────┘

qpdf supports: 40, 128, 256-bit encryption
pdftk supports: 40, 128-bit encryption
```

### 4. PDF Page Ranges Syntax

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PAGE RANGE SYNTAX (pdftk)                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│ <page-range>                                                             │
│                                                                          │
│ Examples:                                                                │
│   1           - Page 1 only                                             │
│   1-5         - Pages 1 through 5                                       │
│   5-end       - Page 5 to last page                                     │
│   1-end       - All pages                                               │
│   odd         - All odd-numbered pages                                  │
│   even        - All even-numbered pages                                 │
│   1-5 10-15   - Pages 1-5 AND 10-15                                     │
│                                                                          │
│ Rotation suffixes:                                                       │
│   1right      - Page 1 rotated 90° clockwise                            │
│   1left       - Page 1 rotated 90° counter-clockwise                    │
│   1down       - Page 1 rotated 180°                                     │
│                                                                          │
│ Multiple files:                                                          │
│   A=file1.pdf B=file2.pdf                                               │
│   cat A1-3 B2-5 A6-end                                                  │
│   (Pages from A: 1-3 and 6-end, from B: 2-5)                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 INSTALLATION GUIDE

### Complete PDF Tools Setup

```bash
# Update Termux first
pkg update && pkg upgrade -y

# Install core PDF tools
pkg install pdftk -y
pkg install qpdf -y
pkg install poppler -y
pkg install ghostscript -y
pkg install imagemagick -y

# Install Python for PyPDF2
pkg install python -y
pip install PyPDF2
pip install pypdf  # Newer version
pip install reportlab  # For PDF creation

# Verify installations
pdftk --version
qpdf --version
pdftotext -v
gs --version
convert --version
python -c "import PyPDF2; print('PyPDF2 OK')"
```

### Tool-Specific Details

```bash
# pdftk - PDF Toolkit
pkg install pdftk
# Provides: pdftk command
# Features: merge, split, rotate, encrypt, decrypt

# qpdf - PDF Transformation
pkg install qpdf
# Provides: qpdf command
# Features: linearize, encrypt, decrypt, inspect, optimize

# poppler - PDF Rendering
pkg install poppler
# Provides: pdftotext, pdftohtml, pdfimages, pdftoppm, pdfinfo
# Features: text extraction, HTML conversion, image extraction

# ghostscript - PDF Processing
pkg install ghostscript
# Provides: gs command
# Features: PDF compression, conversion, manipulation

# imagemagick - Image Processing
pkg install imagemagick
# Provides: convert, identify, montage
# Features: image to PDF, PDF to image, resize, format conversion
```

---

## 📋 COMMANDS REFERENCE

### PDF Merge Commands

```bash
# Basic merge two files
pdftk file1.pdf file2.pdf cat output merged.pdf

# Merge multiple files
pdftk file1.pdf file2.pdf file3.pdf cat output merged.pdf

# Merge all PDFs in directory
pdftk *.pdf cat output all_merged.pdf

# Merge with specific order
pdftk chapter1.pdf chapter2.pdf chapter3.pdf cat output book.pdf

# Merge using qpdf
qpdf --empty --pages file1.pdf file2.pdf -- merged.pdf

# Merge with page selection
pdftk A=file1.pdf B=file2.pdf cat A1-3 B2-5 output merged.pdf

# Merge odd pages only
pdftk input.pdf cat odd output odd_pages.pdf

# Merge even pages only
pdftk input.pdf cat even output even_pages.pdf

# Python merge
python << 'EOF'
import PyPDF2
merger = PyPDF2.PdfMerger()
for pdf in ['file1.pdf', 'file2.pdf']:
    merger.append(pdf)
merger.write('merged.pdf')
merger.close()
EOF
```

### PDF Split Commands

```bash
# Split into individual pages
pdftk input.pdf burst output page_%d.pdf

# Extract specific pages
pdftk input.pdf cat 5-10 output extracted.pdf

# Extract multiple ranges
pdftk input.pdf cat 1-5 10-15 20-end output selected.pdf

# Extract single page
pdftk input.pdf cat 5 output page5.pdf

# Extract first page
pdftk input.pdf cat 1 output first_page.pdf

# Extract last page (need to know total pages)
pdftk input.pdf cat end output last_page.pdf

# Split using qpdf
qpdf --split-pages input.pdf page_%d.pdf

# Split every 5 pages
python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('large.pdf')
total = len(reader.pages)
for i in range(0, total, 5):
    writer = PyPDF2.PdfWriter()
    for j in range(i, min(i+5, total)):
        writer.add_page(reader.pages[j])
    with open(f'part_{i//5+1}.pdf', 'wb') as f:
        writer.write(f)
EOF
```

### PDF to Text Commands

```bash
# Basic text extraction
pdftotext input.pdf output.txt

# View in terminal
pdftotext input.pdf -

# Preserve layout
pdftotext -layout input.pdf output.txt

# Extract specific pages
pdftotext -f 1 -l 5 input.pdf output.txt

# Extract with encoding
pdftotext -enc UTF-8 input.pdf output.txt

# Extract from encrypted PDF
pdftotext -upw password input.pdf output.txt

# Python text extraction
python << 'EOF'
import PyPDF2
with open('input.pdf', 'rb') as f:
    reader = PyPDF2.PdfReader(f)
    text = ''
    for page in reader.pages:
        text += page.extract_text()
    print(text)
EOF
```

### PDF to Image Commands

```bash
# Convert to PNG
pdftoppm input.pdf output -png

# Convert to JPEG
pdftoppm input.pdf output -jpeg

# Convert specific page
pdftoppm -f 1 -l 1 input.pdf output -png

# High resolution (300 DPI)
pdftoppm -r 300 input.pdf output -png

# Low resolution (72 DPI)
pdftoppm -r 72 input.pdf output -png

# Single page extraction
pdftoppm -f 5 -l 5 input.pdf page5 -png

# Using ImageMagick
convert input.pdf output.png

# Convert all pages to separate images
convert input.pdf page_%d.png
```

### Image to PDF Commands

```bash
# Single image to PDF
convert image.jpg output.pdf

# Multiple images to PDF
convert image1.jpg image2.jpg output.pdf

# All images in folder
convert *.jpg combined.pdf

# With quality setting
convert -quality 90 image.jpg output.pdf

# Resize before converting
convert -resize 800x600 image.jpg output.pdf

# Multiple pages from images
convert page1.png page2.png page3.png document.pdf

# With page size
convert -page A4 image.jpg output.pdf

# Using img2pdf (better quality)
pip install img2pdf
img2pdf image.jpg -o output.pdf
```

### PDF Compression Commands

```bash
# Using pdftk
pdftk input.pdf output compressed.pdf compress

# Using qpdf
qpdf --compress-streams=yes input.pdf output.pdf

# Ghostscript - Screen quality (smallest)
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen \
   -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

# Ghostscript - Ebook quality
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook \
   -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

# Ghostscript - Printer quality
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer \
   -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

# Ghostscript - Default quality
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/default \
   -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

# Python compression
python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('input.pdf')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    writer.add_page(page)
writer.add_metadata(reader.metadata)
with open('compressed.pdf', 'wb') as f:
    writer.write(f)
EOF
```

### PDF Password Commands

```bash
# Add password with pdftk
pdftk input.pdf output protected.pdf user_pw MyPassword

# Add with owner password
pdftk input.pdf output protected.pdf user_pw UserPass owner_pw OwnerPass

# Add with permissions
pdftk input.pdf output protected.pdf user_pw MyPassword allow printing

# Allow specific features
pdftk input.pdf output protected.pdf user_pw MyPassword \
    allow printing copy modifyannotations

# Allow all features with password
pdftk input.pdf output protected.pdf user_pw MyPassword allow AllFeatures

# Add password with qpdf (256-bit)
qpdf --encrypt userpass ownerpass 256 -- input.pdf output.pdf

# Add password with qpdf (128-bit)
qpdf --encrypt userpass ownerpass 128 -- input.pdf output.pdf

# Remove password with pdftk
pdftk protected.pdf input_pw MyPassword output unprotected.pdf

# Remove password with qpdf
qpdf --password=MyPassword --decrypt protected.pdf output.pdf

# Remove password with Ghostscript
gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite \
   -sOutputFile=output.pdf protected.pdf
```

### PDF Rotation Commands

```bash
# Rotate all pages right (90° clockwise)
pdftk input.pdf cat 1-endright output rotated.pdf

# Rotate all pages left (90° counter-clockwise)
pdftk input.pdf cat 1-endleft output rotated.pdf

# Rotate all pages 180°
pdftk input.pdf cat 1-enddown output rotated.pdf

# Rotate specific page
pdftk input.pdf cat 1 2right 3-end output rotated.pdf

# Rotate multiple specific pages
pdftk input.pdf cat 1right 2right 3-end output rotated.pdf

# Rotate using qpdf
qpdf input.pdf output.pdf --rotate=+90:1,2,3

# Rotate all pages with qpdf
qpdf input.pdf output.pdf --rotate=+90

# Rotate 180 degrees
qpdf input.pdf output.pdf --rotate=+180
```

### PDF Info Commands

```bash
# Get PDF info
pdfinfo input.pdf

# Get number of pages
pdfinfo input.pdf | grep Pages

# Get metadata
pdftk input.pdf dump_data

# Get specific metadata
pdftk input.pdf dump_data | grep InfoKey

# Python info extraction
python << 'EOF'
import PyPDF2
with open('input.pdf', 'rb') as f:
    reader = PyPDF2.PdfReader(f)
    print(f"Pages: {len(reader.pages)}")
    print(f"Metadata: {reader.metadata}")
EOF

# Check if encrypted
python << 'EOF'
import PyPDF2
with open('input.pdf', 'rb') as f:
    reader = PyPDF2.PdfReader(f)
    print(f"Encrypted: {reader.is_encrypted}")
EOF
```

### PDF Page Extraction Commands

```bash
# Extract pages 1-5
pdftk input.pdf cat 1-5 output pages1-5.pdf

# Extract last 5 pages
pdftk input.pdf cat r1-r5 output last5.pdf

# Extract from page 10 to end
pdftk input.pdf cat 10-end output from10.pdf

# Extract odd pages
pdftk input.pdf cat odd output odd.pdf

# Extract even pages
pdftk input.pdf cat even output even.pdf

# Extract specific pages
pdftk input.pdf cat 1 3 5 7 9 output odd_specific.pdf

# Reverse page order
pdftk input.pdf cat end-1 output reversed.pdf

# Duplicate pages
pdftk input.pdf cat 1 1 1 output triple_first.pdf
```

### PDF Watermark Commands

```bash
# Add watermark using pdftk
pdftk input.pdf background watermark.pdf output watermarked.pdf

# Add stamp (foreground)
pdftk input.pdf stamp stamp.pdf output stamped.pdf

# Multi-page watermark
pdftk A=input.pdf B=watermark.pdf shuffle A B output watermarked.pdf

# Python watermark
python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('input.pdf')
watermark = PyPDF2.PdfReader('watermark.pdf')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    page.merge_page(watermark.pages[0])
    writer.add_page(page)
with open('watermarked.pdf', 'wb') as f:
    writer.write(f)
EOF
```

### PDF Metadata Commands

```bash
# Dump metadata
pdftk input.pdf dump_data output metadata.txt

# Update metadata
pdftk input.pdf update_info metadata.txt output updated.pdf

# Set title
pdftk input.pdf update_info_utf8 <(echo "InfoKey: Title
InfoValue: My Document Title") output updated.pdf

# Python metadata
python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('input.pdf')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    writer.add_page(page)
writer.add_metadata({
    '/Title': 'My Document',
    '/Author': 'T3rmuxk1ng',
    '/Subject': 'Termux Course'
})
with open('with_metadata.pdf', 'wb') as f:
    writer.write(f)
EOF
```

---

## 💻 PRACTICE EXERCISES

### Exercise 1: Basic PDF Merge

```bash
# Task: Create three simple PDFs and merge them

# Step 1: Create test PDFs using Python
python << 'EOF'
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas

for i in range(1, 4):
    c = canvas.Canvas(f"document{i}.pdf", pagesize=letter)
    c.drawString(100, 750, f"This is Document {i}")
    c.drawString(100, 720, "Created in Termux")
    c.save()
EOF

# Step 2: Merge all three PDFs
pdftk document1.pdf document2.pdf document3.pdf cat output merged.pdf

# Step 3: Verify
pdfinfo merged.pdf
# Should show Pages: 3

# Step 4: Clean up test files
rm document1.pdf document2.pdf document3.pdf
```

### Exercise 2: PDF Split and Reorganize

```bash
# Task: Create a 10-page PDF and extract specific pages

# Step 1: Create 10-page PDF
python << 'EOF'
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas

c = canvas.Canvas("book.pdf", pagesize=letter)
for i in range(1, 11):
    c.drawString(100, 750, f"Page {i} of 10")
    c.drawString(100, 720, "Termux PDF Tools Chapter")
    c.showPage()
c.save()
EOF

# Step 2: Split into individual pages
mkdir pages
pdftk book.pdf burst output pages/page_%d.pdf

# Step 3: Verify split
ls pages/

# Step 4: Reorganize - take pages 3,5,7 and create new PDF
pdftk pages/page_3.pdf pages/page_5.pdf pages/page_7.pdf \
    cat output selected.pdf

# Step 5: Verify
pdfinfo selected.pdf
# Should show Pages: 3

# Step 6: Clean up
rm -rf pages book.pdf selected.pdf
```

### Exercise 3: PDF to Text Extraction

```bash
# Task: Extract text from a PDF and analyze it

# Step 1: Create PDF with text
python << 'EOF'
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas

c = canvas.Canvas("article.pdf", pagesize=letter)
text_lines = [
    "Termux is a powerful terminal emulator for Android.",
    "It provides a Linux environment without root access.",
    "You can install Python, Node.js, and many other tools.",
    "PDF tools in Termux include pdftk, qpdf, and poppler.",
    "This is Chapter 42 of the Termux Full Course."
]

y = 750
for line in text_lines:
    c.drawString(50, y, line)
    y -= 30
c.save()
EOF

# Step 2: Extract text to file
pdftotext article.pdf extracted.txt

# Step 3: View extracted text
cat extracted.txt

# Step 4: Search in extracted text
grep -i "termux" extracted.txt

# Step 5: Count words
wc -w extracted.txt

# Step 6: Clean up
rm article.pdf extracted.txt
```

### Exercise 4: PDF Compression

```bash
# Task: Create a large PDF and compress it

# Step 1: Create PDF with images (simulated)
convert -size 1000x1000 xc:white white.png
convert -size 1000x1000 xc:black black.png

# Step 2: Create multi-page PDF
convert white.png black.png white.png black.png white.png large.pdf

# Step 3: Check original size
ls -lh large.pdf

# Step 4: Compress with pdftk
pdftk large.pdf output compressed_pdftk.pdf compress

# Step 5: Compress with Ghostscript
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
   -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH \
   -sOutputFile=compressed_gs.pdf large.pdf

# Step 6: Compare sizes
ls -lh large.pdf compressed_pdftk.pdf compressed_gs.pdf

# Step 7: Clean up
rm large.pdf compressed_pdftk.pdf compressed_gs.pdf white.png black.png
```

### Exercise 5: PDF Password Protection

```bash
# Task: Protect a PDF with password and verify

# Step 1: Create test PDF
python << 'EOF'
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas
c = canvas.Canvas("secret.pdf", pagesize=letter)
c.drawString(100, 750, "This is a secret document")
c.drawString(100, 720, "Password protected!")
c.save()
EOF

# Step 2: Add password
pdftk secret.pdf output protected.pdf user_pw mysecret123

# Step 3: Verify protection - this should fail without password
pdftotext protected.pdf test.txt
# Should show error

# Step 4: Remove password
pdftk protected.pdf input_pw mysecret123 output unprotected.pdf

# Step 5: Verify unprotected file
pdftotext unprotected.pdf test.txt
cat test.txt

# Step 6: Clean up
rm secret.pdf protected.pdf unprotected.pdf test.txt
```

### Exercise 6: PDF Rotation

```bash
# Task: Create PDF and rotate specific pages

# Step 1: Create multi-page PDF
python << 'EOF'
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas
c = canvas.Canvas("landscape.pdf", pagesize=letter)
for i in range(1, 6):
    c.drawString(100, 750, f"Page {i}")
    c.showPage()
c.save()
EOF

# Step 2: Rotate all pages 90 degrees
pdftk landscape.pdf cat 1-endright output rotated_all.pdf

# Step 3: Rotate only page 3
pdftk landscape.pdf cat 1-2 3right 4-end output rotated_one.pdf

# Step 4: Verify with pdfinfo
pdfinfo rotated_all.pdf
pdfinfo rotated_one.pdf

# Step 5: Clean up
rm landscape.pdf rotated_all.pdf rotated_one.pdf
```

### Exercise 7: Python PDF Script

```bash
# Task: Create a comprehensive PDF manipulation script

# Step 1: Create the script
cat > pdf_tools.py << 'EOF'
#!/usr/bin/env python3
import PyPDF2
import sys

def get_info(filename):
    with open(filename, 'rb') as f:
        reader = PyPDF2.PdfReader(f)
        print(f"Pages: {len(reader.pages)}")
        print(f"Encrypted: {reader.is_encrypted}")
        if reader.metadata:
            print("Metadata:")
            for key, value in reader.metadata.items():
                print(f"  {key}: {value}")

def extract_text(filename, output):
    with open(filename, 'rb') as f:
        reader = PyPDF2.PdfReader(f)
        with open(output, 'w') as out:
            for page in reader.pages:
                out.write(page.extract_text() + "\n")
    print(f"Text saved to {output}")

def merge_pdfs(files, output):
    merger = PyPDF2.PdfMerger()
    for f in files:
        merger.append(f)
    merger.write(output)
    merger.close()
    print(f"Merged {len(files)} files to {output}")

def split_pdf(filename, output_prefix):
    with open(filename, 'rb') as f:
        reader = PyPDF2.PdfReader(f)
        for i, page in enumerate(reader.pages):
            writer = PyPDF2.PdfWriter()
            writer.add_page(page)
            with open(f"{output_prefix}_{i+1}.pdf", 'wb') as out:
                writer.write(out)
    print(f"Split into {len(reader.pages)} files")

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print("Usage: python pdf_tools.py <command> [args]")
        print("Commands: info, extract, merge, split")
        sys.exit(1)
    
    cmd = sys.argv[1]
    
    if cmd == "info" and len(sys.argv) >= 3:
        get_info(sys.argv[2])
    elif cmd == "extract" and len(sys.argv) >= 4:
        extract_text(sys.argv[2], sys.argv[3])
    elif cmd == "merge" and len(sys.argv) >= 4:
        merge_pdfs(sys.argv[2:-1], sys.argv[-1])
    elif cmd == "split" and len(sys.argv) >= 4:
        split_pdf(sys.argv[2], sys.argv[3])
    else:
        print("Invalid command or arguments")
EOF

# Step 2: Test the script
python pdf_tools.py info test.pdf

# Step 3: Clean up
rm pdf_tools.py
```

---

## ⚠️ TROUBLESHOOTING

### Problem 1: "pdftk: command not found"

```bash
# Cause: pdftk not installed

# Solution: Install pdftk
pkg install pdftk -y

# Verify installation
which pdftk
pdftk --version
```

### Problem 2: "Unable to merge PDFs"

```bash
# Cause: Corrupted PDF or wrong syntax

# Solution 1: Check if PDF is valid
pdfinfo input.pdf

# Solution 2: Try with qpdf
qpdf --check input.pdf

# Solution 3: Repair PDF
pdftk damaged.pdf output repaired.pdf

# Solution 4: Use correct syntax
pdftk file1.pdf file2.pdf cat output merged.pdf
# Note: 'cat' keyword is required
```

### Problem 3: "PDF is password protected"

```bash
# Cause: PDF has encryption

# Solution 1: Check if encrypted
pdfinfo input.pdf | grep "Encrypted"

# Solution 2: Remove password if you know it
pdftk input.pdf input_pw YOUR_PASSWORD output decrypted.pdf

# Solution 3: Using qpdf
qpdf --password=YOUR_PASSWORD --decrypt input.pdf output.pdf
```

### Problem 4: "ImageMagick not converting to PDF"

```bash
# Cause: Policy restrictions or missing dependencies

# Solution 1: Check ImageMagick policy
convert -list policy

# Solution 2: Use pdftoppm instead for PDF to image
pdftoppm input.pdf output -png

# Solution 3: For image to PDF, ensure proper syntax
convert image.jpg output.pdf

# Solution 4: Install additional ImageMagick delegates
pkg install imagemagick -y
```

### Problem 5: "Ghostscript compression fails"

```bash
# Cause: Complex PDF or insufficient memory

# Solution 1: Use simpler compression
pdftk input.pdf output compressed.pdf compress

# Solution 2: Use qpdf
qpdf --compress-streams=yes input.pdf output.pdf

# Solution 3: Increase memory limit
ulimit -v unlimited

# Solution 4: Use lower quality settings
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen \
   -dNOPAUSE -dQUIET -dBATCH \
   -sOutputFile=output.pdf input.pdf
```

### Problem 6: "pdftotext produces empty output"

```bash
# Cause: Scanned PDF (images, no text layer)

# Solution 1: Check if PDF has text
pdfinfo input.pdf | grep "Page size"

# Solution 2: Extract images instead
pdfimages -list input.pdf
pdfimages input.pdf image_prefix

# Solution 3: Use OCR (requires additional packages)
pkg install tesseract
pdftoppm input.pdf page -png
tesseract page-1.png output

# Solution 4: Check encoding
pdftotext -layout -enc UTF-8 input.pdf output.txt
```

### Problem 7: "qpdf encryption fails"

```bash
# Cause: Invalid parameters or unsupported encryption

# Solution 1: Use correct syntax
qpdf --encrypt userpass ownerpass 256 -- input.pdf output.pdf

# Solution 2: Use 128-bit instead
qpdf --encrypt userpass ownerpass 128 -- input.pdf output.pdf

# Solution 3: Check qpdf version
qpdf --version

# Solution 4: Use pdftk for encryption
pdftk input.pdf output output.pdf user_pw password
```

### Problem 8: "Python PyPDF2 import error"

```bash
# Cause: PyPDF2 not installed or Python version issue

# Solution 1: Install PyPDF2
pip install PyPDF2

# Solution 2: Upgrade pip
pip install --upgrade pip

# Solution 3: Try newer pypdf library
pip install pypdf

# Solution 4: Check Python
python --version
python -c "import PyPDF2; print(PyPDF2.__version__)"
```

### Problem 9: "Permission denied when saving PDF"

```bash
# Cause: Storage permission or directory issue

# Solution 1: Check current directory
pwd

# Solution 2: Use home directory
pdftk input.pdf cat 1 output ~/output.pdf

# Solution 3: Grant storage permission
termux-setup-storage

# Solution 4: Check file permissions
ls -la output.pdf
chmod 644 output.pdf
```

### Problem 10: "Large PDF processing hangs"

```bash
# Cause: Memory limitation

# Solution 1: Process in chunks
pdftk input.pdf cat 1-50 output part1.pdf
pdftk input.pdf cat 51-100 output part2.pdf

# Solution 2: Use qpdf for large files
qpdf input.pdf output.pdf

# Solution 3: Compress first
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \
   -sOutputFile=smaller.pdf input.pdf

# Solution 4: Process pages individually
python << 'EOF'
import PyPDF2
reader = PyPDF2.PdfReader('large.pdf')
for i in range(min(10, len(reader.pages))):
    print(f"Processing page {i+1}")
    # Process each page
EOF
```

---

## 🎬 VIDEO ASSETS

### Thumbnail Concepts

**Option A: Tool Showcase**
```
┌────────────────────────────────────┐
│  [PDF Document Icon]               │
│                                    │
│   📄 PDF TOOLS IN TERMUX           │
│   ────────────────────────         │
│   ✓ Merge ✓ Split ✓ Protect        │
│   ✓ Compress ✓ Convert             │
│                                    │
│   NO PC REQUIRED!                  │
│   [T3rmuxk1ng Logo]                │
└────────────────────────────────────┘
```

**Option B: Before/After Style**
```
┌────────────────────────────────────┐
│  BEFORE          AFTER             │
│  ──────          ─────             │
│  10 PDF files    1 Merged PDF      │
│  50 MB Size      5 MB Compressed   │
│  Unprotected     Password Set      │
│                                    │
│  ALL IN TERMUX! 🚀                 │
│  [T3rmuxk1ng]                      │
└────────────────────────────────────┘
```

**Option C: Command Style**
```
┌────────────────────────────────────┐
│  📱 TERMUX PDF COMMANDS            │
│                                    │
│  $ pdftk merge                     │
│  $ qpdf encrypt                    │
│  $ pdftotext extract               │
│  $ convert compress                │
│                                    │
│  Chapter 42 | T3rmuxk1ng           │
└────────────────────────────────────┘
```

### Video Description Template

```markdown
📄 Termux Full Course - Chapter 42: PDF Tools in Termux | Complete PDF Manipulation Guide

🔥 In this video you'll learn:
• PDF tools installation in Termux
• PDF merge - Multiple files combine karna
• PDF split - Pages extract karna
• PDF to text conversion
• PDF to images & images to PDF
• PDF compression - Size reduce karna
• Password protection & removal
• PDF rotation
• Python PyPDF2 scripting

⏱️ Timestamps:
0:00 - Introduction
0:45 - PDF Tools Overview
3:00 - Installation Guide
5:00 - PDF Merge Operations
7:00 - PDF Split Operations
9:00 - PDF to Text Extraction
10:30 - PDF to Images & Images to PDF
12:30 - PDF Compression
14:00 - Password Protection
16:00 - Password Removal
17:30 - PDF Rotation
18:30 - Python PyPDF2 Scripting
19:30 - Summary

📝 Commands from this video:
pkg install pdftk qpdf poppler imagemagick ghostscript
pdftk file1.pdf file2.pdf cat output merged.pdf
pdftotext input.pdf output.txt
pdftk input.pdf output protected.pdf user_pw password

📥 Install Commands:
pip install PyPDF2
pip install pypdf
pip install reportlab

📚 Full Course Playlist:
[PLAYLIST LINK]

📱 Follow T3rmuxk1ng:
• YouTube: @T3rmuxk1ng
• Telegram: [LINK]
• GitHub: [LINK]

#Termux #PDFTools #TermuxCourse #T3rmuxk1ng #PDFMerge #PDFSplit #PDFEditor #LinuxOnAndroid #TermuxHindi

---
⚠️ Disclaimer: This video is for educational purposes. Use tools responsibly and only on documents you have permission to modify.
```

### Tags List

```
termux, termux pdf tools, pdftk termux, qpdf termux, 
pdf merge termux, pdf split termux, pdf compress termux,
pdf password protection, pdf to text, pdf to image,
imagemagick termux, poppler termux, pypdf2 python,
pdf manipulation termux, termux tutorial hindi,
t3rmuxk1ng, termux course, android pdf editor,
linux pdf tools, termux utilities, pdf toolkit,
pdf security, pdf encryption, pdf decryption,
mobile pdf tools, android pdf merge
```

### Hashtags

```
#Termux #PDFTools #PDFMerge #PDFSplit #PDFFormat 
#TermuxCourse #T3rmuxk1ng #AndroidTools #LinuxOnAndroid 
#TermuxHindi #PDFEditor #PDFSecurity #PyPDF2 #MobileHacking
```

---

## 📚 ADDITIONAL RESOURCES

### Official Documentation

| Resource | Link |
|----------|------|
| pdftk Manual | https://www.pdflabs.com/docs/pdftk-man-page/ |
| qpdf Manual | https://qpdf.sourceforge.net/ |
| Poppler Utils | https://poppler.freedesktop.org/ |
| ImageMagick | https://imagemagick.org/ |
| PyPDF2 Docs | https://pypdf2.readthedocs.io/ |

### Python PDF Libraries

| Library | Install | Purpose |
|---------|---------|---------|
| PyPDF2 | pip install PyPDF2 | PDF manipulation |
| pypdf | pip install pypdf | Newer fork of PyPDF2 |
| reportlab | pip install reportlab | PDF creation |
| img2pdf | pip install img2pdf | Image to PDF |
| pdf2docx | pip install pdf2docx | PDF to Word |

### Related Termux Packages

```bash
# Additional useful packages
pkg install ghostscript    # PDF processing
pkg install djvulibre      # DjVu format support
pkg install libspectre     # PostScript support
pkg install tesseract      # OCR for scanned PDFs
```

---

## ✅ CHAPTER CHECKLIST

Before moving to Chapter 43, verify:

- [ ] pdftk installed and working
- [ ] qpdf installed and working
- [ ] poppler-utils installed (pdftotext, pdftoppm)
- [ ] ImageMagick installed for image conversion
- [ ] PyPDF2 installed in Python
- [ ] Successfully merged multiple PDFs
- [ ] Successfully split a PDF into pages
- [ ] Extracted text from a PDF
- [ ] Converted PDF to images
- [ ] Compressed a PDF file
- [ ] Added password to a PDF
- [ ] Removed password from a PDF
- [ ] Rotated PDF pages

---

## 🎯 NEXT CHAPTER PREVIEW

**Chapter 43: Task Automation in Termux**

- Cron jobs setup and scheduling
- Automated backup scripts
- Scheduled tasks execution
- Background process management
- Log rotation automation
- System monitoring scripts
- Email notifications
- Task automation best practices

---

**Chapter Complete! 🎉**

*Created by T3rmuxk1ng | Termux Full Course*

---

## 🎮 INTERACTIVE QUIZ - Test Your Knowledge!

<details>
<summary>❓ Q1: PDF को merge करने के लिए कौन सा tool use होता है?</summary>

**Answer:**
```bash
# Using pdftk
pdftk file1.pdf file2.pdf cat output merged.pdf

# Using qpdf
qpdf --empty --pages file1.pdf file2.pdf -- merged.pdf
```
दोनों tools से PDF merge होती है, pdftk ज़्यादा popular है।
</details>

<details>
<summary>❓ Q2: PDF से text extract कैसे करें?</summary>

**Answer:**
```bash
# Basic extraction
pdftotext input.pdf output.txt

# Preserve layout
pdftotext -layout input.pdf output.txt

# Specific pages
pdftotext -f 1 -l 5 input.pdf output.txt
```
</details>

<details>
<summary>❓ Q3: PDF को password protect कैसे करें?</summary>

**Answer:**
```bash
# Using pdftk
pdftk input.pdf output protected.pdf user_pw MyPassword

# Using qpdf (256-bit encryption)
qpdf --encrypt userpass ownerpass 256 -- input.pdf output.pdf
```
</details>

<details>
<summary>❓ Q4: PDF को images में convert कैसे करें?</summary>

**Answer:**
```bash
# PNG format
pdftoppm input.pdf output -png

# JPEG format
pdftoppm input.pdf output -jpeg

# High resolution (300 DPI)
pdftoppm -r 300 input.pdf output -png
```
</details>

<details>
<summary>❓ Q5: PDF से password कैसे remove करें?</summary>

**Answer:**
```bash
# Using pdftk (need to know password)
pdftk protected.pdf input_pw MyPassword output unprotected.pdf

# Using qpdf
qpdf --password=MyPassword --decrypt protected.pdf output.pdf
```
</details>

<details>
<summary>❓ Q6: PDF को compress करने के तरीके?</summary>

**Answer:**
```bash
# Using pdftk
pdftk input.pdf output compressed.pdf compress

# Using Ghostscript (better compression)
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook -o output.pdf input.pdf

# Settings: /screen (smallest), /ebook, /printer (best quality)
```
</details>

<details>
<summary>❓ Q7: PDF से specific pages कैसे extract करें?</summary>

**Answer:**
```bash
# Pages 5-10
pdftk input.pdf cat 5-10 output extracted.pdf

# Multiple ranges
pdftk input.pdf cat 1-5 10-15 output selected.pdf

# Single page
pdftk input.pdf cat 5 output page5.pdf

# Split into individual pages
pdftk input.pdf burst output page_%d.pdf
```
</details>

<details>
<summary>❓ Q8: Images को PDF में convert कैसे करें?</summary>

**Answer:**
```bash
# Using ImageMagick
convert image1.jpg image2.jpg output.pdf

# All images in folder
convert *.jpg combined.pdf

# With quality setting
convert -quality 90 image.jpg output.pdf
```
</details>

<details>
<summary>❓ Q9: PDF pages को rotate कैसे करें?</summary>

**Answer:**
```bash
# Rotate all pages 90° clockwise
pdftk input.pdf cat 1-endright output rotated.pdf

# Rotate specific page
pdftk input.pdf cat 1 2right 3-end output rotated.pdf

# Using qpdf
qpdf input.pdf output.pdf --rotate=+90:1,2,3
```
</details>

<details>
<summary>❓ Q10: PyPDF2 से PDF merge कैसे करें?</summary>

**Answer:**
```python
import PyPDF2
merger = PyPDF2.PdfMerger()
merger.append('file1.pdf')
merger.append('file2.pdf')
merger.write('merged.pdf')
merger.close()
```
</details>

<details>
<summary>❓ Q11: PDF में watermark कैसे add करें?</summary>

**Answer:**
```python
import PyPDF2
reader = PyPDF2.PdfReader('input.pdf')
watermark = PyPDF2.PdfReader('watermark.pdf')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    page.merge_page(watermark.pages[0])
    writer.add_page(page)
with open('watermarked.pdf', 'wb') as f:
    writer.write(f)
```
</details>

<details>
<summary>❓ Q12: PDF info कैसे देखें?</summary>

**Answer:**
```bash
# Using pdfinfo
pdfinfo input.pdf

# Using pdftk
pdftk input.pdf dump_data

# Number of pages
pdfinfo input.pdf | grep Pages
```
</details>

<details>
<summary>❓ Q13: PDF को split करके chapters कैसे बनाएं?</summary>

**Answer:**
```bash
# Manual splitting
pdftk book.pdf cat 1-20 output chapter1.pdf
pdftk book.pdf cat 21-40 output chapter2.pdf

# Python script for automated splitting
for i in range(0, total_pages, 10):
    pdftk input.pdf cat $((i+1))-$((i+10)) output "part_$((i/10+1)).pdf"
```
</details>

<details>
<summary>❓ Q14: Encrypted PDF से text extract कैसे करें?</summary>

**Answer:**
```bash
# Using pdftotext with password
pdftotext -upw MyPassword protected.pdf output.txt

# First decrypt, then extract
qpdf --password=pass --decrypt protected.pdf temp.pdf
pdftotext temp.pdf output.txt
rm temp.pdf
```
</details>

<details>
<summary>❓ Q15: PDF metadata कैसे edit करें?</summary>

**Answer:**
```bash
# Using pdftk
pdftk input.pdf update_info info.txt output new.pdf

# info.txt format:
# InfoKey: Title
# InfoValue: My Document Title
# InfoKey: Author
# InfoValue: T3rmuxk1ng

# Using Python PyPDF2
writer.add_metadata({'/Title': 'My Title', '/Author': 'Author'})
```
</details>

---

## 🎯 INTERVIEW QUESTIONS - Job Preparation

### Q1: PDF file structure explain करें?

**Answer:**
PDF files consist of four main parts:
1. **Header**: PDF version (e.g., %PDF-1.7)
2. **Body**: Objects (pages, fonts, images)
3. **Cross-reference table**: Object locations
4. **Trailer**: File metadata and xref location

```
%PDF-1.7
[Body - Objects]
xref
[Cross-reference table]
trailer
[Trailer dictionary]
%%EOF
```

### Q2: PDF encryption levels explain करें?

**Answer:**
| Level | Algorithm | Security |
|-------|-----------|----------|
| 40-bit RC4 | Legacy | Weak |
| 128-bit RC4 | Standard | Moderate |
| 128-bit AES | Modern | Strong |
| 256-bit AES | Current | Very Strong |

**User Password**: Opens the document
**Owner Password**: Controls permissions (print, copy, modify)

### Q3: pdftk और qpdf में difference?

**Answer:**
| Feature | pdftk | qpdf |
|---------|-------|------|
| Merge | ✅ | ✅ |
| Split | ✅ | ✅ |
| Encrypt | ✅ 128-bit | ✅ 256-bit |
| Linearize | ❌ | ✅ |
| Inspect | ❌ | ✅ |
| Speed | Slower | Faster |
| Memory | Higher | Lower |

Use pdftk for general operations, qpdf for optimization and encryption.

### Q4: PDF linearization क्या है?

**Answer:**
Linearized PDF (Fast Web View) allows:
- First page displays while file downloads
- Progressive loading in browsers
- Better web experience

```bash
# Linearize with qpdf
qpdf --linearize input.pdf output.pdf

# Check if linearized
qpdf --show-linearization input.pdf
```

### Q5: PDF compression techniques?

**Answer:**
1. **Image downsampling**: Reduce image resolution
2. **Font subsetting**: Include only used characters
3. **Object compression**: Compress internal structures
4. **Removing metadata**: Strip unnecessary info

```bash
# Ghostscript compression levels
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -o output.pdf input.pdf  # 72 DPI
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook -o output.pdf input.pdf   # 150 DPI
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/printer -o output.pdf input.pdf # 300 DPI
```

### Q6: PDF/A format क्या है?

**Answer:**
PDF/A is an ISO-standardized version for long-term archiving:
- Self-contained (all fonts embedded)
- No JavaScript or encryption
- Specific color spaces
- Metadata requirements

```bash
# Convert to PDF/A
gs -dPDFA -sDEVICE=pdfwrite -o output.pdf input.pdf
```

### Q7: OCR के बिना scanned PDF से text extract करने की limitations?

**Answer:**
- Scanned PDFs are images, not text
- pdftotext returns empty or garbage
- Need OCR (Optical Character Recognition)

```bash
# Install tesseract for OCR
pkg install tesseract

# OCR a scanned PDF
pdftoppm page.pdf page -png
tesseract page-1.png output
```

### Q8: PDF forms handling?

**Answer:**
```bash
# Fill form fields
pdftk form.pdf fill_form data.fdf output filled.pdf

# Extract form data
pdftk form.pdf generate_fdf output data.fdf

# Flatten form (make non-editable)
pdftk filled.pdf output flattened.pdf flatten
```

### Q9: PDF page extraction performance optimization?

**Answer:**
```bash
# For large PDFs, use page ranges
pdftk large.pdf cat 1-100 output part1.pdf

# Use qpdf for faster splitting
qpdf --split-pages large.pdf page_%d.pdf

# Python for memory-efficient processing
for i, page in enumerate(reader.pages):
    # Process one page at a time
```

### Q10: PDF security best practices?

**Answer:**
1. Use AES-256 encryption
2. Set both user and owner passwords
3. Restrict permissions appropriately
4. Remove sensitive metadata
5. Don't rely solely on PDF encryption for highly sensitive data

```bash
# Best practice encryption
qpdf --encrypt user owner 256 \
    --allow=none \
    -- input.pdf output.pdf
```

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Document Organization System

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  📂 SCENARIO: Automated Document Organization                                ║
║                                                                               ║
║  Problem: Organize large PDF into chapter-wise files with proper naming     ║
║  and table of contents generation.                                           ║
║                                                                               ║
║  ┌─────────────────────────────────────────────────────────────────────────┐ ║
║  │                                                                         │ ║
║  │  #!/bin/bash                                                            │ ║
║  │  INPUT="book.pdf"                                                       │ ║
║  │  OUTPUT_DIR="chapters"                                                  │ ║
║  │  PAGES_PER_CHAPTER=20                                                   │ ║
║  │                                                                         │ ║
║  │  mkdir -p "$OUTPUT_DIR"                                                 │ ║
║  │                                                                         │ ║
║  │  # Get total pages                                                      │ ║
║  │  TOTAL=$(pdfinfo "$INPUT" | grep Pages | awk '{print $2}')              │ ║
║  │                                                                         │ ║
║  │  # Split into chapters                                                  │ ║
║  │  CHAPTER=1                                                              │ ║
║  │  for ((i=1; i<=TOTAL; i+=PAGES_PER_CHAPTER)); do                        │ ║
║  │      END=$((i + PAGES_PER_CHAPTER - 1))                                 │ ║
║  │      [ $END -gt $TOTAL ] && END=$TOTAL                                  │ ║
║  │      pdftk "$INPUT" cat $i-$END output "$OUTPUT_DIR/chapter_$CHAPTER.pdf" │ ║
║  │      echo "Created chapter_$CHAPTER.pdf (pages $i-$END)"                │ ║
║  │      ((CHAPTER++))                                                      │ ║
║  │  done                                                                   │ ║
║  │                                                                         │ ║
║  └─────────────────────────────────────────────────────────────────────────┘ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 2: Secure Document Distribution

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  🔒 SCENARIO: Secure Document Distribution System                            ║
║                                                                               ║
║  Problem: Distribute PDFs with unique passwords for each recipient.          ║
║                                                                               ║
║  ┌─────────────────────────────────────────────────────────────────────────┐ ║
║  │                                                                         │ ║
║  │  #!/bin/bash                                                            │ ║
║  │  INPUT="document.pdf"                                                   │ ║
║  │  RECIPIENTS=("alice" "bob" "charlie")                                   │ ║
║  │  OUTPUT_DIR="secured"                                                   │ ║
║  │                                                                         │ ║
║  │  mkdir -p "$OUTPUT_DIR"                                                 │ ║
║  │                                                                         │ ║
║  │  for recipient in "${RECIPIENTS[@]}"; do                                │ ║
║  │      # Generate unique password                                         │ ║
║  │      PASSWORD=$(openssl rand -base64 12)                                │ ║
║  │                                                                         │ ║
║  │      # Create encrypted PDF                                             │ ║
║  │      qpdf --encrypt "$PASSWORD" "owner123" 256 \                         │ ║
║  │          -- "$INPUT" "$OUTPUT_DIR/${recipient}.pdf"                      │ ║
║  │                                                                         │ ║
║  │      # Save password (in production, send securely)                      │ ║
║  │      echo "$recipient: $PASSWORD" >> passwords.txt                       │ ║
║  │      echo "Created secured PDF for $recipient"                          │ ║
║  │  done                                                                   │ ║
║  │                                                                         │ ║
║  └─────────────────────────────────────────────────────────────────────────┘ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 3: Report Generation Pipeline

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  📊 SCENARIO: Monthly Report Generation Pipeline                             ║
║                                                                               ║
║  Problem: Generate combined PDF report from multiple sources                  ║
║  (images, text, existing PDFs) with cover page.                              ║
║                                                                               ║
║  ┌─────────────────────────────────────────────────────────────────────────┐ ║
║  │                                                                         │ ║
║  │  #!/bin/bash                                                            │ ║
║  │  DATE=$(date +%Y-%m)                                                    │ ║
║  │  REPORT_DIR="reports/$DATE"                                              │ ║
║  │                                                                         │ ║
║  │  mkdir -p "$REPORT_DIR"                                                  │ ║
║  │                                                                         │ ║
║  │  # Create cover page from text                                          │ ║
║  │  echo "Monthly Report - $DATE" | convert -page A4 \                      │ ║
║  │      -pointsize 48 -gravity center text:- "$REPORT_DIR/cover.pdf"        │ ║
║  │                                                                         │ ║
║  │  # Convert images to PDF                                                │ ║
║  │  convert charts/*.png "$REPORT_DIR/charts.pdf"                           │ ║
║  │                                                                         │ ║
║  │  # Combine all PDFs                                                     │ ║
║  │  pdftk "$REPORT_DIR/cover.pdf" \                                        │ ║
║  │      data/*.pdf \                                                        │ ║
║  │      "$REPORT_DIR/charts.pdf" \                                          │ ║
║  │      cat output "$REPORT_DIR/monthly_report_$DATE.pdf"                   │ ║
║  │                                                                         │ ║
║  │  # Compress final report                                                │ ║
║  │  gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \                            │ ║
║  │      -o "$REPORT_DIR/final_report.pdf" \                                │ ║
║  │      "$REPORT_DIR/monthly_report_$DATE.pdf"                             │ ║
║  │                                                                         │ ║
║  └─────────────────────────────────────────────────────────────────────────┘ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 4: PDF Batch Processing

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  ⚡ SCENARIO: Batch PDF Processing                                           ║
║                                                                               ║
║  Problem: Process multiple PDFs - compress, add watermark, encrypt          ║
║  in a single automated pipeline.                                              ║
║                                                                               ║
║  ┌─────────────────────────────────────────────────────────────────────────┐ ║
║  │                                                                         │ ║
║  │  #!/bin/bash                                                            │ ║
║  │  INPUT_DIR="raw_pdfs"                                                   │ ║
║  │  OUTPUT_DIR="processed"                                                  │ ║
║  │  WATERMARK="watermark.pdf"                                               │ ║
║  │                                                                         │ ║
║  │  mkdir -p "$OUTPUT_DIR"                                                  │ ║
║  │                                                                         │ ║
║  │  for pdf in "$INPUT_DIR"/*.pdf; do                                       │ ║
║  │      name=$(basename "$pdf")                                             │ ║
║  │      temp="$OUTPUT_DIR/temp.pdf"                                         │ ║
║  │      output="$OUTPUT_DIR/$name"                                          │ ║
║  │                                                                         │ ║
║  │      # Step 1: Compress                                                  │ ║
║  │      gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook -o "$temp" "$pdf"         │ ║
║  │                                                                         │ ║
║  │      # Step 2: Add watermark (using Python)                              │ ║
║  │      python3 << EOF                                                      │ ║
║  │  import PyPDF2                                                           │ ║
║  │  reader = PyPDF2.PdfReader('$temp')                                      │ ║
║  │  wm = PyPDF2.PdfReader('$WATERMARK')                                     │ ║
║  │  writer = PyPDF2.PdfWriter()                                             │ ║
║  │  for page in reader.pages:                                               │ ║
║  │      page.merge_page(wm.pages[0])                                        │ ║
║  │      writer.add_page(page)                                               │ ║
║  │  with open('$output', 'wb') as f:                                        │ ║
║  │      writer.write(f)                                                     │ ║
║  │  EOF                                                                     │ ║
║  │                                                                         │ ║
║  │      rm "$temp"                                                          │ ║
║  │      echo "Processed: $name"                                             │ ║
║  │  done                                                                   │ ║
║  │                                                                         │ ║
║  └─────────────────────────────────────────────────────────────────────────┘ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### Scenario 5: PDF Text Extraction for Analysis

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  📝 SCENARIO: PDF Text Extraction Pipeline                                   ║
║                                                                               ║
║  Problem: Extract text from multiple PDFs for data analysis and             ║
║  generate summary statistics.                                                 ║
║                                                                               ║
║  ┌─────────────────────────────────────────────────────────────────────────┐ ║
║  │                                                                         │ ║
║  │  #!/bin/bash                                                            │ ║
║  │  INPUT_DIR="documents"                                                   │ ║
║  │  OUTPUT_DIR="extracted_text"                                             │ ║
║  │                                                                         │ ║
║  │  mkdir -p "$OUTPUT_DIR"                                                  │ ║
║  │                                                                         │ ║
║  │  echo "Document,Pages,WordCount,Size" > stats.csv                        │ ║
║  │                                                                         │ ║
║  │  for pdf in "$INPUT_DIR"/*.pdf; do                                       │ ║
║  │      name=$(basename "$pdf" .pdf)                                        │ ║
║  │      txt="$OUTPUT_DIR/${name}.txt"                                       │ ║
║  │                                                                         │ ║
║  │      # Extract text with layout                                          │ ║
║  │      pdftotext -layout "$pdf" "$txt"                                     │ ║
║  │                                                                         │ ║
║  │      # Collect statistics                                                │ ║
║  │      pages=$(pdfinfo "$pdf" | grep Pages | awk '{print $2}')             │ ║
║  │      words=$(wc -w < "$txt")                                             │ ║
║  │      size=$(du -h "$pdf" | cut -f1)                                      │ ║
║  │                                                                         │ ║
║  │      echo "$name,$pages,$words,$size" >> stats.csv                       │ ║
║  │      echo "Extracted: $name"                                             │ ║
║  │  done                                                                   │ ║
║  │                                                                         │ ║
║  │  echo "Text extraction complete. Stats saved to stats.csv"               │ ║
║  │                                                                         │ ║
║  └─────────────────────────────────────────────────────────────────────────┘ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: PDF Tools Ecosystem

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      PDF TOOLS ECOSYSTEM IN TERMUX                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    PDF MANIPULATION TOOLS                            │   │
│   │                                                                       │   │
│   │   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐            │   │
│   │   │  pdftk   │  │   qpdf   │  │ poppler  │  │imagemagick│            │   │
│   │   │          │  │          │  │          │  │          │            │   │
│   │   │ • Merge  │  │ • Linear │  │ • ToText │  │ • ToPDF  │            │   │
│   │   │ • Split  │  │ • Encrypt│  │ • ToHTML │  │ • ToImg  │            │   │
│   │   │ • Rotate │  │ • Optimize│ │ • ToImg  │  │ • Resize │            │   │
│   │   │ • Encrypt│  │ • Inspect│  │ • Info   │  │          │            │   │
│   │   └──────────┘  └──────────┘  └──────────┘  └──────────┘            │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                   │                                         │
│                                   ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    PROGRAMMING INTERFACE                             │   │
│   │                                                                       │   │
│   │   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │   │
│   │   │   PyPDF2     │  │   reportlab  │  │   pypdf      │              │   │
│   │   │   (Python)   │  │   (Python)   │  │   (Python)   │              │   │
│   │   └──────────────┘  └──────────────┘  └──────────────┘              │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                   │                                         │
│                                   ▼                                         │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                    BACKEND LIBRARIES                                 │   │
│   │                                                                       │   │
│   │   libjpeg, libpng, zlib, freetype, ghostscript, poppler              │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: PDF Processing Pipeline

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       PDF PROCESSING PIPELINE                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────┐     ┌─────────────┐     ┌─────────────┐                   │
│   │ Input PDF   │────▶│   Parser    │────▶│  Operations │                   │
│   │             │     │             │     │             │                   │
│   └─────────────┘     └─────────────┘     └─────────────┘                   │
│                                                   │                         │
│                    ┌──────────────────────────────┼──────────┐              │
│                    │                              │          │              │
│                    ▼                              ▼          ▼              │
│             ┌──────────┐                   ┌──────────┐ ┌──────────┐        │
│             │  Merge   │                   │  Split   │ │ Compress │        │
│             └──────────┘                   └──────────┘ └──────────┘        │
│                    │                              │          │              │
│                    ▼                              ▼          ▼              │
│             ┌──────────┐                   ┌──────────┐ ┌──────────┐        │
│             │ Encrypt  │                   │  Rotate  │ │  Extract │        │
│             └──────────┘                   └──────────┘ └──────────┘        │
│                    │                              │          │              │
│                    └──────────────────────────────┼──────────┘              │
│                                                   │                         │
│                                                   ▼                         │
│                                           ┌─────────────┐                   │
│                                           │ Output PDF  │                   │
│                                           │             │                   │
│                                           └─────────────┘                   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: PDF Encryption Levels

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       PDF ENCRYPTION LEVELS                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   Security Level ▲                                                          │
│                  │                                                           │
│     Very High    │  ┌─────────────────┐                                     │
│                  │  │ 256-bit AES     │ ●●●●● Recommended                  │
│                  │  │ qpdf --encrypt  │                                     │
│                  │  └─────────────────┘                                     │
│                  │         ┌─────────────────┐                               │
│        High      │         │ 128-bit AES    │ ●●●●○ Good                     │
│                  │         │ pdftk/qpdf     │                               │
│                  │         └─────────────────┘                               │
│                  │              ┌─────────────────┐                          │
│      Medium      │              │ 128-bit RC4   │ ●●●○○ Legacy              │
│                  │              │ older PDFs    │                          │
│                  │              └─────────────────┘                          │
│                  │                   ┌─────────────────┐                     │
│         Low      │                   │ 40-bit RC4    │ ●●○○○ Weak           │
│                  │                   │ PDF 1.3       │                     │
│                  │                   └─────────────────┘                     │
│                  │                                                           │
│                  └──────────────────────────────────────────────────▶        │
│                              Compatibility                                   │
│                                                                              │
│   Note: Higher security = Less compatibility with old readers              │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Prerequisite Chapters | Description |
|----------------------|-------------|
| Ch1-Introduction to Termux | Basic Termux setup |
| Ch3-Package Management | Installing packages |
| Ch5-Storage Setup | Understanding storage paths |
| Ch40-File Compression | Compressing PDF files |
| Ch41-Image & Media Tools | Image to PDF conversion |

| Next Chapters | Description |
|--------------|-------------|
| Ch43-Task Automation | Automating PDF processing |
| Ch44-Termux Widgets | Quick PDF shortcuts |

---

## 🏆 BONUS ADVANCED CONTENT

### Advanced Technique 1: Intelligent PDF Splitter

```bash
#!/bin/bash
# smart-pdf-splitter.sh
# Split PDF based on bookmarks or page patterns

PDF="$1"
OUTPUT_DIR="split_output"
mkdir -p "$OUTPUT_DIR"

# Method 1: Split by bookmark chapters (if bookmarks exist)
pdftk "$PDF" dump_data | grep BookmarkTitle | while read line; do
    # Process bookmarks
    chapter=$(echo "$line" | cut -d' ' -f2-)
    echo "Found chapter: $chapter"
done

# Method 2: Split by page patterns (e.g., new chapter starts with specific pattern)
for i in {1..10}; do
    start=$(( (i-1)*10 + 1 ))
    end=$((i*10))
    pdftk "$PDF" cat $start-$end output "$OUTPUT_DIR/section_$i.pdf"
done

# Method 3: Split by file size (create parts under 5MB)
pdftk "$PDF" burst output "$OUTPUT_DIR/page_%04d.pdf"
```

### Advanced Technique 2: PDF Comparison Tool

```bash
#!/bin/bash
# pdf-compare.sh
# Compare two PDFs and highlight differences

PDF1="$1"
PDF2="$2"
OUTPUT="comparison.pdf"

# Convert to images
mkdir -p /tmp/pdf_compare
pdftoppm "$PDF1" /tmp/pdf_compare/doc1 -png
pdftoppm "$PDF2" /tmp/pdf_compare/doc2 -png

# Compare each page
for img in /tmp/pdf_compare/doc1-*.png; do
    num=$(basename "$img" | sed 's/doc1-//' | sed 's/.png//')
    img2="/tmp/pdf_compare/doc2-$num.png"
    
    if [ -f "$img2" ]; then
        # Create difference image
        compare "$img" "$img2" "/tmp/pdf_compare/diff-$num.png"
        echo "Compared page $num"
    fi
done

# Combine into PDF
convert /tmp/pdf_compare/diff-*.png "$OUTPUT"
rm -rf /tmp/pdf_compare
```

### Advanced Technique 3: PDF Report Generator

```python
#!/usr/bin/env python3
# pdf_report_generator.py
# Generate professional PDF reports

from reportlab.lib.pagesizes import A4
from reportlab.lib.styles import getSampleStyleSheet
from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer, Table, Image
from reportlab.lib import colors
import datetime

def generate_report(title, data, output_file):
    doc = SimpleDocTemplate(output_file, pagesize=A4)
    styles = getSampleStyleSheet()
    story = []
    
    # Title
    story.append(Paragraph(title, styles['Title']))
    story.append(Spacer(1, 20))
    
    # Date
    story.append(Paragraph(f"Generated: {datetime.date.today()}", styles['Normal']))
    story.append(Spacer(1, 30))
    
    # Table
    table_data = [['Item', 'Value', 'Status']]
    for item, value, status in data:
        table_data.append([item, str(value), status])
    
    table = Table(table_data)
    table.setStyle([
        ('BACKGROUND', (0, 0), (-1, 0), colors.grey),
        ('TEXTCOLOR', (0, 0), (-1, 0), colors.whitesmoke),
        ('ALIGN', (0, 0), (-1, -1), 'CENTER'),
        ('FONTSIZE', (0, 0), (-1, 0), 12),
        ('BOTTOMPADDING', (0, 0), (-1, 0), 12),
        ('GRID', (0, 0), (-1, -1), 1, colors.black)
    ])
    story.append(table)
    
    doc.build(story)
    print(f"Report generated: {output_file}")

# Usage
data = [
    ['Downloads', 1234, '✓'],
    ['Processing', 567, '✓'],
    ['Errors', 5, '⚠']
]
generate_report("Monthly Statistics", data, "report.pdf")
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

- [ ] **PDF Tools Installation**
  - pdftk installed and verified
  - qpdf installed and verified
  - poppler-utils installed
  - ImageMagick installed
  - PyPDF2 installed

- [ ] **PDF Operations**
  - Merge multiple PDFs
  - Split PDF into pages
  - Extract specific pages
  - Rotate PDF pages

- [ ] **PDF Conversion**
  - PDF to text extraction
  - PDF to images
  - Images to PDF
  - PDF compression

- [ ] **PDF Security**
  - Add password protection
  - Remove password
  - Set permissions
  - Understand encryption levels

- [ ] **Advanced Features**
  - PDF metadata editing
  - Watermark addition
  - PDF inspection
  - Form handling

- [ ] **Python Integration**
  - PyPDF2 basics
  - Programmatic PDF manipulation
  - Report generation

---

## 🎮 INTERACTIVE QUIZ

Test your PDF Tools knowledge! Click to reveal answers.

<details>
<summary><b>Q1: Which tool is best for merging multiple PDF files?</b></summary>

**Answer: pdftk**

`pdftk file1.pdf file2.pdf cat output merged.pdf` - pdftk is the most versatile tool for PDF manipulation including merging, splitting, and rotating.
</details>

<details>
<summary><b>Q2: What command extracts text from a PDF while preserving layout?</b></summary>

**Answer: pdftotext -layout**

`pdftotext -layout input.pdf output.txt` - The `-layout` flag maintains the original formatting and structure of the text.
</details>

<details>
<summary><b>Q3: Which encryption level is most secure for PDF passwords?</b></summary>

**Answer: 256-bit AES**

qpdf supports 256-bit AES encryption: `qpdf --encrypt user owner 256 -- input.pdf output.pdf` - This is the strongest encryption available.
</details>

<details>
<summary><b>Q4: How do you convert PDF pages to PNG images?</b></summary>

**Answer: pdftoppm -png**

`pdftoppm input.pdf output -png` creates output-1.png, output-2.png, etc. for each page.
</details>

<details>
<summary><b>Q5: Which tool provides the best PDF compression?</b></summary>

**Answer: Ghostscript with /screen setting**

`gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -o output.pdf input.pdf` can reduce file size by 70-90%.
</details>

<details>
<summary><b>Q6: How do you extract only pages 5-10 from a PDF?</b></summary>

**Answer: pdftk input.pdf cat 5-10 output extracted.pdf**

This command extracts the specified page range into a new PDF file.
</details>

<details>
<summary><b>Q7: What is the purpose of qpdf's linearize option?</b></summary>

**Answer: Optimize for fast web viewing**

`qpdf --linearize input.pdf output.pdf` reorganizes the PDF so the first page loads while the rest downloads - perfect for web sharing.
</details>

<details>
<summary><b>Q8: How do you remove a password from a PDF (with known password)?</b></summary>

**Answer: qpdf --password=pass --decrypt protected.pdf output.pdf**

Or with pdftk: `pdftk protected.pdf input_pw password output unprotected.pdf`
</details>

<details>
<summary><b>Q9: Which Python library is commonly used for PDF manipulation?</b></summary>

**Answer: PyPDF2**

PyPDF2 allows programmatic PDF operations like merging, splitting, and text extraction through Python scripts.
</details>

<details>
<summary><b>Q10: How do you rotate a PDF page 90 degrees clockwise?</b></summary>

**Answer: pdftk input.pdf cat 1-endright output rotated.pdf**

The `right` suffix rotates pages 90° clockwise. Use `left` for counter-clockwise, `down` for 180°.
</details>

<details>
<summary><b>Q11: What is the difference between user password and owner password?</b></summary>

**Answer: User password opens the PDF; owner password controls permissions**

User password is required to view the document. Owner password is needed to change permissions like printing, copying, or modifying.
</details>

<details>
<summary><b>Q12: How do you split a PDF into individual pages?</b></summary>

**Answer: pdftk input.pdf burst output page_%d.pdf**

The `burst` command creates separate files for each page with the specified naming pattern.
</details>

<details>
<summary><b>Q13: Which flag in pdftoppm controls output resolution?</b></summary>

**Answer: -r (resolution)**

`pdftoppm -r 300 input.pdf output -png` generates images at 300 DPI for high-quality output.
</details>

<details>
<summary><b>Q14: How do you add a watermark to all PDF pages?</b></summary>

**Answer: Use PyPDF2 to merge watermark with each page**

```python
import PyPDF2
reader = PyPDF2.PdfReader('input.pdf')
watermark = PyPDF2.PdfReader('watermark.pdf')
writer = PyPDF2.PdfWriter()
for page in reader.pages:
    page.merge_page(watermark.pages[0])
    writer.add_page(page)
```
</details>

<details>
<summary><b>Q15: What is the safest compression level for important documents?</b></summary>

**Answer: /printer (300 DPI)**

Ghostscript's `/printer` setting maintains high quality while still providing 20-40% size reduction. Use `/default` for no quality loss.
</details>

---

## 🎯 INTERVIEW QUESTIONS

### Q1: Explain the differences between pdftk, qpdf, and poppler-utils.

**Answer:**
- **pdftk**: Swiss Army knife for PDF - best for merge, split, rotate, encrypt/decrypt operations. User-friendly syntax.
- **qpdf**: Specialized in structural operations - linearization, encryption, optimization. Better at preserving PDF structure.
- **poppler-utils**: Focus on conversion - PDF to text, HTML, images. Based on poppler library for rendering.

Choose based on task: pdftk for manipulation, qpdf for optimization/encryption, poppler for extraction/conversion.

### Q2: How would you automate daily PDF backups with compression?

**Answer:**
```bash
#!/bin/bash
BACKUP_DIR="/sdcard/backups"
DATE=$(date +%Y%m%d)
# Compress PDFs older than 7 days
find ~/documents -name "*.pdf" -mtime +7 -exec gs -sDEVICE=pdfwrite \
  -dPDFSETTINGS=/ebook -o "$BACKUP_DIR/compressed_$DATE.pdf" {} \;
# Rotate old backups
ls -t $BACKUP_DIR/*.pdf | tail -n +8 | xargs rm -f
```
Add to crontab: `0 2 * * * /path/to/backup.sh`

### Q3: What are the security considerations when handling PDF passwords?

**Answer:**
1. **Encryption levels**: Use 256-bit AES (strongest), avoid 40-bit RC4 (weak)
2. **Two password types**: User password (viewing), Owner password (permissions)
3. **Password removal**: Only remove passwords from documents you own
4. **Audit trail**: Log all encryption/decryption operations
5. **Key management**: Store passwords securely, never in plain text scripts
6. **Legal compliance**: PDF password removal may violate laws in some jurisdictions

### Q4: How would you handle a corrupted PDF file?

**Answer:**
```bash
# Step 1: Try qpdf for structure repair
qpdf --input-password=pass --check input.pdf

# Step 2: Use Ghostscript to rebuild
gs -sDEVICE=pdfwrite -o repaired.pdf input.pdf

# Step 3: Extract salvageable pages with pdftk
pdftk input.pdf cat 1-10 12-end output partial.pdf

# Step 4: If severely corrupted, extract text
pdftotext -layout input.pdf recovered_text.txt
```

### Q5: Explain PDF linearization and when to use it.

**Answer:**
**Linearization** reorganizes PDF internal structure for progressive web display. The first page displays while remaining pages download.

**When to use:**
- Web-hosted PDFs for fast initial display
- Large documents shared online
- Mobile viewing optimization
- Streaming PDF content

**Implementation:**
```bash
qpdf --linearize input.pdf web_optimized.pdf
# Or with pdftk
pdftk input.pdf cat output linearized.pdf
```

**Trade-off:** Slightly larger file size for better user experience.

### Q6: How do you merge PDFs with specific page selections from each?

**Answer:**
```bash
# Assign handles to files, then specify pages
pdftk A=report.pdf B=appendix.pdf C=covers.pdf \
  cat C1 A1-5 A7-10 B1-20 output final_report.pdf

# Explanation:
# C1 = First page from covers.pdf
# A1-5 = Pages 1-5 from report.pdf
# A7-10 = Pages 7-10 (skipping page 6) from report.pdf
# B1-20 = First 20 pages from appendix.pdf
```

### Q7: What's the most efficient way to batch convert 100 PDFs to images?

**Answer:**
```bash
# Method 1: Using GNU parallel (fastest)
pkg install parallel
find . -name "*.pdf" | parallel -j 4 pdftoppm -jpeg -r 150 {} {.}

# Method 2: Simple loop with background jobs
for pdf in *.pdf; do
  pdftoppm -jpeg -r 150 "$pdf" "${pdf%.pdf}" &
  # Limit concurrent jobs
  if (( $(jobs -r | wc -l) >= 4 )); then wait -n; fi
done
wait

# Method 3: Using xargs
ls *.pdf | xargs -P 4 -I {} pdftoppm -jpeg -r 150 {} {.}
```

### Q8: How would you implement PDF text extraction with OCR for scanned documents?

**Answer:**
```bash
# Install OCR tools
pkg install tesseract tesseract-data-eng

# Convert PDF to images, then OCR
pdftoppm -png scanned_doc.pdf temp_page
for img in temp_page-*.png; do
  tesseract "$img" "${img%.png}" -l eng
done

# Combine all text
cat temp_page-*.txt > extracted_text.txt
rm temp_page-*.png temp_page-*.txt
```

For better results, use OCRmyPDF: `pkg install ocrmypdf`

### Q9: Explain the PDF compression trade-offs between different quality settings.

**Answer:**
| Setting | DPI | Quality | Size Reduction | Use Case |
|---------|-----|---------|----------------|----------|
| /screen | 72 | Low | 70-90% | Web preview, email |
| /ebook | 150 | Medium | 50-70% | Tablets, e-readers |
| /printer | 300 | High | 20-40% | Professional printing |
| /default | Original | Full | 0-10% | Archive, no loss |

**Decision factors:**
- Viewing device capability
- Required text clarity
- Image importance
- Storage constraints
- Download speed needs

### Q10: How do you handle PDFs with embedded fonts that won't display correctly?

**Answer:**
```bash
# Step 1: Check embedded fonts
pdffonts document.pdf

# Step 2: Extract to images (preserves visual)
pdftoppm -png -r 300 document.pdf output

# Step 3: Rebuild with standard fonts
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \
   -dEmbedAllFonts=true -dSubsetFonts=true \
   -o fixed.pdf document.pdf

# Step 4: For text extraction with encoding issues
pdftotext -enc UTF-8 -layout document.pdf output.txt
```

---

## 🔥 REAL-WORLD SCENARIOS

### Scenario 1: Office Document Processing Pipeline

```
┌──────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  SITUATION: Process 50 daily reports - merge, compress, and email       │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────┤
|                                                                          │
│  PROBLEM:                                                                │
│  • 50 separate PDF reports from different departments                   │
│  • Each 2-5 MB, total 150+ MB                                           │
│  • Need single merged document under 10 MB for email                    │
│  • Must preserve page order by department                               │
|                                                                          │
│  SOLUTION:                                                               │
|  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ #!/bin/bash                                                         │ │
│  │ # Daily Report Processor                                            │ │
│  │                                                                     │ │
│  │ DATE=$(date +%Y%m%d)                                                │ │
│  │ WORK_DIR=~/reports/daily                                            │ │
│  │                                                                     │ │
│  │ # Sort by department code in filename                               │ │
│  │ sorted_files=$(ls $WORK_DIR/*.pdf | sort -t_ -k2)                   │ │
│  │                                                                     │ │
│  │ # Merge with pdftk                                                  │ │
│  │ pdftk $sorted_files cat output $WORK_DIR/merged_$DATE.pdf          │ │
│  │                                                                     │ │
│  │ # Compress with Ghostscript                                         │ │
│  │ gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \                        │ │
│  │    -o $WORK_DIR/final_$DATE.pdf $WORK_DIR/merged_$DATE.pdf         │ │
│  │                                                                     │ │
│  │ # Email using termux-api                                            │ │
│  │ termux-share --action email $WORK_DIR/final_$DATE.pdf              │ │
│  └────────────────────────────────────────────────────────────────────┘ │
|                                                                          │
│  RESULT: 150 MB → 8 MB, ready for email attachment                      │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 2: Secure Document Distribution

```
┌──────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  SITUATION: Distribute confidential reports to team members             │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────┤
|                                                                          │
│  PROBLEM:                                                                │
│  • Sensitive financial documents                                        │
│  • Need unique password for each recipient                              │
│  • Must restrict printing and copying                                   │
│  • Track distribution                                                   │
|                                                                          │
│  SOLUTION:                                                               │
|  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ #!/bin/bash                                                         │ │
│  │ # Secure Document Distributor                                       │ │
│  │                                                                     │ │
│  │ DOC="confidential_report.pdf"                                       │ │
│  │ declare -A RECIPIENTS=(                                             │ │
│  │   ["alice"]="AlicePass123"                                          │ │
│  │   ["bob"]="BobSecure456"                                            │ │
│  │   ["charlie"]="CharlieKey789"                                       │ │
│  │ )                                                                   │ │
│  │                                                                     │ │
│  │ for name in "${!RECIPIENTS[@]}"; do                                 │ │
│  │   pass="${RECIPIENTS[$name]}"                                       │ │
│  │   output="${name}_${DOC}"                                           │ │
│  │                                                                     │ │
│  │   # Encrypt with restrictions                                       │ │
│  │   pdftk $DOC output $output user_pw $pass \                        │ │
│  │     owner_pw AdminOwnerKey allow printing                           │ │
│  │                                                                     │ │
│  │   # Log distribution                                                │ │
│  │   echo "$(date): Created $output for $name" >> distribution.log    │ │
│  │ done                                                                │ │
│  └────────────────────────────────────────────────────────────────────┘ │
|                                                                          │
│  RESULT: Each recipient gets unique password-protected document         │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 3: Archive Digitization Project

```
┌──────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  SITUATION: Digitize 1000 scanned documents with OCR                    │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────┤
|                                                                          │
│  PROBLEM:                                                                │
│  • Scanned PDFs have no searchable text                                 │
│  • Multiple pages per document                                          │
│  • Need to make them searchable                                         │
│  • Preserve original appearance                                         │
|                                                                          │
│  SOLUTION:                                                               │
|  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ #!/bin/bash                                                         │ │
│  │ # Batch OCR Processor                                               │ │
│  │                                                                     │ │
│  │ pkg install ocrmypdf tesseract-data-eng                            │ │
│  │                                                                     │ │
│  │ INPUT_DIR="/sdcard/Scans"                                           │ │
│  │ OUTPUT_DIR="/sdcard/SearchablePDFs"                                 │ │
│  │                                                                     │ │
│  │ mkdir -p $OUTPUT_DIR                                                │ │
│  │                                                                     │ │
│  │ for pdf in "$INPUT_DIR"/*.pdf; do                                   │ │
│  │   filename=$(basename "$pdf")                                       │ │
│  │   echo "Processing: $filename"                                      │ │
│  │                                                                     │ │
│  │   # Add OCR layer while preserving original                         │ │
│  │   ocrmypdf --deskew --clean \                                       │ │
│  │     --language eng \                                                │ │
│  │     "$pdf" "$OUTPUT_DIR/$filename" 2>/dev/null                      │ │
│  │                                                                     │ │
│  │   # Compress result                                                 │ │
│  │   gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \                      │ │
│  │     -o "$OUTPUT_DIR/optimized_$filename" \                          │ │
│  │     "$OUTPUT_DIR/$filename"                                         │ │
│  │ done                                                                │ │
│  └────────────────────────────────────────────────────────────────────┘ │
|                                                                          │
│  RESULT: 1000 searchable, optimized PDFs                                 │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 4: Multi-Format Report Generator

```
┌──────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  SITUATION: Generate reports in multiple formats from single source     │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────┤
|                                                                          │
│  PROBLEM:                                                                │
│  • Single PDF source document                                           │
│  • Need PDF, images, and text versions                                  │
│  • Different quality requirements                                       │
│  • Automated distribution                                               │
|                                                                          │
│  SOLUTION:                                                               │
|  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ #!/bin/bash                                                         │ │
│  │ # Multi-Format Report Generator                                     │ │
│  │                                                                     │ │
│  │ SOURCE="report.pdf"                                                 │ │
│  │ BASENAME=$(basename "$SOURCE" .pdf)                                 │ │
│  │ OUTPUT_DIR="~/reports/output"                                       │ │
│  │                                                                     │ │
│  │ mkdir -p $OUTPUT_DIR/{pdf,images,text}                              │ │
│  │                                                                     │ │
│  │ # 1. Compressed PDF for web                                        │ │
│  │ gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \                        │ │
│  │    -o "$OUTPUT_DIR/pdf/${BASENAME}_web.pdf" "$SOURCE"              │ │
│  │                                                                     │ │
│  │ # 2. High-res images for print                                     │ │
│  │ pdftoppm -png -r 300 "$SOURCE" "$OUTPUT_DIR/images/${BASENAME}"    │ │
│  │                                                                     │ │
│  │ # 3. Plain text for data processing                                │ │
│  │ pdftotext -layout "$SOURCE" "$OUTPUT_DIR/text/${BASENAME}.txt"     │ │
│  │                                                                     │ │
│  │ # 4. Thumbnail preview                                             │ │
│  │ pdftoppm -png -r 72 -f 1 -l 1 "$SOURCE" "$OUTPUT_DIR/thumbnail"    │ │
│  │                                                                     │ │
│  │ echo "Generated all formats in $OUTPUT_DIR"                        │ │
│  └────────────────────────────────────────────────────────────────────┘ │
|                                                                          │
│  RESULT: One source → 4 output formats automatically                    │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

### Scenario 5: Legal Document Redaction

```
┌──────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│  SITUATION: Redact sensitive information before document release        │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────┤
|                                                                          │
│  PROBLEM:                                                                │
│  • Legal document with sensitive names/numbers                          │
│  • Must completely remove (not just hide) information                   │
│  • Verify no trace remains                                              │
│  • Maintain document structure                                          │
|                                                                          │
│  SOLUTION:                                                               │
|  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ #!/bin/bash                                                         │ │
│  │ # Secure Redaction Process                                          │ │
│  │                                                                     │ │
│  │ INPUT="legal_document.pdf"                                          │ │
│  │ OUTPUT="redacted_document.pdf"                                      │ │
│  │                                                                     │ │
│  │ # Step 1: Convert to images (removes all hidden data)              │ │
│  │ pdftoppm -png -r 300 "$INPUT" temp_page                            │ │
│  │                                                                     │ │
│  │ # Step 2: Use ImageMagick to black out regions                     │ │
│  │ for img in temp_page-*.png; do                                     │ │
│  │   # Example: black out coordinates (adjust as needed)              │ │
│  │   convert "$img" -fill black -draw "rectangle 100,200 300,250" \   │ │
│  │     -draw "rectangle 400,300 600,350" "$img"                       │ │
│  │ done                                                                │ │
│  │                                                                     │ │
│  │ # Step 3: Rebuild PDF from images                                  │ │
│  │ convert temp_page-*.png "$OUTPUT"                                  │ │
│  │                                                                     │ │
│  │ # Step 4: Verify - check for text patterns                         │ │
│  │ pdftotext "$OUTPUT" - | grep -i "sensitive\|pattern" && \          │ │
│  │   echo "WARNING: Pattern found!" || echo "Redaction verified"      │ │
│  │                                                                     │ │
│  │ # Cleanup                                                           │ │
│  │ rm -f temp_page-*.png                                              │ │
│  └────────────────────────────────────────────────────────────────────┘ │
|                                                                          │
│  RESULT: Completely sanitized document with no recoverable data         │
│                                                                          │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 ARCHITECTURE DIAGRAMS

### Diagram 1: PDF Tool Selection Flowchart

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PDF TOOL SELECTION FLOWCHART                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                         ┌─────────────┐                                 │
│                         │  PDF Task?  │                                 │
│                         └──────┬──────┘                                 │
│                                │                                        │
│              ┌─────────────────┼─────────────────┐                      │
│              │                 │                 │                      │
│              ▼                 ▼                 ▼                      │
│      ┌───────────────┐ ┌───────────────┐ ┌───────────────┐             │
│      │   MERGE/SPLIT │ │   CONVERT     │ │  EXTRACT      │             │
│      │   /ROTATE     │ │   /COMPRESS   │ │   /VIEW       │             │
│      └───────┬───────┘ └───────┬───────┘ └───────┬───────┘             │
│              │                 │                 │                      │
│              ▼                 ▼                 ▼                      │
│      ┌───────────────┐ ┌───────────────┐ ┌───────────────┐             │
│      │    pdftk      │ │  Ghostscript  │ │  poppler      │             │
│      │    or qpdf    │ │  for compress │ │  for text/img │             │
│      └───────────────┘ └───────────────┘ └───────────────┘             │
│                                                                          │
│              │                 │                 │                      │
│              ▼                 ▼                 ▼                      │
│      ┌───────────────────────────────────────────────────────┐         │
│      │                    OUTPUT FILE                         │         │
│      │                                                       │         │
│      │  • merged.pdf    • compressed.pdf    • text.txt       │         │
│      │  • split_*.pdf   • optimized.pdf     • images/*.png   │         │
│      │  • rotated.pdf   • web_ready.pdf     • extracted.pdf  │         │
│      └───────────────────────────────────────────────────────┘         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 2: PDF Processing Pipeline

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PDF PROCESSING PIPELINE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  INPUT SOURCE                                                            │
│       │                                                                  │
│       ▼                                                                  │
│  ┌─────────┐     ┌─────────┐     ┌─────────┐     ┌─────────┐           │
│  │ PDF     │────▶│ PRE-    │────▶│ PROCESS │────▶│ POST-   │           │
│  │ FILE    │     │ PROCESS │     │         │     │ PROCESS │           │
│  └─────────┘     └─────────┘     └─────────┘     └─────────┘           │
│                       │               │               │                 │
│                       ▼               ▼               ▼                 │
│                  ┌─────────┐     ┌─────────┐     ┌─────────┐           │
│                  │ VALIDATE│     │ OPERATE │     │ VERIFY  │           │
│                  │ • Check │     │ • Merge │     │ • Check │           │
│                  │ • Scan  │     │ • Split │     │ • Test  │           │
│                  │ • Info  │     │ • Convert│    │ • Log   │           │
│                  └─────────┘     └─────────┘     └─────────┘           │
│                                      │                                  │
│                                      ▼                                  │
│                    ┌─────────────────────────────────────┐              │
│                    │         OPERATIONS MATRIX           │              │
│                    ├─────────────┬───────────────────────┤              │
│                    │ pdftk       │ merge, split, encrypt │              │
│                    │ qpdf        │ linearize, optimize   │              │
│                    │ gs          │ compress, convert     │              │
│                    │ poppler     │ extract text/images   │              │
│                    │ imagemagick │ images ↔ PDF          │              │
│                    └─────────────┴───────────────────────┘              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Diagram 3: PDF Encryption Workflow

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PDF ENCRYPTION WORKFLOW                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                    ┌─────────────────────┐                              │
│                    │   UNPROTECTED PDF   │                              │
│                    └──────────┬──────────┘                              │
│                               │                                         │
│                               ▼                                         │
│              ┌────────────────────────────────┐                         │
│              │     ENCRYPTION DECISION        │                         │
│              │                                │                         │
│              │  ┌──────────┐   ┌──────────┐  │                         │
│              │  │ pdftk    │   │  qpdf    │  │                         │
│              │  │ 128-bit  │   │ 256-bit  │  │                         │
│              │  └──────────┘   └──────────┘  │                         │
│              └────────────────┬───────────────┘                         │
│                               │                                         │
│                               ▼                                         │
│              ┌────────────────────────────────┐                         │
│              │    PASSWORD CONFIGURATION      │                         │
│              │                                │                         │
│              │  user_pw: User password        │                         │
│              │  owner_pw: Owner password      │                         │
│              │  allow: Permissions            │                         │
│              │    • printing                  │                         │
│              │    • copy                      │                         │
│              │    • modifyannotations         │                         │
│              │    • AllFeatures               │                         │
│              └────────────────┬───────────────┘                         │
│                               │                                         │
│                               ▼                                         │
│                    ┌─────────────────────┐                              │
│                    │   PROTECTED PDF     │                              │
│                    │   • Encrypted       │                              │
│                    │   • Restricted      │                              │
│                    │   • Secure          │                              │
│                    └─────────────────────┘                              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🔗 RELATED CHAPTERS

| Chapter | Title | Relationship |
|---------|-------|--------------|
| Ch16 | Python Installation | PyPDF2 requires Python setup |
| Ch17 | Package Management | Installing PDF tools via pkg |
| Ch25 | Termux API | Sharing PDFs via termux-share |
| Ch43 | Task Automation | Automating PDF processing with cron |
| Ch44 | Termux Widgets | Quick PDF shortcuts on home screen |
| Ch35 | File Compression | PDF compression techniques |
| Ch36 | Archive Management | Working with PDF archives |
| Ch45 | SSH Server | Remote PDF processing |

---

## 🏆 BONUS ADVANCED CONTENT

### Technique 1: PDF Batch Watermarking System

```bash
#!/bin/bash
# Advanced PDF Watermarking System

WATERMARK_TEXT="CONFIDENTIAL - $(date +%Y)"
INPUT_DIR="./input"
OUTPUT_DIR="./watermarked"

mkdir -p "$OUTPUT_DIR"

# Create watermark PDF using reportlab
python3 << 'PYTHON_SCRIPT'
from reportlab.pdfgen import canvas
from reportlab.lib.pagesizes import letter
import sys

def create_watermark(text, output="watermark.pdf"):
    c = canvas.Canvas(output, pagesize=letter)
    c.setFont("Helvetica", 40)
    c.setFillColorRGB(0.7, 0.7, 0.7, alpha=0.3)
    c.rotate(45)
    c.drawString(200, 100, text)
    c.save()

create_watermark(sys.argv[1])
PYTHON_SCRIPT "$WATERMARK_TEXT"

# Apply watermark to all PDFs
for pdf in "$INPUT_DIR"/*.pdf; do
    filename=$(basename "$pdf")
    pdftk "$pdf" background watermark.pdf output "$OUTPUT_DIR/$filename"
    echo "Watermarked: $filename"
done

rm watermark.pdf
echo "Batch watermarking complete!"
```

### Technique 2: PDF Form Filling Automation

```bash
#!/bin/bash
# PDF Form Auto-Filler

FORM_TEMPLATE="application_form.pdf"
DATA_FILE="form_data.csv"
OUTPUT_DIR="./filled_forms"

mkdir -p "$OUTPUT_DIR"

# Get form fields
echo "Available form fields:"
pdftk "$FORM_TEMPLATE" dump_data_fields | grep "FieldName:"

# Auto-fill from CSV
while IFS=',' read -r name email phone address; do
    output_file="$OUTPUT_DIR/${name// /_}_form.pdf"
    
    pdftk "$FORM_TEMPLATE" fill_form - << EOF output "$output_file"
---
FieldName: name
FieldValue: $name

FieldName: email
FieldValue: $email

FieldName: phone
FieldValue: $phone

FieldName: address
FieldValue: $address
EOF
    
    echo "Generated: $output_file"
done < "$DATA_FILE"
```

### Technique 3: PDF Security Auditor

```bash
#!/bin/bash
# PDF Security Analysis Tool

analyze_pdf() {
    local pdf="$1"
    echo "=== Analyzing: $pdf ==="
    
    # Check encryption
    encryption=$(pdftk "$pdf" dump_data 2>/dev/null | grep -i "encrypted" || echo "Not encrypted")
    echo "Encryption: $encryption"
    
    # Check permissions
    echo "Permissions:"
    qpdf --show-encryption "$pdf" 2>/dev/null || echo "  No encryption info"
    
    # Check metadata
    echo "Metadata:"
    pdfinfo "$pdf" 2>/dev/null | grep -E "Creator|Producer|ModDate" || echo "  No metadata"
    
    # Check for JavaScript
    echo "JavaScript: $(pdftk "$pdf" dump_data 2>/dev/null | grep -c "JavaScript" || echo "None")"
    
    # Check for embedded files
    echo "Embedded files: $(pdfinfo "$pdf" 2>/dev/null | grep -c "Embedded" || echo "None")"
    
    # Check file size
    size=$(du -h "$pdf" | cut -f1)
    echo "File size: $size"
    
    # Check for linearization
    linearized=$(qpdf --check "$pdf" 2>&1 | grep -c "linearized" || echo "Not linearized")
    echo "Linearized: $linearized"
    
    echo ""
}

# Analyze all PDFs in directory
for pdf in *.pdf; do
    [ -f "$pdf" ] && analyze_pdf "$pdf"
done
```

---

## 📝 CHAPTER SUMMARY CHECKLIST

### Core Concepts Mastered
- [ ] PDF tool ecosystem understanding (pdftk, qpdf, poppler, ghostscript)
- [ ] PDF merging operations
- [ ] PDF splitting and extraction
- [ ] Text extraction from PDFs
- [ ] PDF to image conversion
- [ ] Image to PDF conversion
- [ ] PDF compression techniques
- [ ] Password protection and encryption
- [ ] Password removal (authorized documents)
- [ ] PDF rotation operations
- [ ] Python PyPDF2 scripting

### Tools Installed
- [ ] pdftk - PDF toolkit
- [ ] qpdf - PDF transformation
- [ ] poppler - PDF rendering utilities
- [ ] ghostscript - PDF processing
- [ ] imagemagick - Image processing
- [ ] PyPDF2 - Python PDF library

### Practical Skills
- [ ] Merge multiple PDFs into single document
- [ ] Extract specific pages from PDF
- [ ] Convert PDF pages to images
- [ ] Compress large PDF files
- [ ] Add/remove PDF passwords
- [ ] Rotate PDF pages
- [ ] Extract text with layout preservation
- [ ] Create PDF from images

### Advanced Operations
- [ ] Selective page merging from multiple files
- [ ] Batch PDF processing
- [ ] PDF optimization for web
- [ ] Permission-based encryption
- [ ] Automated PDF workflows

### Integration Skills
- [ ] Use PDF tools in shell scripts
- [ ] Combine with cron for automation
- [ ] Integrate with Termux widgets
- [ ] Python PDF scripting

---

## 💡 PRO TIPS BOX (10 Advanced Tips)

> 💡 **Pro Tip #1:** Use `pdftk input.pdf cat 1-end output new.pdf` to re-linearize PDFs for faster web viewing - great for sharing large documents online.

> 💡 **Pro Tip #2:** For smallest PDF size, use Ghostscript with `/screen` setting: `gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -o output.pdf input.pdf` - can reduce files by 70-90%.

> 💡 **Pro Tip #3:** Extract images from PDF with `pdfimages -j input.pdf output_prefix` - the `-j` flag saves as JPEG instead of raw format.

> 💡 **Pro Tip #4:** Use `qpdf --linearize input.pdf output.pdf` to optimize PDFs for fast web viewing - first page loads while rest downloads.

> 💡 **Pro Tip #5:** Merge PDFs in specific order with `pdftk A=first.pdf B=second.pdf C=third.pdf cat A B C output merged.pdf` - gives you full control over page order.

> 💡 **Pro Tip #6:** Extract text while preserving layout with `pdftotext -layout input.pdf output.txt` - maintains original formatting for better readability.

> 💡 **Pro Tip #7:** Create PDF from images with optimal quality using `convert -quality 90 -density 150 *.jpg output.pdf` - adjusts DPI and compression.

> 💡 **Pro Tip #8:** Use `pdftk input.pdf update_info info.txt output new.pdf` to edit PDF metadata like title, author, subject.

> 💡 **Pro Tip #9:** For password-protected PDFs, qpdf's 256-bit encryption is most secure: `qpdf --encrypt user owner 256 -- input.pdf output.pdf`.

> 💡 **Pro Tip #10:** Batch process PDFs with `for f in *.pdf; do pdftotext "$f" "${f%.pdf}.txt"; done` - converts all PDFs to text files.

---

## 🔥 REAL WORLD USE CASES

### Use Case 1: Document Organization System

```bash
#!/bin/bash
# PDF Organization Script

INPUT_PDF="$1"
OUTPUT_DIR="organized_pdfs"

mkdir -p "$OUTPUT_DIR"

# Get page count
PAGES=$(pdfinfo "$INPUT_PDF" | grep Pages | awk '{print $2}')

# Split into chapters (assuming 10 pages per chapter)
CHAPTERS=$((PAGES / 10))

for ((i=0; i<CHAPTERS; i++)); do
    START=$((i*10 + 1))
    END=$((START + 9))
    
    pdftk "$INPUT_PDF" cat $START-$END output "$OUTPUT_DIR/chapter_$((i+1)).pdf"
    echo "Created chapter_$((i+1)).pdf (pages $START-$END)"
done
```

### Use Case 2: Invoice Processing

```bash
#!/bin/bash
# Invoice PDF Processor

INVOICE_DIR="invoices"
ARCHIVE_DIR="processed"

mkdir -p "$ARCHIVE_DIR"

for pdf in "$INVOICE_DIR"/*.pdf; do
    filename=$(basename "$pdf" .pdf)
    
    # Extract text
    pdftotext "$pdf" "${filename}.txt"
    
    # Extract first page as preview image
    pdftoppm -f 1 -l 1 -png "$pdf" "${filename}_preview"
    
    # Compress PDF
    gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook \
       -o "$ARCHIVE_DIR/${filename}_compressed.pdf" "$pdf"
    
    echo "Processed: $filename"
done
```

### Use Case 3: Study Material Preparation

```bash
#!/bin/bash
# Study Material Merger

OUTPUT="study_material.pdf"
TEMP_DIR=$(mktemp -d)

# Merge all PDFs with chapter numbers
counter=1
for pdf in chapters/*.pdf; do
    # Add chapter number
    pdftk "$pdf" stamp <(echo "Chapter $counter" | convert -pointsize 40 text:- pdf:-) \
        output "$TEMP_DIR/ch_$counter.pdf"
    ((counter++))
done

# Merge all chapters
pdftk "$TEMP_DIR"/*.pdf cat output "$OUTPUT"

rm -rf "$TEMP_DIR"
echo "Created: $OUTPUT"
```

### Use Case 4: Report Generation

```bash
#!/bin/bash
# Generate PDF Report from Images

REPORT_NAME="report_$(date +%Y%m%d).pdf"
IMAGES_DIR="screenshots"

# Sort images by date
cd "$IMAGES_DIR"

# Create PDF with page numbers
convert $(ls -t *.png) \
    -gravity SouthEast \
    -pointsize 20 \
    -fill black \
    -annotate +10+10 "Page %p" \
    "../$REPORT_NAME"

echo "Report created: $REPORT_NAME"
```

### Productivity Hacks

| Task | Command | Time Saved |
|------|---------|------------|
| Quick merge | `pdftk *.pdf cat output merged.pdf` | 5 minutes |
| Extract text | `pdftotext file.pdf - | head -50` | 2 minutes |
| Compress PDF | `gs -sDEVICE=pdfwrite -o out.pdf in.pdf` | 3 minutes |
| Extract images | `pdfimages -j file.pdf img` | 5 minutes |
| Split by page | `pdftk in.pdf burst output p_%d.pdf` | 2 minutes |

### Daily Automation Ideas

1. **Receipt Digitization** - Combine receipt images into monthly PDF
2. **Document Backup** - Auto-compress and archive important PDFs
3. **Invoice Management** - Extract text from invoices for record keeping
4. **Study Notes** - Merge lecture slides into single study document
5. **Report Generation** - Auto-generate PDF reports from data

---

## ⚡ QUICK REFERENCE CARD

### PDF Merge Commands

| Task | Command |
|------|---------|
| Merge two files | `pdftk a.pdf b.pdf cat output merged.pdf` |
| Merge all PDFs | `pdftk *.pdf cat output all.pdf` |
| Merge with qpdf | `qpdf --empty --pages *.pdf -- output.pdf` |
| Merge specific pages | `pdftk A=in.pdf cat A1-5 A10-15 output out.pdf` |

### PDF Split Commands

| Task | Command |
|------|---------|
| Split into pages | `pdftk input.pdf burst output page_%d.pdf` |
| Extract pages 5-10 | `pdftk in.pdf cat 5-10 output extract.pdf` |
| Extract first page | `pdftk in.pdf cat 1 output first.pdf` |
| Split with qpdf | `qpdf --split-pages in.pdf out_%d.pdf` |

### PDF Conversion Commands

| Task | Command |
|------|---------|
| PDF to text | `pdftotext input.pdf output.txt` |
| PDF to HTML | `pdftohtml input.pdf output.html` |
| PDF to images | `pdftoppm -png input.pdf output` |
| Images to PDF | `convert *.jpg output.pdf` |
| PDF to single image | `convert input.pdf output.png` |

### PDF Compression Commands

| Task | Command |
|------|---------|
| Screen quality | `gs -sDEVICE=pdfwrite -dPDFSETTINGS=/screen -o out.pdf in.pdf` |
| Ebook quality | `gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook -o out.pdf in.pdf` |
| Printer quality | `gs -sDEVICE=pdfwrite -dPDFSETTINGS=/printer -o out.pdf in.pdf` |
| pdftk compress | `pdftk in.pdf output out.pdf compress` |

### PDF Security Commands

| Task | Command |
|------|---------|
| Add password | `pdftk in.pdf output out.pdf user_pw PASSWORD` |
| Remove password | `pdftk in.pdf input_pw PASS output out.pdf` |
| qpdf encrypt 256 | `qpdf --encrypt user owner 256 -- in.pdf out.pdf` |
| qpdf decrypt | `qpdf --password=PASS --decrypt in.pdf out.pdf` |

---

## 🏆 BONUS: POWER USER TIPS

### Advanced PDF Operations

```bash
# Rotate specific pages
pdftk input.pdf cat 1 2right 3-end output rotated.pdf

# Remove duplicate pages
pdftk input.pdf cat 1-10 12-end output no_duplicates.pdf

# Add watermark
pdftk input.pdf stamp watermark.pdf output watermarked.pdf

# Extract all images from PDF
pdfimages -all input.pdf extracted_images/image

# Fix corrupted PDF
qpdf --input-file=input.pdf --output-file=fixed.pdf --normalize-content=y

# Linearize for web
qpdf --linearize input.pdf output.pdf

# Add metadata
pdftk input.pdf update_info <(echo -e "InfoKey: Title\nInfoValue: My Title") output new.pdf

# Compare two PDFs
diff <(pdftotext a.pdf -) <(pdftotext b.pdf -)
```

### Python PDF Scripting

```python
#!/usr/bin/env python3
# Advanced PDF manipulation with PyPDF2

import PyPDF2
import sys

def merge_pdfs(files, output):
    merger = PyPDF2.PdfMerger()
    for pdf in files:
        merger.append(pdf)
    merger.write(output)
    merger.close()

def split_pdf(input_file, output_prefix):
    reader = PyPDF2.PdfReader(input_file)
    for i, page in enumerate(reader.pages):
        writer = PyPDF2.PdfWriter()
        writer.add_page(page)
        with open(f"{output_prefix}_{i+1}.pdf", 'wb') as f:
            writer.write(f)

def add_watermark(input_file, watermark_file, output):
    reader = PyPDF2.PdfReader(input_file)
    watermark = PyPDF2.PdfReader(watermark_file)
    writer = PyPDF2.PdfWriter()
    
    for page in reader.pages:
        page.merge_page(watermark.pages[0])
        writer.add_page(page)
    
    with open(output, 'wb') as f:
        writer.write(f)

if __name__ == "__main__":
    # Usage examples
    pass
```

---

## 📝 CHAPTER SUMMARY: What You Learned

### Key Takeaways

- ✅ **PDF Tools Installation** - Install pdftk, qpdf, poppler, and ghostscript
- ✅ **PDF Merging** - Combine multiple PDFs with pdftk or qpdf
- ✅ **PDF Splitting** - Extract pages or split into individual files
- ✅ **Text Extraction** - Use pdftotext to extract text content
- ✅ **Image Conversion** - Convert PDFs to images and images to PDFs
- ✅ **PDF Compression** - Reduce file size with ghostscript
- ✅ **Password Protection** - Add and remove PDF encryption
- ✅ **PDF Rotation** - Rotate specific pages or entire documents
- ✅ **Python PyPDF2** - Programmatic PDF manipulation
- ✅ **Batch Processing** - Process multiple PDFs automatically

### Skills Acquired

| Skill | Level |
|-------|-------|
| PDF Merge/Split | ⭐⭐⭐⭐⭐ |
| Text Extraction | ⭐⭐⭐⭐ |
| PDF Compression | ⭐⭐⭐⭐ |
| Password Protection | ⭐⭐⭐ |
| Python PDF Scripting | ⭐⭐⭐ |

---

## 🔧 AUTOMATION SCRIPTS

### Ready-to-Use Scripts

**1. PDF Merger Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/merge-pdf.sh
OUTPUT="${1:-merged.pdf}"
shift
pdftk "$@" cat output "$OUTPUT"
echo "Created: $OUTPUT"
```

**2. PDF Compressor Script:**
```bash
#!/bin/bash
# Save as: ~/scripts/compress-pdf.sh
INPUT="$1"
OUTPUT="${1%.pdf}_compressed.pdf"
gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook -o "$OUTPUT" "$INPUT"
echo "Created: $OUTPUT"
```

**3. PDF to Text Batch:**
```bash
#!/bin/bash
# Save as: ~/scripts/pdf-to-text.sh
for pdf in *.pdf; do
    pdftotext "$pdf" "${pdf%.pdf}.txt"
    echo "Converted: $pdf"
done
```

### Cron Job Templates

```bash
# Add to crontab with: crontab -e

# Daily PDF compression
0 3 * * * find ~/storage/documents -name "*.pdf" -mtime -1 -exec compress-pdf.sh {} \;

# Weekly PDF organization
0 4 * * 0 /path/to/organize-pdfs.sh

# Monthly archive
0 5 1 * * find ~/storage/documents -name "*.pdf" -mtime +30 -exec mv {} ~/archives/ \;
```

---

## 🚀 WORKFLOW OPTIMIZATION

### Speed Up Daily Tasks

| Task | Slow Way | Fast Way |
|------|----------|----------|
| Merge PDFs | Open online tool → Upload → Download | `pdftk *.pdf cat output merged.pdf` |
| Extract text | Open PDF → Select → Copy | `pdftotext file.pdf -` |
| Compress PDF | Upload to compressor | `gs -sDEVICE=pdfwrite -o out.pdf in.pdf` |
| Split PDF | Use online splitter | `pdftk in.pdf burst` |
| Add password | Use PDF editor | `pdftk in.pdf output out.pdf user_pw PASS` |

### Efficiency Tips

1. **Use Aliases** - Add to `.bashrc`:
   ```bash
   alias pdfmerge='pdftk *.pdf cat output merged.pdf'
   alias pdfcompress='gs -sDEVICE=pdfwrite -dPDFSETTINGS=/ebook'
   alias pdftext='pdftotext'
   ```

2. **Use Functions** - Create universal extractor:
   ```bash
   extract-pdf() {
       pdftk "$1" burst output "${1%.pdf}_%02d.pdf"
   }
   ```

3. **Use Batch Processing** - Process multiple files with loops

4. **Use Ghostscript Presets** - `/screen`, `/ebook`, `/printer`

5. **Use qpdf for Optimization** - `--linearize` for web

---

## 📊 COMPARISON TABLES

### PDF Tool Comparison

| Feature | pdftk | qpdf | poppler | ghostscript |
|---------|-------|------|---------|-------------|
| Merge | ✅ | ✅ | ❌ | ✅ |
| Split | ✅ | ✅ | ❌ | ✅ |
| Compress | ✅ | ✅ | ❌ | ✅ Best |
| Encrypt | ✅ | ✅ | ❌ | ✅ |
| Text Extract | ❌ | ❌ | ✅ Best | ❌ |
| PDF to Image | ❌ | ❌ | ✅ | ✅ |
| Image to PDF | ❌ | ❌ | ❌ | ✅ |

### Compression Settings

| Setting | DPI | Size | Quality | Use Case |
|---------|-----|------|---------|----------|
| /screen | 72 | Smallest | Low | Web preview |
| /ebook | 150 | Medium | Good | E-books |
| /printer | 300 | Large | High | Printing |
| /prepress | 300 | Largest | Best | Professional |

### Encryption Levels

| Level | Bits | Security | Compatibility |
|-------|------|----------|---------------|
| RC4-40 | 40 | Weak | Old PDFs |
| RC4-128 | 128 | Medium | PDF 1.4+ |
| AES-128 | 128 | Good | PDF 1.5+ |
| AES-256 | 256 | Best | PDF 1.6+ |

---

## 🔗 RELATED CHAPTERS

| Chapter | Topic | Relationship |
|---------|-------|--------------|
| Ch39 | YouTube Downloaders | Download PDF tutorials |
| Ch40 | File Compression | Compress PDF files |
| Ch41 | Image/Media Tools | Convert images to PDF |
| Ch43 | Task Automation | Schedule PDF processing |
| Ch44 | Termux Widgets | Quick PDF tools widget |

---

## 🎮 INTERACTIVE QUIZ

### Test Your Knowledge (10 Questions)

**Q1:** Which command merges multiple PDFs?
- A) `pdfmerge a.pdf b.pdf output.pdf`
- B) `pdftk a.pdf b.pdf cat output merged.pdf`
- C) `join-pdf a.pdf b.pdf output.pdf`
- D) `cat a.pdf b.pdf > merged.pdf`

**Q2:** How do you extract text from PDF?
- A) `pdf-text input.pdf`
- B) `pdftotext input.pdf`
- C) `extract-text input.pdf`
- D) `cat input.pdf`

**Q3:** Which tool is best for PDF compression?
- A) pdftk
- B) qpdf
- C) ghostscript
- D) poppler

**Q4:** How do you add a password to PDF?
- A) `pdftk in.pdf output out.pdf password PASS`
- B) `pdftk in.pdf output out.pdf user_pw PASS`
- C) `pdftk in.pdf -pw PASS out.pdf`
- D) `encrypt-pdf in.pdf PASS out.pdf`

**Q5:** Which command extracts images from PDF?
- A) `pdfimages -j input.pdf output`
- B) `extract-images input.pdf`
- C) `pdftoimages input.pdf`
- D) `image-extract input.pdf output`

**Q6:** How do you split PDF into pages?
- A) `pdftk input.pdf split`
- B) `pdftk input.pdf burst`
- C) `pdftk input.pdf pages`
- D) `pdfsplit input.pdf`

**Q7:** Which qpdf command linearizes PDF?
- A) `qpdf --optimize input.pdf output.pdf`
- B) `qpdf --linearize input.pdf output.pdf`
- C) `qpdf --fast-web input.pdf output.pdf`
- D) `qpdf --web input.pdf output.pdf`

**Q8:** What does pdftotext -layout do?
- A) Creates layout file
- B) Preserves original formatting
- C) Changes output layout
- D) Adds page numbers

**Q9:** How do you convert images to PDF?
- A) `pdfcreate *.jpg output.pdf`
- B) `convert *.jpg output.pdf`
- C) `images-to-pdf *.jpg output.pdf`
- D) `pdftk *.jpg output.pdf`

**Q10:** Which compression setting gives smallest files?
- A) `/printer`
- B) `/ebook`
- C) `/screen`
- D) `/prepress`

**Answers:** 1-B, 2-B, 3-C, 4-B, 5-A, 6-B, 7-B, 8-B, 9-B, 10-C

---

## 🎯 AUTOMATION CHALLENGES

### Challenge 1: PDF Organization System
**Objective:** Create a script that organizes PDFs by date into year/month folders.
**Hint:** Use `pdfinfo` to get creation date.

### Challenge 2: Batch PDF Compressor
**Objective:** Create a script that compresses all PDFs over 5MB.
**Hint:** Check file size, use ghostscript with appropriate settings.

### Challenge 3: PDF Search Tool
**Objective:** Create a script that searches text content in all PDFs.
**Hint:** Use `pdftotext` with `grep`.

### Challenge 4: Invoice Processor
**Objective:** Create a script that extracts key data from invoice PDFs.
**Hint:** Use `pdftotext` with regex parsing.

### Challenge 5: PDF Report Generator
**Objective:** Create a script that generates PDF reports from data.
**Hint:** Use Python with reportlab or convert from HTML.

---

## 📝 SCRIPT WRITING EXERCISES

### Exercise A: PDF Merger Function
Create a function that merges all PDFs in current directory:
```bash
#!/bin/bash
# Your code here
```

### Exercise B: PDF Splitter Script
Create a script that splits PDF into specified page ranges:
```bash
#!/bin/bash
# Your code here
```

### Exercise C: PDF Text Search
Create a script that searches for text across multiple PDFs:
```bash
#!/bin/bash
# Your code here
```

---

**End of Chapter 42 Upgrade**
