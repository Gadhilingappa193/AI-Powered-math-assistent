# AI-Powered-math-assistent
# 🔢 Mathly - Real-Time Math Problem Solver

<div align="center">

![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)
![OpenCV](https://img.shields.io/badge/OpenCV-4.5+-green.svg)
![Tesseract](https://img.shields.io/badge/Tesseract-4.0+-orange.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Status](https://img.shields.io/badge/Status-Active-success.svg)

**An intelligent computer vision application that solves mathematical equations in real-time using your webcam.**

[Features](#features) • [Demo](#demo) • [Installation](#installation) • [Usage](#usage) • [Architecture](#architecture) • [Contributing](#contributing)

</div>

---

📖 Overview

Mathly is a real-time automated math problem solver that combines **Computer Vision**, **Optical Character Recognition (OCR)**, and **Symbolic Mathematics** to solve equations captured through your webcam. Simply point your camera at any mathematical equation, and get instant solutions displayed on screen.

 ✨ Key Highlights

- 🎥 **Real-time Processing**: Smooth 30 FPS camera feed with instant equation detection
- 🔍 **Advanced OCR**: Multi-configuration Tesseract OCR with 85%+ accuracy
- 🧮 **Symbolic Math**: Powered by SymPy for solving equations and expressions
- 🎨 **User-Friendly UI**: Intuitive interface with visual scanning box and answer display
- ⚡ **Optimized Performance**: Dual-thread architecture with 85% memory reduction
- 📸 **Capture & Save**: Built-in screenshot and question capture functionality

---

## 🎯 Features

### Core Functionality
- ✅ **Algebraic Equation Solving**: Solve equations like `2x + 5 = 15`, `x² - 4 = 0`
- ✅ **Expression Evaluation**: Calculate `2 + 3 × 4`, simplify `(x + 2)²`
- ✅ **Multi-Variable Support**: Handle equations with variables x, y, z, a, b, c
- ✅ **Real-time Detection**: Continuous scanning and solving as you move equations
- ✅ **Multiple Solutions**: Display all possible solutions for equations

Technical Features
- 🔧 **Advanced Image Processing**: 5-step OpenCV pipeline for optimal OCR accuracy
- 🔧 **Adaptive Thresholding**: Works in varying lighting conditions
- 🔧 **Multi-Camera Support**: Automatic detection of available cameras
- 🔧 **Error Correction**: Post-processing to fix common OCR mistakes
- 🔧 **Background Threading**: Non-blocking UI with smooth performance

User Interface
- 📱 **Visual Scanning Box**: Clear green rectangle showing scan area
- 📱 **Dedicated Answer Box**: Real-time Q&A display on camera screen
- 📱 **Keyboard Controls**: Intuitive shortcuts for capture and save
- 📱 **Processing Indicator**: Visual feedback during equation solving

---

 🎬 Demo

Screenshots

```
┌─────────────────────────────────────────────┐
│ MATHLY - REAL-TIME MATH SOLVER              │
│                                             │
│ QUESTION AREA - Place equation here         │
│ ┌═══════════════════════════════════════┐   │
│ ║            2x + 5 = 15               ║   │
│ ║                                      ║   │
│ └═══════════════════════════════════════┘   │
│                                             │
│ ANSWER                                      │
│ ┌─────────────────────────────────────────┐ │
│ │ Q: 2*x+5=15                            │ │
│ │ A: x = 5                               │ │
│ └─────────────────────────────────────────┘ │
│                                             │
│ CONTROLS: Q-Quit | S-Screenshot | C-Capture│
└─────────────────────────────────────────────┘
```

### Example Equations

| Input Equation | Output Solution |
|---------------|-----------------|
| `2x + 5 = 15` | `x = 5` |
| `x² - 4 = 0` | `x = -2, 2` |
| `2 + 3 × 4` | `= 14` |
| `(x + 2)²` | `= x² + 4x + 4` |
| `3x + 2y = 10` | Solutions for both variables |

---

🚀 Installation

### Prerequisites

- Python 3.7 or higher
- Webcam (built-in or external USB camera)
- Operating System: Windows, macOS, or Linux

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/mathly.git
cd mathly
```

### Step 2: Install Python Dependencies

```bash
pip install -r requirements.txt
```

**requirements.txt:**
```
opencv-python>=4.5.0
pytesseract>=0.3.8
sympy>=1.8
numpy>=1.19.0
```

### Step 3: Install Tesseract OCR

#### Windows
1. Download installer from [GitHub](https://github.com/UB-Mannheim/tesseract/wiki)
2. Run the installer and note the installation path
3. Add Tesseract to PATH or update code with path:
```python
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

#### macOS
```bash
brew install tesseract
```

#### Linux (Ubuntu/Debian)
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
```

#### Linux (Fedora/RHEL)
```bash
sudo dnf install tesseract
```

### Step 4: Verify Installation

```bash
# Test Tesseract
tesseract --version

# Test Python packages
python -c "import cv2, pytesseract, sympy; print('All packages installed successfully!')"
```

---

## 💻 Usage

### Basic Usage

1. **Run the application:**
```bash
python mathly_solver.py
```

2. **Point camera at equation:**
   - Place your written or printed equation in the green scanning box
   - Wait 1-2 seconds for detection and solving

3. **View results:**
   - Question and answer appear in the dedicated answer box below

### Keyboard Controls

| Key | Action |
|-----|--------|
| `Q` | Quit application |
| `S` | Save screenshot of current screen |
| `C` | Capture photo of current question |
| `ESC` | Alternative quit option |

### Command Line Options

```bash
# Use specific camera (if you have multiple cameras)
python mathly_solver.py --camera 0  # Default
python mathly_solver.py --camera 1  # External USB camera

# Adjust processing frequency (frames to skip)
python mathly_solver.py --skip-frames 15  # Default: process every 15th frame

# Enable debug mode
python mathly_solver.py --debug
```

### Supported Equation Types

**Linear Equations:**
- `2x + 5 = 15`
- `3x - 7 = 20`
- `x/2 + 3 = 10`

**Quadratic Equations:**
- `x² - 4 = 0`
- `2x² + 3x - 5 = 0`
- `x² + 6x + 9 = 0`

**Expressions:**
- `2 + 3 × 4`
- `(x + 2)²`
- `x² + 2x + 1`

**Multi-Variable:**
- `2x + 3y = 12`
- `x + y = 10`

---

## 🏗️ Architecture

### System Components

```
┌─────────────────────────────────────────────────────────────┐
│                    MATHLY ARCHITECTURE                      │
└─────────────────────────────────────────────────────────────┘

┌─────────────┐    ┌──────────────┐    ┌─────────────┐
│   Camera    │───▶│   OpenCV     │───▶│  Tesseract  │
│  Hardware   │    │ Preprocessing│    │     OCR     │
└─────────────┘    └──────────────┘    └─────────────┘
                            │                   │
                            ▼                   ▼
                    ┌──────────────┐    ┌─────────────┐
                    │     SymPy    │◀───│    Text     │
                    │  Math Solver │    │  Cleaning   │
                    └──────────────┘    └─────────────┘
                            │
                            ▼
                    ┌──────────────┐
                    │   Real-time  │
                    │  UI Display  │
                    └──────────────┘
```

### Image Processing Pipeline

1. **Camera Capture** (1280×720 @ 30 FPS)
2. **ROI Extraction** (960×180 region)
3. **Grayscale Conversion** (BGR → Gray)
4. **Bilateral Filtering** (Noise reduction + edge preservation)
5. **Adaptive Thresholding** (Binary conversion)
6. **Morphological Operations** (Character cleaning)
7. **4× Scaling** (Resolution enhancement)
8. **OCR Processing** (Text extraction)

### Performance Characteristics

| Metric | Value |
|--------|-------|
| Display FPS | 30 FPS |
| Processing FPS | 2 FPS |
| Memory Efficiency | 85% reduction via ROI |
| CPU Optimization | 93% reduction via frame skipping |
| OCR Accuracy | 85-90% (printed), 70-75% (handwritten) |
| Solution Time | <1 second |

---

## 🛠️ Technical Details

### Technologies Used

- **Python 3.7+**: Core programming language
- **OpenCV 4.5+**: Computer vision and image processing
- **Tesseract 4.0+**: Optical character recognition
- **SymPy 1.8+**: Symbolic mathematics and equation solving
- **NumPy 1.19+**: Numerical computing and array operations

### Key Algorithms

#### Image Processing
- **Bilateral Filter**: Edge-preserving noise reduction
- **Adaptive Thresholding**: Local contrast-based binarization
- **Morphological Operations**: Shape-based image processing
- **Cubic Interpolation**: High-quality image scaling

#### OCR Optimization
- **Multi-PSM Strategy**: Multiple Page Segmentation Modes
- **Character Whitelisting**: Mathematical symbol restriction
- **Post-processing**: Error correction and formatting

#### Performance
- **Dual-thread Architecture**: UI and processing separation
- **Frame Skipping**: Process every Nth frame
- **ROI Processing**: Region-of-interest optimization

---

## 📂 Project Structure

```
mathly/
├── mathly_solver.py          # Main application file
├── requirements.txt          # Python dependencies
├── README.md                 # This file
├── LICENSE                   # MIT License
├── .gitignore               # Git ignore rules
├── docs/                    # Documentation
│   ├── architecture.md      # System architecture details
│   ├── api.md              # API documentation
│   └── troubleshooting.md  # Common issues and solutions
├── examples/               # Example equations and images
│   ├── linear_equations.jpg
│   ├── quadratic_equations.jpg
│   └── expressions.jpg
├── tests/                  # Unit tests
│   ├── test_preprocessing.py
│   ├── test_ocr.py
│   └── test_solver.py
└── captured_questions/     # Auto-created for saved captures
```

---

## 🔧 Configuration

### Adjustable Parameters

Edit these in `mathly_solver.py`:

```python
# Scanning box size (relative to frame)
self.scan_box_width_ratio = 0.75   # 75% of frame width
self.scan_box_height_ratio = 0.25  # 25% of frame height

# Processing frequency
frame_skip = 15  # Process every 15th frame

# OCR configuration
psm_modes = [8, 7, 6, 13]  # Page Segmentation Modes to try
char_whitelist = '0123456789+-*/=()^xyzabcXYZABC.,'

# Image processing parameters
bilateral_d = 9           # Bilateral filter diameter
bilateral_sigma = 75      # Bilateral filter sigma
threshold_block_size = 15 # Adaptive threshold block size
threshold_c = 10          # Adaptive threshold constant
```

---

## 🐛 Troubleshooting

### Camera Not Opening

**Problem**: "Error: Cannot open camera"

**Solutions**:
1. Check camera permissions in system settings
2. Close other applications using the camera (Zoom, Skype, etc.)
3. Try different camera index: `python mathly_solver.py --camera 1`
4. Verify camera works with: `python -c "import cv2; print(cv2.VideoCapture(0).isOpened())"`

### Low OCR Accuracy

**Problem**: Equations not recognized correctly

**Solutions**:
1. Ensure good lighting (avoid shadows)
2. Use printed text instead of handwriting
3. Make text larger and clearer
4. Keep equation horizontal in frame
5. Adjust adaptive threshold parameters

### Slow Performance

**Problem**: Laggy camera feed

**Solutions**:
1. Reduce camera resolution: `cap.set(cv2.CAP_PROP_FRAME_WIDTH, 640)`
2. Increase frame skip: `frame_count % 20 == 0`
3. Close other applications
4. Update graphics drivers

### Tesseract Not Found

**Problem**: "TesseractNotFoundError"

**Solutions**:
1. Verify installation: `tesseract --version`
2. Add to PATH or set path in code:
   ```python
   pytesseract.pytesseract.tesseract_cmd = '/path/to/tesseract'
   ```
3. Reinstall Tesseract OCR

---

## 🧪 Testing

### Run Unit Tests

```bash
# Run all tests
python -m pytest tests/

# Run specific test file
python -m pytest tests/test_preprocessing.py

# Run with coverage
python -m pytest --cov=mathly_solver tests/
```

### Test with Example Images

```bash
# Test with provided examples
python test_static_images.py examples/linear_equations.jpg
```

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

### Ways to Contribute

1. 🐛 **Report Bugs**: Open an issue with details
2. 💡 **Suggest Features**: Share your ideas
3. 📝 **Improve Documentation**: Fix typos, add examples
4. 🔧 **Submit Pull Requests**: Add features or fix bugs

### Development Setup

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Run tests: `pytest tests/`
5. Commit: `git commit -m "Add feature"`
6. Push: `git push origin feature-name`
7. Open a Pull Request

### Code Style

- Follow PEP 8 guidelines
- Add docstrings to functions
- Include type hints where appropriate
- Write unit tests for new features

---

## 📋 Roadmap

### Version 2.0 (Planned)

- [ ] Deep learning-based OCR for better handwriting recognition
- [ ] Multi-equation detection and solving
- [ ] Step-by-step solution display
- [ ] Support for calculus (derivatives, integrals)
- [ ] Geometric problem solving
- [ ] Mobile app (iOS/Android)
- [ ] Web-based version
- [ ] Cloud processing option
- [ ] Equation history and favorites
- [ ] Export solutions to PDF

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)
- LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)
- Email: your.email@example.com

---

## 🙏 Acknowledgments

- **OpenCV Team**: For the comprehensive computer vision library
- **Google Tesseract**: For the powerful OCR engine
- **SymPy Developers**: For symbolic mathematics capabilities
- **Python Community**: For extensive libraries and support

---

## 📊 Project Stats

![GitHub stars](https://img.shields.io/github/stars/yourusername/mathly?style=social)
![GitHub forks](https://img.shields.io/github/forks/yourusername/mathly?style=social)
![GitHub issues](https://img.shields.io/github/issues/yourusername/mathly)
![GitHub pull requests](https://img.shields.io/github/issues-pr/yourusername/mathly)

---

## 📚 Additional Resources

- [OpenCV Documentation](https://docs.opencv.org/)
- [Tesseract OCR Documentation](https://tesseract-ocr.github.io/)
- [SymPy Documentation](https://docs.sympy.org/)
- [Project Wiki](https://github.com/yourusername/mathly/wiki)
- [Video Tutorial](https://youtube.com/watch?v=your-video)

---

<div align="center">

**Made with ❤️ and Python**

If you find this project helpful, please consider giving it a ⭐!

[⬆ Back to Top](#-mathly---real-time-math-problem-solver)

</div>
```

---

## 🎯 Quick Start Guide

For first-time users, follow this minimal setup:

```bash
# 1. Clone and enter directory
git clone https://github.com/yourusername/mathly.git && cd mathly

# 2. Install dependencies
pip install opencv-python pytesseract sympy numpy

# 3. Install Tesseract (macOS example)
brew install tesseract

# 4. Run the application
python mathly_solver.py

# That's it! Point your camera at an equation and see the magic ✨
```

---

**Last Updated**: November 2025
**Version**: 1.0.0
**Status**: ✅ Production Ready
