Overview
This repository contains a Python-based Streamlit application designed to fetch and summarize blog articles into concise bullet-point formats using large language models (LLMs) like OpenAI's GPT series. It leverages web scraping to extract article content from URLs and generates structured summaries with customizable bullet-point counts. Additional utilities for token counting, cost estimation, and multi-LLM support are included for extensibility.
Ideal for quick content digestion, research, or automated note-taking from online articles.
Features

Article Fetching: Automatically scrape and extract text from blog URLs using newspaper3k.
LLM Integration: Supports OpenAI GPT models (e.g., gpt-3.5-turbo), with hooks for NLPCloud and Cohere.
Customizable Summaries: Specify min/max number of bullet points; summaries incorporate perplexity and burstiness for natural, human-like output.
Token & Cost Management: Estimate input tokens and API costs before generation.
Streamlit UI: Simple web interface for inputting URLs, selecting models, and viewing results.
Prompt Engineering: Pre-built templates for high-quality, emoji-enhanced bullet summaries.
Extras: YouTube transcript extraction and domain authority checks.

Technologies

Language: Python 3.x
Framework: Streamlit for the UI
LLMs: OpenAI API (primary), NLPCloud, Cohere
Scraping: Newspaper3k
Other: Tiktoken (tokenization), Requests (API calls)

Installation

Clone the repository:textgit clone https://github.com/Shreyaaaa010102/blog.git
cd blog
Create a virtual environment (recommended):textpython -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install dependencies:textpip install -r requirements.txt
Set up environment variables:
For OpenAI: Export your API key as OPENAI_API_KEY (e.g., export OPENAI_API_KEY=your_key_here).
For Cohere: Update cohere_api_key in llm.py (currently a placeholder).
For NLPCloud: Update nlp_cloud_key in llm.py.


Usage

Run the Streamlit app:textstreamlit run resp.pyThis launches a local web server (usually at http://localhost:8501).
In the app:
Enter a blog URL (e.g., https://example.com/article).
Select a model (e.g., gpt-3.5-turbo).
Adjust min/max bullet points (default: 5-10).
Click "Generate Summary" to fetch, process, and display the bullet-point summary.


Example Output
For a sample article, the summary might look like:

🚀 Key Innovation: The tool introduces novel features...
📊 Data Insights: Backed by stats showing 30% improvement...
⚠️ Challenges: Potential scalability issues in large datasets...

Command-Line Usage (Advanced)
You can also use the core functions directly in a Python script:
Pythonfrom helpers import get_article_from_url
from llm import llm_generate_text
from prompts1 import blog_bullet_summary_prompt

url = "https://example.com/blog-post"
article = get_article_from_url(url)
if article:
    prompt = blog_bullet_summary_prompt.format(MaxPoints=10, MinPoints=5, InputText=article)
    summary = llm_generate_text(prompt, "OpenAI", "gpt-3.5-turbo")
    print(summary)
Project Structure
textblog/
├── .gitignore.txt       # Git ignore rules
├── helpers.py           # Utility functions (fetching, tokens, costs)
├── llm.py               # LLM generation wrappers (OpenAI, etc.)
├── prompts1.py          # Prompt templates for summarization
├── resp.py              # Main Streamlit app (blog summary generator)
└── requirements.txt     # Dependencies
Contributing

Fork the repo and create a pull request.
Add new LLM providers in llm.py.
Improve prompts in prompts1.py for better outputs.
Ensure code follows PEP 8 standards.

License
MIT License (feel free to add one if desired).
Contact
Shreyaaaa010102 - Feel free to open issues for bugs or features!
