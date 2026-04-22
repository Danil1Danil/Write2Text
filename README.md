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

US (User Story)
Как пользователь, я хочу загрузить фотографию рукописного русского текста через сайт, чтобы получить распознанный и грамматически/смыслово связанный печатный текст, обработанный ИИ.

UC (Use Case)
Пользователь открывает сайт.
Нажимает кнопку загрузки файла и выбирает изображение с русским рукописным текстом.
Система отправляет изображение на сервер.
ИИ распознаёт символы (OCR) и преобразует их в печатный текст.
Обученная модель связывает слова (исправляет ошибки распознавания, восстанавливает связность предложений).
Система возвращает итоговый печатный текст на экран.
Пользователь копирует или скачивает результат.

ПИМ аналитика (Product Impact Metrics)
Точность распознавания символов (Accuracy, % правильных символов)
Коэффициент связности текста (пользовательская оценка 1–5, среднее)
Время обработки одной фотографии (секунды, p95)
Конверсия загрузка → успешный результат (%, количество обработанных фото без ошибок)
Повторные использования на одного пользователя (stickiness)

Проблема
Школьники и студенты вынуждены работать с бумажными конспектами там, где гаджеты запрещены (уроки, лекции). Перенос записей в цифру вручную — долго, скучно, убивает продуктивность. Готовые OCR-решения есть, но они тупо распознают символы, теряя смысл и связность текста.

Решение
Сервис, который за секунды превращает фото рукописного русского текста в печатный, анализируемый и связываемый ИИ. Не просто OCR, а умная доработка: модель сопоставляет текущий текст с ранее распознанным контекстом, исправляя ошибки и восстанавливая логику записей.

Целевая аудитория (ЦА)
Школьники и студенты 13–25 лет
Те, кто много пишет от руки и хочет быстро оцифровать конспекты
Учится на дистанте или гибриде, активно пользуется учебными платформами

Каналы продвижения
Сайты для решения задач (e.g. «Решу ЕГЭ», «Фоксфорд», «Сдам ГИА»)
Учебные платформы и онлайн-школы (баннеры, интеграции)
Студенческие форумы и паблики ВК (где сидит ЦА)

Монетизация
Ограниченное число бесплатных сканирований в день / месяц
Платные опции: снятие лимитов, сканирование текстов на других языках
Возможна подписка для активных студентов (безлимит)

Конкурентное преимущество (уникальность)
Ни один конкурент (мобильные приложения или сайты-OCR) не использует дообученную ИИ-модель, которая связывает текущий распознанный текст с историей предыдущих анализов. Это даёт не просто символы, а осмысленный, скорректированный и связанный результат — как если бы текст перепечатал человек, а не робот.
