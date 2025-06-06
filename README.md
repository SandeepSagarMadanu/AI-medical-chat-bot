https://github.com/user-attachments/assets/c09d695a-6802-4fb6-8d66-5778cc09e44d


# 🧠 Multimodal Image Query System with GROQ LLM API

This project is an AI-powered web and script-based system that allows users to upload an image and ask questions about its contents. It uses Meta's LLaMA models hosted on the [GROQ](https://groq.com/) API, capable of processing both **textual and visual** information.

## 🚀 Features

- Upload and query images directly via a FastAPI-powered web interface.
- Supports image-to-text multimodal queries using LLaMA models.
- Secure `.env` key management with `python-dotenv`.
- Logs and handles API responses, including fallbacks.
- CLI utility for local testing and automation.
- Displays side-by-side model responses from:
  - `meta-llama/llama-4-scout-17b-16e-instruct`
  - `meta-llama/llama-prompt-guard-2-22m`


## 📂 Project Structure

```
.
├── app.py              # FastAPI backend for web interaction
├── main(1).py          # CLI-based tester for image+text queries
├── .env                # Stores GROQ_API_KEY (DO NOT share publicly)
├── templates/
│   └── index.html      # Jinja2 HTML template for upload UI (assumed)
├── static/             # For CSS or image assets if used
├── test1.png / test2.jpg / test3.png  # Demo images
└── temp.md             # Sample output log
```

## 🛠️ Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/multimodal-image-query
cd multimodal-image-query
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
# or manually:
pip install fastapi uvicorn python-dotenv pillow requests jinja2
```

### 3. Setup the `.env` file

```ini
# .env
GROQ_API_KEY=your_groq_api_key_here
```

## 🌐 Run the Web App

```bash
uvicorn app:app --reload
```

- Visit: `http://127.0.0.1:8000`
- Upload an image and enter a query like: `What does this image represent?`

## 🧪 Run the CLI Script

```bash
python main(1).py
```

- Make sure to update the image path and query inside the script:
```python
image_path = "test1.png"
query = "What are the encoders in this picture?"
```

## 📊 Sample Response (from `temp.md`)

```json
{
  "llama11b": "The encoders in the provided image are comprised of: Multi-Head Attention, Add & Norm, Feed Forward...",
  "llama90b": "Error from llama90b API: 400 - max_tokens must be <= 512"
}
```

## 📌 Notes

- LLaMA-90b model currently **only supports text** input and returns an error for image queries.
- Make sure to keep your `.env` file private and **never commit it** to public repositories.

## 📈 Future Improvements

- Add support for drag-and-drop uploads with progress bars.
- Display model confidence or ranking.
- Integrate with other multimodal APIs like OpenAI GPT-4V or Google Gemini.
- Extend to PDF/image documents with OCR for text + diagram QA.

## 🙌 Acknowledgments

- [GROQ API](https://groq.com/)
- Meta’s LLaMA LLMs
- FastAPI and PIL community
