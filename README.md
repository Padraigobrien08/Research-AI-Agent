# Research Assistant with Tool-Calling Agent

This project implements a research assistant that leverages Langchain's tool-calling capabilities to process user queries, search for information, query Wikipedia, and save research outputs. It integrates the Anthropic Claude model for language understanding and uses a structured response format validated by Pydantic.

## Features

- **Tool-Calling Agent**: Dynamically integrates various tools to handle research queries.
- **Structured Response**: Utilizes a Pydantic model (`ResearchResponse`) to ensure outputs are well-structured.
- **Integrated Tools**:
  - **Web Search**: Uses DuckDuckGo for real-time information searches.
  - **Wikipedia Query**: Fetches concise information using Wikipedia.
  - **File Saving**: Saves the structured research output to a text file.

## Project Structure

- **main.py**: 
  - Initializes environment variables.
  - Defines the `ResearchResponse` model.
  - Configures the language model (Anthropic Claude), prompt templates, and output parser.
  - Creates the tool-calling agent using available tools from `tools.py`.
  - Accepts a user query, invokes the agent, and prints the parsed research response.
  
- **tools.py**:
  - Implements `save_tool` to save research data to a file with a timestamp.
  - Implements `search_tool` for web search functionality using DuckDuckGo.
  - Implements `wiki_tool` for querying Wikipedia using a custom API wrapper.

## Installation

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```

2. **Set Up Environment Variables**:
   - Create a `.env` file in the project root and add any necessary environment variables.

3. **Install Dependencies**:
   Ensure you have Python 3.7+ installed and run:
   ```bash
   pip install -r requirements.txt
   ```
   **Dependencies include**:
   - `python-dotenv`
   - `pydantic`
   - `langchain`
   - `langchain_anthropic`
   - `langchain_core`
   - `langchain_community`
   - `duckduckgo-search`

## Usage

Run the main script:
```bash
python main.py
```
When prompted, enter your research query. The agent will process the query by:
- Utilizing web search and Wikipedia tools to gather information.
- Parsing the result into a structured format defined by the `ResearchResponse` model.
- Optionally saving the output to a text file.

## Customization

- **Modify the Response Format**:  
  You can update the `ResearchResponse` Pydantic model in `main.py` to customize the structure of the output.

- **Extend Tools**:  
  Add or modify tool integrations in `tools.py` and update the `tools` list in `main.py` to adjust which tools are available to the agent.

## Troubleshooting

- **Parsing Issues**:  
  If you encounter errors while parsing the response, the script will print an error message along with the raw output. Ensure the response format matches the `ResearchResponse` schema.

- **Environment Configuration**:  
  Verify that your `.env` file is correctly set up with any required API keys or configurations.

## Acknowledgements
- Built following tutorial by TechwithTim (https://www.youtube.com/watch?v=bTMPwUgLZf0)
- Built using the [Langchain](https://github.com/hwchase17/langchain) framework.
- Integrates capabilities from Anthropic's Claude model and community tools for comprehensive research assistance.
