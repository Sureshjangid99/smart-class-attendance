# Smart Class Attendance System

> Automated face recognition-based attendance system for classrooms — built with Python, OpenCV, and Streamlit.

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-5C3EE8?style=flat&logo=opencv&logoColor=white)
![face_recognition](https://img.shields.io/badge/face__recognition-1.3.0-00A86B?style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)

---

## What it does

Smart Class Attendance replaces manual roll calls with a camera-based face recognition system. A teacher opens the app, points the webcam at the class (or uploads a photo), and attendance is marked automatically — with a downloadable report generated instantly.

- Mark attendance via **live webcam** or **photo upload**
- Recognize multiple students in a single frame simultaneously
- Generate **Excel and PDF reports** per class, per date
- Manage student profiles with face enrollment
- View **attendance history and analytics** from a dashboard

---

## Demo

> _Screenshots below show the live webcam attendance flow and report export_

| Webcam Attendance | Student Dashboard | Report Export |
|---|---|---|
| ![webcam](#) | ![dashboard](#) | ![report](#) |

> **Note:** Replace placeholder images above with actual screenshots. Recommended: record a short screen capture GIF using [ScreenToGif](https://www.screentogif.com/) (Windows) or [Kap](https://getkap.co/) (Mac) and embed it here.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend / UI | Streamlit |
| Face Detection | OpenCV (Haar Cascade) |
| Face Recognition | `face_recognition` (dlib-based) |
| Data Storage | CSV / SQLite |
| Report Export | pandas + openpyxl |
| Language | Python 3.8+ |

---

## Project Structure

```
smart-class-attendance/
├── app.py                  # Main Streamlit application entry point
├── requirements.txt        # Python dependencies
├── packages.txt            # System-level dependencies (for cloud deploy)
├── src/
│   ├── face_utils.py       # Face detection and recognition logic
│   ├── attendance.py       # Attendance marking and storage
│   ├── report.py           # Report generation (Excel/PDF)
│   └── dashboard.py        # Analytics and history views
├── data/
│   ├── students/           # Enrolled student face images
│   └── attendance/         # Attendance records (CSV)
├── assets/
│   └── demo.gif            # Demo GIF for README
└── .gitignore
```

---

## Getting Started

### Prerequisites

Make sure you have the following installed on your system before proceeding:

- Python 3.8 or higher
- `cmake` (required by dlib)
- A working webcam (for live attendance mode)

**Install cmake:**

```bash
# Ubuntu / Debian
sudo apt-get install cmake build-essential libopenblas-dev liblapack-dev

# macOS
brew install cmake

# Windows
# Download from https://cmake.org/download/ and add to PATH
```

### Installation

**Step 1 — Clone the repository**

```bash
git clone https://github.com/Sureshjangid99/smart-class-attendance.git
cd smart-class-attendance
```

**Step 2 — Create a virtual environment (recommended)**

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

**Step 3 — Install dependencies**

```bash
pip install -r requirements.txt
```

> ⚠️ `dlib` can take 5–10 minutes to compile. This is normal. Do not cancel.

**Step 4 — Run the app**

```bash
streamlit run app.py
```

The app will open automatically at `http://localhost:8501`

---

## Usage

### 1. Enroll students

Go to the **"Add Student"** section → Enter the student's name and roll number → Upload 3–5 clear photos of their face (different angles, lighting) → Click **Enroll**.

### 2. Mark attendance

Go to **"Take Attendance"** → Select the class and subject → Either:
- Click **"Open Webcam"** to use live camera (recommended)
- Click **"Upload Photo"** to use a classroom photo

The system will recognize faces and mark attendance automatically. Unrecognized faces are flagged for manual review.

### 3. Export reports

Go to **"Reports"** → Select date range and class → Export as Excel or PDF.

---

## Common Issues & Fixes

| Problem | Fix |
|---|---|
| `dlib` installation fails | Make sure `cmake` is installed and in PATH before running `pip install` |
| Webcam not detected | Check browser permissions — allow camera access for localhost |
| Face not recognized | Enroll more photos (5+) with varied lighting and angles |
| Slow recognition | Reduce webcam resolution in settings, or use photo upload mode |
| `ModuleNotFoundError: face_recognition` | Run `pip install face_recognition` separately after cmake |

---

## Limitations (known)

- Recognition accuracy decreases in poor lighting conditions
- Students who look very similar (twins, siblings) may cause errors — use manual correction
- First load after inactivity may be slow on cloud deployments
- Currently supports JPEG/PNG image formats only

---

## Future Roadmap

- [ ] WhatsApp/SMS alerts to parents when student is absent
- [ ] Multi-school support with isolated data per institution
- [ ] Admin dashboard with monthly attendance analytics
- [ ] Mobile-responsive UI for teacher tablets
- [ ] Integration with Google Sheets for automatic syncing
- [ ] Supabase cloud database for persistent storage

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m "Add: your feature description"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## Author

**Suresh Jangid**
- GitHub: [@Sureshjangid99](https://github.com/Sureshjangid99)
- Project built as part of Computer Vision coursework

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- [face_recognition](https://github.com/ageitgey/face_recognition) by Adam Geitgey
- [Streamlit](https://streamlit.io/) for the web framework
- [OpenCV](https://opencv.org/) for image processing
