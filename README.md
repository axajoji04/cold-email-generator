# 📧 Cold Email Generator

An AI-powered automation tool that generates personalized cold emails by scraping job postings, matching them with your portfolio, and creating tailored outreach messages in seconds.

## 🎯 Overview

This tool automates the entire cold email workflow for business development and job applications. Simply provide a careers page URL, and the system will:
- Extract relevant job postings
- Match required skills with your portfolio
- Generate personalized cold emails with relevant project links

## ✨ Features

- **Smart Web Scraping**: Extracts job postings from any careers page
- **LLM-Powered Parsing**: Uses Groq's Llama 3.3 to extract structured job data
- **Intelligent Filtering**: Automatically identifies tech-related positions
- **Semantic Matching**: Vector database (ChromaDB) matches skills to portfolio projects
- **Personalized Generation**: Creates context-aware cold emails
- **Clean UI**: Simple Streamlit interface for easy interaction

## 🛠️ Tech Stack

- **LangChain**: LLM orchestration and prompt management
- **Groq API**: Fast LLM inference with Llama 3.3 70B
- **ChromaDB**: Vector database for semantic search
- **Streamlit**: Web interface
- **Python 3.8+**: Core language

## 📋 Prerequisites

- Python 3.8 or higher
- Groq API key ([Get one here](https://console.groq.com))
- pip or conda for package management

## 🚀 Installation

1. **Clone the repository**
```bash
git clone <https://github.com/axajoji04/cold-email-generator>
cd cold-email-generator
```

2. **Create a virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Set up environment variables**

Create a `.env` file in the root directory:
```env
GROQ_API_KEY=your_groq_api_key_here
```

5. **Prepare your portfolio**

Edit `app/resource/my_portfolio.csv` with your projects:
```csv
Techstack,Links
"React, Node.js, MongoDB","https://github.com/yourproject1"
"Python, FastAPI, PostgreSQL","https://github.com/yourproject2"
```

## 📦 Required Dependencies

Create a `requirements.txt` file:
```
streamlit
langchain
langchain-groq
langchain-community
chromadb
pandas
python-dotenv
```

## 🎮 Usage

1. **Start the application**
```bash
streamlit run app/main.py
```

2. **Open your browser**
   - The app will automatically open at `http://localhost:8501`

3. **Generate cold emails**
   - Enter a careers page URL (e.g., `https://careers.nike.com/jobs`)
   - Click "Submit"
   - View generated personalized emails

## 📁 Project Structure

```
cold-email-generator/
│
├── app/
│   ├── main.py              # Streamlit app entry point
│   ├── chains.py            # LLM chain logic
│   ├── portfolio.py         # Portfolio management & vector DB
│   ├── utils.py             # Text cleaning utilities
│   └── resource/
│       └── my_portfolio.csv # Your portfolio data
│
├── vectorstore/             # ChromaDB persistent storage (auto-generated)
├── .env                     # Environment variables (create this)
├── requirements.txt         # Python dependencies
└── README.md               # This file
```

## 🔧 Configuration

### Customize the Email Template

Edit the prompt in `chains.py` → `write_mail()` method:

```python
prompt_email = PromptTemplate.from_template(
    """
    ### JOB DESCRIPTION:
    {job_description}

    ### INSTRUCTION:
    You are [YOUR NAME], a [YOUR ROLE] at [YOUR COMPANY]...
    """
)
```

### Adjust Tech Keywords

Modify `tech_keywords` in your main script to filter different job types:

```python
tech_keywords = [
    "software", "developer", "engineer", 
    "data", "machine learning", "AI"
]
```

## 🎯 How It Works

1. **Scraping**: WebBaseLoader fetches the careers page HTML
2. **Cleaning**: Removes HTML tags, URLs, and special characters
3. **Extraction**: LLM extracts structured job data (role, skills, experience, description)
4. **Filtering**: Identifies relevant tech positions based on keywords
5. **Matching**: Vector search finds portfolio projects matching required skills
6. **Generation**: LLM creates personalized cold email with relevant links

## 🔍 Example Output

```markdown
Subject: Partnering to Scale Your Engineering Team

Hi [Hiring Manager],

I noticed your opening for Senior Backend Engineer at Nike. With your focus 
on building scalable microservices and real-time data processing, I believe 
AtliQ can add significant value.

We've helped companies like yours:
- Build cloud-native architectures: [project link]
- Implement ML pipelines for real-time analytics: [project link]

Our expertise in Python, AWS, and distributed systems aligns perfectly with 
your requirements. Would you be open to a brief call to explore how we can 
support your team's goals?

Best regards,
Mohan
Business Development Executive, AtliQ
```

## ⚠️ Limitations

- Requires valid Groq API key (free tier has rate limits)
- Web scraping depends on website structure (some sites may not work)
- Portfolio matching quality depends on how well you've documented your projects
- Not a true AI agent—follows a fixed pipeline without dynamic decision-making

## 🐛 Troubleshooting

**Error: "Context too big. Unable to parse jobs."**
- The scraped page is too large. Try a more specific job posting URL.

**Error: "Unable to load portfolio"**
- Check that `my_portfolio.csv` exists in `app/resource/`
- Verify the CSV format matches the expected structure

**No emails generated**
- Check if the URL contains actual job postings
- Verify your GROQ_API_KEY is set correctly

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [LangChain](https://www.langchain.com/) for LLM orchestration
- [Groq](https://groq.com/) for fast LLM inference
- [ChromaDB](https://www.trychroma.com/) for vector storage
- [Streamlit](https://streamlit.io/) for the web framework

## 📧 Contact

Name - Axa Joji [https://github.com/axajoji04]
Project Link: [https://github.com/axajoji04/cold-email-generator](https://github.com/axajoji04/cold-email-generator)

---

⭐ If you find this project useful, please consider giving it a star on GitHub!
