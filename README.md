# 📜 Intelligent Document Validation – OCR Demo

This project simulates a lightweight **Intelligent Document Processing (IDP)** pipeline using Python and Tesseract OCR. The goal is to **extract and validate key fields** (e.g., name, address, date, signature, and beneficiary) from scanned insurance application forms.

---

## 📌 Sample Document

<img src="https://github.com/sprouse9/OCR/blob/main/LIfeApplication20230405-5593.png" width="400" height="600">

---

## 🧠 Project Goals

* Use OCR to extract structured information from an unstructured scanned image
* Validate presence of required fields:

  * Full Name
  * Address
  * Date of Birth
  * Primary Beneficiary
  * Signature (presence only)
* Preprocess the image to improve OCR accuracy
* Demonstrate typical challenges in document automation workflows

---

## 📅 Initial OCR Output (Before Preprocessing)

```
Extracted Text:
 LIFE INSURANCE
APPLICATION

INSURED’S INFORMATION

Full Name: John Doe
Address: _!234 Elm St.

Springfield , IL 62701
Date of Birth: June 8, 1983

BENEFICIARY DESIGNATION

Primary Beneficiary: Jane Doe

Signature: Gabe Dee
Date: 06/08/2023

Date Found: June 8, 1983
Signature Mentioned
Signature Contents: Gabe Dee
Signature Field Filled
Primary Beneficiary: Jane Doe
```

---

## 🔧 OCR Output After Preprocessing

Image preprocessing (grayscale + thresholding) improved field recognition.

```
LIFE INSURANCE
APPLICATION

INSURED’S INFORMATION

FullName: John Doe
Address: 1234 Elm St.

Springfield , IL 62701
Date of Birth: June 8, 1983

BENEFICIARY DESIGNATION

Primary Beneficiary: Jane Doe

Signature: Gabe Dee
Date: 06/08/2023
```

**Improvements:**

* ✅ Address field correctly scanned
* ✅ Less whitespace and noise
* ⚠️ Signature name still misread as "Gabe Dee"

---

## ✍️ Signature Detection Notes

As we can see, the **signature field is filled**, but the OCR **does not recognize the correct name**.

This hits a real-world IDP pain point:

Even if a signature is present, OCR often misreads handwritten names like "Gabe Dee" or "John Smith" due to:

* Inconsistent handwriting
* Stylized script fonts
* Noise, blur, or compression artifacts

---

## 🧰 Recommended Approach

For real-world IDP systems and this project:

* ✅ **Confirm presence** of a signature field
* ❌ **Do not attempt name matching** (unreliable via OCR)

---

## 🛠️ Tools Used

* Python 3.x
* Tesseract OCR (`pytesseract`)
* OpenCV (for preprocessing)
* PIL / Matplotlib (for image display)
* Regex (for field detection)

---

## 🚀 Future Improvements

* Use bounding box detection for visual validation
* Apply NLP to categorize document type (e.g., "insurance application")
* Add confidence scores per field


