# Chapter 42: PDF Tools in Termux

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
