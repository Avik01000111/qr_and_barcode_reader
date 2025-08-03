Here is a detailed and well-structured `README.md` for your **QR & Barcode Authorization System using OpenCV and Pyzbar** project:

---

# 📦 QR & Barcode Scanner with Access Control

This real-time Python project uses **OpenCV** and **pyzbar** to scan **QR codes** and **barcodes** from a webcam feed. It compares the decoded data against a predefined list of authorized entries and displays either an **"Authorized"** or **"Un-Authorized"** message on screen.

---

## 🔍 Features

* Real-time QR/Barcode detection using your webcam.
* Verifies the scanned data against a local **whitelist file** (`myDataFile.text`).
* Draws colored boxes around scanned codes:

  * ✅ Green for Authorized
  * ❌ Red for Un-Authorized
* Displays status label beside each detected code.

---

## 📦 Requirements

Install the necessary Python libraries:

```bash
pip install opencv-python pyzbar numpy
```

> Also install `zbar` for `pyzbar` to work:

* **Windows**: Install using a prebuilt `.whl` or follow `pyzbar` documentation.
* **Linux**: `sudo apt-get install libzbar0`

---

## 📁 Project Structure

```
📂 your_project_folder/
├── 📄 qr_scanner.py              # Main script
├── 📄 myDataFile.text            # Whitelisted authorized entries
└── 📷 (Optional sample images)
```

**Example of `myDataFile.text`:**

```
1234567890
https://example.com
authorized_user_id
```

---

## ▶️ How It Works

1. Initializes webcam (`cv2.VideoCapture(0)`).
2. Continuously scans each frame using `pyzbar.decode()`.
3. Decodes any detected QR/Barcodes.
4. Compares decoded data with entries in `myDataFile.text`.
5. Draws a polygon and displays either:

   * ✅ `Authorized` in green if matched.
   * ❌ `Un-Authorized` in red if not.

---

## 🖥️ How to Run

1. Ensure your webcam is connected.
2. Add your authorized entries into `myDataFile.text`.
3. Run the script:

```bash
python qr_scanner.py
```

4. Point a QR code or barcode toward the webcam.
5. Press `Ctrl + C` or close the window to stop.

---

## 🧠 Code Highlights

```python
myDataList = f.read().splitlines()
...
for barcode in decode(img):
    myData = barcode.data.decode('utf-8')
    if myData in myDataList:
        myOutput = 'Authorized'
        myColor = (0,255,0)
    else:
        myOutput = 'Un-Authorized'
        myColor = (0, 0, 255)
```

---

## 📷 Sample Output

| Input 📸                   | Output Display 🖼️        |
| -------------------------- | ------------------------- |
| QR Code: `https://abc.com` | ✅ Green box + Authorized  |
| QR Code: `unknown`         | ❌ Red box + Un-Authorized |

---

## 🔐 Use Cases

* Attendance systems
* Event access control
* Package or inventory verification
* Any use case involving QR/barcode verification

---

## 📌 Customization Ideas

* Save scanned codes to a log file.
* Add timestamps or user IDs.
* Add audio feedback (e.g., beep on success/failure).
* Send data to a remote server or database.

---

## 📝 License

This project is open-source and available under the MIT License.

---

Let me know if you’d like to extend it with sound alerts, GUI interface, or logging features!
