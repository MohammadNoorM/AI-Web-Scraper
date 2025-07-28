# AI Web Scraper

A powerful web scraping application that combines Selenium for dynamic content extraction with AI-powered parsing using Ollama. This tool allows you to scrape websites and extract specific information using natural language descriptions.

## Features

- **Dynamic Web Scraping**: Uses Selenium WebDriver to handle JavaScript-rendered content
- **AI-Powered Parsing**: Leverages Ollama (Gemma3 model) for intelligent content extraction
- **Streamlit UI**: User-friendly web interface for easy interaction
- **Content Cleaning**: Automatically removes scripts, styles, and unnecessary elements
- **Chunked Processing**: Handles large content by splitting into manageable chunks

## Prerequisites

- Python 3.7+
- Chrome browser installed
- Ollama installed and running locally
- Gemma3 model downloaded in Ollama

## Installation

1. **Clone or download the project files**

2. **Install required Python packages:**
   ```bash
   pip install streamlit selenium beautifulsoup4 langchain-ollama langchain-core
   ```

3. **Download ChromeDriver:**
   - Download the appropriate ChromeDriver version for your Chrome browser from [ChromeDriver Downloads](https://chromedriver.chromium.org/)
   - Place `chromedriver.exe` in the project root directory

4. **Set up Ollama:**
   - Install Ollama from [ollama.ai](https://ollama.ai)
   - Pull the Gemma3 model:
     ```bash
     ollama pull gemma3
     ```

## Usage

1. **Start the Streamlit application:**
   ```bash
   streamlit run main.py
   ```

2. **Using the application:**
   - Enter a website URL in the text input field
   - Click "Scrape Website" to extract the page content
   - View the extracted content in the expandable section
   - Enter a description of what information you want to extract
   - Click "Parse Content" to get the AI-processed results

## Example Use Cases

- **Product Information**: Extract product names, prices, and descriptions from e-commerce sites
- **News Articles**: Extract headlines, summaries, and publication dates
- **Contact Information**: Find phone numbers, emails, and addresses
- **Job Listings**: Extract job titles, companies, and requirements
- **Real Estate**: Extract property details, prices, and locations

## Project Structure

```
ai-web-scraping/
├── main.py          # Streamlit application entry point
├── scrape.py        # Web scraping functionality using Selenium
├── parse.py         # AI parsing using Ollama
├── chromedriver.exe # Chrome WebDriver (download separately)
└── README.md        # This file
```

## How It Works

1. **Web Scraping (`scrape.py`)**:
   - Uses Selenium WebDriver to load the target website
   - Waits for JavaScript content to load
   - Extracts the HTML body content
   - Cleans the content by removing scripts, styles, and formatting

2. **Content Processing**:
   - Splits large content into manageable chunks (6000 characters by default)
   - Prepares content for AI processing

3. **AI Parsing (`parse.py`)**:
   - Uses Ollama with the Gemma3 model
   - Processes each chunk with a specific prompt template
   - Extracts only the requested information based on natural language description

4. **User Interface (`main.py`)**:
   - Provides a clean Streamlit interface
   - Manages the scraping and parsing workflow
   - Displays results in an organized manner

## Configuration

### ChromeDriver
- Ensure `chromedriver.exe` is in the project root
- The version should match your Chrome browser version

### Ollama Model
- The application uses the "gemma3" model by default
- You can modify the model in `parse.py` if needed
- Ensure Ollama is running locally on your machine

### Content Chunking
- Default chunk size is 6000 characters
- Modify the `max_length` parameter in `split_dom_content()` function if needed

## Troubleshooting

### Common Issues

1. **ChromeDriver not found**:
   - Download the correct ChromeDriver version for your Chrome browser
   - Place it in the project root directory

2. **Ollama connection error**:
   - Ensure Ollama is running: `ollama serve`
   - Verify the Gemma3 model is installed: `ollama list`

3. **Website not loading**:
   - Some websites may block automated access
   - Try adding delays or user-agent headers if needed

4. **Memory issues with large content**:
   - Reduce the chunk size in `split_dom_content()`
   - Process smaller sections of content

## Dependencies

- **streamlit**: Web application framework
- **selenium**: Web browser automation
- **beautifulsoup4**: HTML parsing and cleaning
- **langchain-ollama**: Ollama integration for AI processing
- **langchain-core**: Core LangChain functionality

## License

This project is open source and available under the MIT License.

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve this tool.

## Disclaimer

Please ensure you comply with the target website's terms of service and robots.txt file when scraping. This tool is for educational and legitimate use cases only. 