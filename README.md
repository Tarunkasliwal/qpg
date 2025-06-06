# Ollama Question Paper Generator

An AI-powered Flask application that automatically generates academic question papers from syllabus PDFs using Large Language Models (LLaMA via Ollama).

## 🚀 Features

- **PDF Syllabus Processing**: Upload and extract text from academic syllabus PDFs
- **AI-Powered Question Generation**: Uses LLaMA 3.2-vision model via Ollama to generate contextual questions
- **Structured Output**: Generates questions with Course Outcomes (CO) and Bloom's Taxonomy (BT) levels
- **Multiple Paper Variants**: Creates multiple unique question papers for exam security
- **Professional PDF Export**: Generates publication-ready question papers with proper formatting
- **Question Banking**: Stores generated questions in SQLite database for reuse
- **Web Interface**: User-friendly interface for upload, generation, and download

## 📋 Prerequisites

- Python 3.8+
- Ollama installed and running locally
- LLaMA 3.2-vision model downloaded in Ollama

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Tarunkasliwal/qpg
   cd qpg
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install and setup Ollama**
   ```bash
   # Install Ollama (visit https://ollama.ai for installation guide)
   ollama pull llama3.2-vision
   ```

5. **Start Ollama server**
   ```bash
   ollama serve
   ```

## 📦 Dependencies

```
Flask==2.3.3
Flask-CORS==4.0.0
requests==2.31.0
PyPDF2==3.0.1
reportlab==4.0.4
Werkzeug==2.3.7
```

## 🚀 Usage

1. **Start the application**
   ```bash
   python app.py
   ```

2. **Access the web interface**
   Open your browser and navigate to `http://localhost:5000`

3. **Generate Questions**
   - Upload a PDF syllabus file
   - Click "Generate Questions" to process and create questions
   - Wait for the AI to generate questions for each unit

4. **Generate Question Papers**
   - Click "Generate Papers" to create multiple paper variants
   - Download the generated PDF question papers

## 📁 Project Structure

```
ollama-question-paper-generator/
│
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── README.md             # Project documentation
├── app.log               # Application logs
│
├── templates/            # HTML templates
│   └── index.html        # Web interface
│
├── uploads/              # Uploaded files and generated PDFs
│   ├── syllabus_files/   # Uploaded syllabus PDFs
│   └── question_papers/  # Generated question papers
│
├── data/                 # Database storage
│   └── questions.db      # SQLite database
│
└── static/               # CSS, JS, and other static files
    ├── css/
    ├── js/
    └── images/
```

## ⚙️ Configuration

### System Prompt Customization

The AI prompt can be customized in the `SYSTEM_PROMPT` variable to modify:
- Question format requirements
- Bloom's Taxonomy levels
- Course Outcome specifications
- Mark distribution rules

### Database Schema

```sql
CREATE TABLE questions (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    unit TEXT NOT NULL,
    question TEXT NOT NULL,
    marks INTEGER NOT NULL
);
```

## 📝 Question Format

Generated questions follow this strict format:

```
Unit X:
1. Question text [CO:X] [BT:Y] (4 marks).
2. Question text [CO:X] [BT:Y] (4 marks).
3. Question text [CO:X] [BT:Y] (4 marks).
4. Question text [CO:X] [BT:Y] (6 marks).
5. Question text [CO:X] [BT:Y] (6 marks).
6. Question text [CO:X] [BT:Y] (6 marks).
```

Where:
- `CO:X` = Course Outcome number (matches unit number)
- `BT:Y` = Bloom's Taxonomy level (1-6)
- Each unit generates exactly 3 four-mark and 3 six-mark questions

## 🔧 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Main web interface |
| POST | `/generate-questions` | Upload syllabus and generate questions |
| GET | `/generate-papers` | Create question paper variants |
| GET | `/download/<filename>` | Download generated PDF files |

## 🎯 Use Cases

- **Educational Institutions**: Automate question paper creation
- **Online Learning Platforms**: Generate assessment content
- **Training Organizations**: Create evaluation materials
- **Academic Research**: Generate questions for studies

## 🔍 Troubleshooting

### Common Issues

1. **Ollama Connection Error**
   ```
   Error: Failed to generate questions from AI API
   ```
   **Solution**: Ensure Ollama is running on `localhost:11434`

2. **PDF Text Extraction Issues**
   ```
   Error: No units found in the syllabus text
   ```
   **Solution**: Ensure PDF contains readable text and proper unit formatting

3. **Insufficient Questions Generated**
   ```
   Error: Units do not have the required number of questions
   ```
   **Solution**: Check AI model response and adjust system prompt if needed

### Logging

Application logs are stored in `app.log` with detailed information about:
- File uploads and processing
- AI API interactions
- Question parsing and validation
- Error traces and debugging info

## 🚧 Future Enhancements

- [ ] Support for multiple LLM providers (OpenAI, Claude, etc.)
- [ ] Question difficulty analysis and balancing
- [ ] Manual question editing interface
- [ ] Template customization options
- [ ] Question quality scoring system
- [ ] Batch processing for multiple syllabi
- [ ] Export to multiple formats (Word, LaTeX, etc.)
- [ ] Question bank management system
- [ ] User authentication and role management
- [ ] Question review and approval workflow

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



## 🙏 Acknowledgments

- Ollama team for the excellent local LLM framework
- LLaMA model developers at Meta
- Flask community for the robust web framework
- ReportLab for professional PDF generation capabilities

## 📞 Support

For support, email: tarunmpk227@gmail.com or create an issue in the GitHub repository.

---

**Note**: This project requires a local Ollama installation with the LLaMA 3.2-vision model. Ensure your system has sufficient resources (minimum 8GB RAM recommended) for optimal performance.
