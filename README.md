# AI Agent

A modular AI-powered code assistant that can interact with your filesystem, read and write files, and execute Python scripts. The project includes a sample calculator app and a set of utility functions for file operations, all orchestrated by an AI agent using the Gemini API.

## Features

- **AI Code Assistant**: Interprets user prompts and performs actions like listing files, reading/writing file content, and running Python scripts.
- **Calculator Example**: A simple calculator package demonstrating modular Python code.
- **Extensible Functions**: Easily add new file operations or extend the agent's capabilities.
- **Secure File Access**: All file operations are sandboxed to a working directory.

## Project Structure

```
.
├── main.py                # Entry point for the AI agent
├── config.py              # Configuration (working dir, limits)
├── functions/             # Modular file operation functions
│   ├── call_function.py
│   ├── get_file_content.py
│   ├── get_files_info.py
│   ├── run_python_file.py
│   └── write_file.py
├── calculator/            # Example calculator app
│   ├── main.py
│   ├── tests.py
│   ├── lorem.txt
│   └── pkg/
│       ├── calculator.py
│       └── render.py
├── tests.py               # Test runner for agent functions
├── pyproject.toml         # Project metadata and dependencies
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.13+
- [Google Gemini API key](https://ai.google.dev/)
- Install dependencies:

```bash
pip install -r requirements.txt
# or, if using pyproject.toml:
pip install .
```

### Environment Setup

Create a `.env` file in the project root with your Gemini API key:

```
GEMINI_API_KEY=your_api_key_here
```

### Usage

#### Run the AI Agent

```bash
python main.py "How do I build a calculator app?" --verbose
```

- The agent will interpret your prompt and perform actions like listing files, reading content, or running scripts in the `calculator/` directory.

#### Calculator Example

- The calculator logic is in `calculator/pkg/calculator.py`.
- Run the calculator example:

```bash
python calculator/main.py
```

#### Run Tests

```bash
python tests.py
```

## How It Works

- The agent uses the Gemini API to interpret user prompts.
- It can:
  - List files and directories
  - Read file content (with size limits)
  - Write to files
  - Execute Python scripts (sandboxed to the working directory)
- All file operations are routed through the `functions/` modules for safety and extensibility.

## Configuration

- `config.py` sets:
  - `MAX_CHARS`: Max characters to read from files
  - `WORKING_DIR`: Directory for file operations (default: `./calculator`)
  - `MAX_ITERS`: Max agent response iterations

## Dependencies

- `google-genai`
- `python-dotenv`

(See `pyproject.toml` for exact versions.)

## Extending

- Add new functions to the `functions/` directory and register them in `call_function.py`.
- Update the agent's system prompt in `main.py` to describe new capabilities.

