# LangChain Multi-Agent Research Assistant

A lightweight multi-agent research workflow built with LangChain, OpenAI models, and web search/scraping tools. It automatically searches for recent information, scrapes the most relevant source, drafts a detailed research report, and then critiques the report for quality and gaps.

This project is designed as a practical example of an AI-powered research pipeline that combines agentic search, extraction, writing, and review steps in a single app.

## Features

- Multi-step research pipeline with specialized agents
- Web search using Tavily
- URL scraping and content extraction
- Structured report generation
- Critique loop for quality review
- Streamlit UI for interactive usage
- Python-first architecture for easy extension

## Architecture

The application follows a simple research flow:

1. Search agent gathers recent, relevant results
2. Reader agent picks a target URL and extracts readable content
3. Writer chain turns the gathered research into a polished report
4. Critic chain reviews the report and provides feedback

## Technologies Used

This project combines modern AI tooling and data extraction libraries to build an autonomous research workflow.

- Python 3.10+
- LangChain for agent orchestration and prompt pipelines
- LangChain OpenAI for LLM integration
- OpenAI GPT-4o-mini model
- Streamlit for the interactive web app
- Tavily API for web search
- BeautifulSoup for HTML parsing
- readability-lxml for article extraction
- trafilatura for clean text extraction
- requests for HTTP fetching
- python-dotenv for environment management
- rich for terminal output

## Installation & Configuration

### 1) Clone the repository

```bash
git clone https://github.com/your-username/LangChainMultiAgent.git
cd LangChainMultiAgent
```

### 2) Create a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate
```

On Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3) Install dependencies

```bash
pip install -r requirements.txt
```

### 4) Configure environment variables

Create a `.env` file in the project root and add the following:

```env
OPENAI_API_KEY=your_openai_api_key
TAVILY_API_KEY=your_tavily_api_key
```

You can also optionally add other configuration values later as the project evolves.

### 5) Verify setup

```bash
python main.py
```

If the environment is configured correctly, the pipeline will run and print the research output in the terminal.

## Project Structure

```text
.
├── app.py                 # Streamlit UI
├── main.py                # CLI entrypoint for a one-off research run
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
├── .env                   # Local environment variables
├── src/
│   ├── agents/
│   │   └── agents.py      # Search, reader, writer, and critic agents
│   ├── pipeline/
│   │   └── pipeline.py    # End-to-end research workflow orchestration
│   └── tools/
│       └── tools.py       # Search and scraping utilities
├── __init__.py
├── .venv                  # Local virtual environment (optional, generated locally)
└── .gitignore
```

## Getting Started

### Prerequisites

- Python 3.10 or newer
- OpenAI API access
- Tavily API access
- Internet access for web search and scraping

### Quick Installation

```bash
git clone https://github.com/your-username/LangChainMultiAgent.git
cd LangChainMultiAgent
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Create your `.env` file:

```env
OPENAI_API_KEY=your_openai_api_key
TAVILY_API_KEY=your_tavily_api_key
```

## Running the App

### Streamlit UI

```bash
streamlit run app.py
```

This starts the interactive research assistant where you can enter a topic and trigger the multi-agent workflow.

### Command-line runner

```bash
python main.py
```

The script runs a sample research topic through the pipeline and prints the search results, scraped content, generated report, and critique.

## Example Usage

```python
from src.pipeline.pipeline import run_research_pipeline

result = run_research_pipeline("The impact of AI on the job market in 2026")
print(result["report"])
```

## How the Pipeline Works

The pipeline is defined in [src/pipeline/pipeline.py](src/pipeline/pipeline.py) and orchestrates the following phases:

- Search for recent and reliable sources
- Identify the most relevant page
- Extract readable text from that page
- Generate a structured research report
- Critique the report for strengths and improvement areas

## Customization

You can extend the system by:

- swapping in different LLMs
- changing prompt instructions for the writer or critic
- adding additional research sources or scraping policies
- tailoring the underlying tools for domain-specific data gathering

## Contributing

Contributions are welcome.

1. Fork the repository
2. Create your feature branch:

```bash
git checkout -b feature/my-improvement
```

3. Commit your changes:

```bash
git commit -m "Add my improvement"
```

4. Push to your branch:

```bash
git push origin feature/my-improvement
```

5. Open a pull request

## License

This project is currently unlicensed. If you plan to share it publicly, consider adding an open-source license such as MIT or Apache 2.0.

## Notes

This repository is a strong starting point for experimentation with autonomous research agents and can be adapted for use cases such as:

- market research
- technical analysis
- journalism support
- competitive intelligence
- academic literature reviews

## Acknowledgements

- LangChain for agent orchestration and LLM integrations
- Tavily for search capabilities
- Streamlit for the application UI
- OpenAI for language model support
