# DocChat

DocChat is a FastAPI-based application that lets you upload PDF files and ask questions about them. It uses PyMuPDF to read PDFs, sentence embeddings to search the content, ChromaDB for storage, and Gemini for answering questions.

## What you need before starting

Before running this project on a fresh Windows machine, make sure you have:

- Python 3.10, 3.11, or 3.12 installed
- VS Code installed
- Git installed (optional, but useful if you plan to clone the project)
- A Google API key for Gemini

If Python is not installed yet, install it first.

## 1. Install Python

On Windows, the easiest way is to install Python from the official website:

- Go to https://www.python.org/downloads/
- Download Python 3.11 or 3.12
- Run the installer
- Make sure you check the box that says "Add Python to PATH"

After installation, open a new terminal and verify it worked:

```powershell
python --version
py --version
```

If either command shows a version number, Python is installed correctly.

## 2. Open the project in VS Code

Option A: Clone the repository

```powershell
git clone <your-repository-url>
cd <your-repository-folder>
```

Option B: Download the project as a ZIP file

- Download the ZIP file from GitHub
- Extract it
- Open the extracted folder in VS Code

## 3. Create and use a virtual environment

A virtual environment keeps this project's dependencies separate from the rest of your computer.

In the project folder, open the terminal in VS Code and run:

```powershell
python -m venv .venv
```

This creates a folder called .venv inside the project.

### Activate the virtual environment

In PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks the script, run this once and then try again:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

If you are using Command Prompt instead of PowerShell:

```cmd
.venv\Scripts\activate.bat
```

When it is activated, your terminal prompt will usually show (.venv) at the start.

## 4. Install the required packages

With the virtual environment active, install the dependencies:

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

This may take a few minutes. Wait for it to finish.

## 5. Create a .env file

Create a file named .env in the project root and add your Google API key.

Example:

```env
GOOGLE_API_KEY=your_google_api_key_here
CHROMA_DIRECTORY=chroma_db
UPLOAD_DIRECTORY=uploads
```

You can also copy the sample file if it exists.

## 6. Run the application

Start the app with:

```powershell
uvicorn app.main:app --reload
```

Then open this URL in your browser:

```text
http://127.0.0.1:8000
```

## 7. Use the app

Once the app is running:

- Upload one or more PDF files
- Select the documents you want to use
- Ask questions about the uploaded content

## 8. Stop the server

When you are done, press Ctrl + C in the terminal.

## 9. Activate the environment next time

When you open the project again later, activate the virtual environment again:

```powershell
.\.venv\Scripts\Activate.ps1
```

## Features

- Responsive chat-style web interface
- Upload and index PDF files
- Ask questions about selected documents
- Hybrid semantic and keyword retrieval
- Page-level source references

## API overview

- GET /documents — list indexed PDFs
- POST /documents/upload — upload and index a PDF
- DELETE /documents/{document_id} — remove a PDF and its vectors
- POST /chat — ask selected documents a question
- GET /health — application health check
