📝 Write2Text
Handwritten Text to Printed Text Conversion using Machine Learning

Python FastAPI PyTorch

📋 Description
Write2Text converts images containing handwritten text into printed text. The system segments text into individual words and recognizes them using the TrOCR model.

🔄 How It Works
Image Upload → User uploads an image with handwritten text
Segmentation → System divides text into separate words and rows
Recognition → Each word is processed by the OCR model (TrOCR)
Result → Recognized text is returned in printed format
✨ Features
🖼️ Image processing with various formats support
✂️ Intelligent text segmentation into words
🤖 ML-based recognition using TrOCR
🌐 Web interface for easy usage
🚀 REST API for integration
💾 Local model storage for offline work
🚀 Quick Start
Installation
# Clone repository
git clone <repository-url>
cd write2text

# Create virtual environment
python -m venv venv
venv\Scripts\activate  # Windows
# source venv/bin/activate  # Linux/Mac

# Install dependencies
pip install -r requirements.txt

# Download OCR model
python download_model.py
Usage
# Start server
python main.py
Open frontend/index.html or navigate to http://localhost:8000

📁 Project Structure
write2text/
├── backend/          # FastAPI application
├── frontend/         # Web interface
├── ml/               # ML components
│   ├── preprocessing/  # Text segmentation
│   ├── ocr/          # OCR model
│   └── notebooks/    # Experiments
├── models/           # Saved ML models
├── main.py           # Entry point
└── download_model.py # Model download script
🛠️ Technologies
FastAPI — Web framework
PyTorch — Deep learning
Transformers — Pre-trained models
TrOCR — Text recognition
OpenCV — Image processing
📡 API
POST /segment
Upload image for processing.

curl -X POST "http://localhost:8000/segment" \
     -F "file=@image.png"
Response:

{
  "status": "success",
  "word_count": 42,
  "recognized_text": "Recognized text...",
  "word_frames": [...]
}
🔧 Configuration
Change OCR model in ml/ocr/model.py:

ocr_model = OCRModel(model_name)
Device is auto-detected: CUDA → MPS → CPU

🙏 Acknowledgments
TrOCR by Microsoft
raxtemur/trocr-base-ru for Russian language
