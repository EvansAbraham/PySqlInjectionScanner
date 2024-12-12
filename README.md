# PySqlInjectionScanner

**PySqlInjectionScanner** is a Python-based tool that scans a given website for potential **SQL Injection** vulnerabilities. It detects forms on the page, extracts their details, and tests them with common SQL injection payloads to identify vulnerabilities.

## Features

- Scans a website for forms and tests them for SQL injection vulnerabilities.
- Supports both `GET` and `POST` methods for form submission.
- Detects common SQL errors to determine vulnerabilities.
- Uses **`python-dotenv`** for secure handling of sensitive information (e.g., `User-Agent`).

## Prerequisites

- Python 3.x
- Libraries: `requests`, `bs4`, `python-dotenv`

## Installation

### 1. Clone the repository

First, clone the repository to your local machine:

```bash
git clone https://github.com/EvansAbraham/PySqlInjectionScanner.git
cd PySqlInjectionScanner
```

### 2. Create a virtual environment (optional but recommended)

To avoid conflicts with other Python projects, it's a good idea to set up a virtual environment:

```bash
python3 -m venv venv  # Create a virtual environment
source venv/bin/activate  # Activate the virtual environment (macOS/Linux)
# .\venv\Scripts\activate  # For Windows
```

### 3. Install the required libraries

Install the required libraries by running:

```bash
pip3 install -r requirements.txt
```

Alternatively, you can manually install the libraries:

```bash
pip3 install requests bs4 python-dotenv
```

### 4. Set up your `.env` file

Create a `.env` file based on `.env.sample` in the root directory of the project to securely store sensitive data like the `User_Agent` and other credentials required for the project based on `.env.sample`.


This allows you to easily modify the user-agent string without hardcoding it into your code.
If you're unsure of your user agent search `what is my user agent ?` in google to find your user agent.


## Usage

### Running the Script

To scan a website for SQL injection vulnerabilities, run the script with the desired URL:

```bash
python scanner.py
```

The script will scan the specified URL (defined in the `urlToBeChecked` variable) and attempt SQL injection attacks on detected forms.

### Modifying the Target URL

If you want to scan a different website, modify the `urlToBeChecked` variable in the `scanner.py` script:

```python
urlToBeChecked = URL #URL variable that holds the website to be tested fetched from .env file
```

### Example Output

When running the script, it will detect the forms on the page and test them for SQL injection vulnerabilities. Example output:

```bash
[+] Detected 3 forms on https://www.example.com.
[!] SQL injection vulnerability detected in link: https://www.example.com
```

If no vulnerabilities are found, the script will output:

```bash
No SQL injection attack vulnerability detected
```

### Scan Process Overview

1. **Form Detection**:  
   The script scans the webpage and identifies all forms.

2. **SQL Injection Testing**:  
   The script submits different types of payloads to each form (e.g., single quote `"` and apostrophe `'`) and checks if the form returns any error indicating SQL injection vulnerability.

3. **Logging Results**:  
   The results are printed on the console, informing you whether SQL injection vulnerabilities were found for each form.


## Troubleshooting

1. **Module Not Found Error**:
   If you encounter a `ModuleNotFoundError`, make sure you have installed all the dependencies in the virtual environment and activated it.

2. **Invalid URL**:
   If you get an "Invalid URL" error, check that the URL you're providing is valid and correctly formatted.

3. **Timeout/Connection Issues**:
   If the script is timing out or unable to connect to the target URL, ensure the website is reachable or try increasing the `timeout` in the `requests.get()` method.
