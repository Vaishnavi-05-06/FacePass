# 🔐 FaceGate

**A face-recognition access prototype that runs entirely in the browser.**
Enrol a person with a few photos, then scan a face to see whether access is granted.

![Status](https://img.shields.io/badge/status-prototype-orange)
![Single file](https://img.shields.io/badge/build-single%20HTML%20file-3DDC97)
![No dependencies](https://img.shields.io/badge/dependencies-none-blue)

> ⚠️ **Prototype only.** FaceGate matches faces using a simple pixel-based fingerprint, not a trained deep-learning model. It can be fooled by a printed photo and is **not suitable for securing anything real** yet. See [Roadmap](#roadmap).

---

## ✨ Features

- **Enrol people** with three camera captures or uploaded photos
- **Scan to unlock** with clear granted / denied feedback
- **Adjustable strictness** to balance false accepts against false rejects
- **Lockout** for 10 seconds after three failed scans
- **People management** with confirmed removal
- **Access log** showing time, name and match score
- **Mobile-first design** with a bottom tab bar and safe-area support
- **Works offline after loading** and keeps all data in memory

## 🚀 Quick start

FaceGate is one file with no build step, no server and no installs.

1. Download `facegate.html`.
2. Open it in a modern browser (Chrome, Edge, Safari or Firefox).
3. Allow camera access when asked, or use **Use a photo instead**.

> Camera access requires a secure context. Opening the file directly from disk usually works, but some browsers block it. If the camera does not start, use the photo upload option.

## 🧭 How to use

| Screen | What you can do |
|---|---|
| **Home** | See counts of people, granted and denied scans. Adjust strictness. |
| **Scan** | Look into the oval and tap **Scan face**, or upload a photo. |
| **Add** | Type a name, capture three photos, then **Save**. |
| **People** | View enrolled people and remove them. |
| **Log** | Review past scans and clear the log. |

## 🧠 How it works

1. Each captured face is cropped to its central region and shrunk to a 32 × 32 greyscale image.
2. The pixel values are normalised so brightness and contrast differences matter less.
3. A scan is compared with every saved sample using cosine similarity.
4. If the best score meets the strictness threshold, access is granted.

Everything runs locally in the browser. No images are uploaded anywhere.

## 🛠️ Tech

- Plain HTML, CSS and JavaScript
- Canvas API for image processing
- `getUserMedia` for the camera
- No frameworks, libraries or external requests

## ⚠️ Limitations

- Easily fooled by a photograph or screen showing a face
- Sensitive to lighting, angle, glasses and camera quality
- Data is not saved, so enrolments reset when the page closes
- Not audited for security or privacy compliance

## 🗺️ Roadmap

- [ ] Replace the pixel fingerprint with a trained face-embedding model (TensorFlow.js or OpenCV.js)
- [ ] Add liveness detection (blink or head-turn check) to block photo spoofing
- [ ] Save enrolments securely, protected by a PIN-based admin area
- [ ] Export the access log to CSV

## 🤝 Contributing

Suggestions and issues are welcome. Please open an issue before starting large changes.

## 📄 License

Choose a license before publishing, for example [MIT](https://choosealicense.com/licenses/mit/).
