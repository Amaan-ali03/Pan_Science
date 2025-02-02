# Name Disambiguator

## Overview
The **Name Disambiguator** is a Python-based tool that helps resolve company names, ticker symbols, and exchange names from structured and unstructured inputs. It is useful for financial applications, data enrichment, and entity recognition.

## Features
- Parses structured inputs like `NASDAQ:AAPL` or `NYSE:MSFT`.
- Resolves company names from common aliases (`Tesla` -> `TSLA` on NASDAQ).
- Supports CSV-based lookup for company data.
- Handles errors gracefully when companies are not found.

## Setup Instructions

### **1. Prerequisites**
- Python 3.6+
- A CSV file containing company data (sample format below)

### **2. Install Dependencies**
No external dependencies are required, as the script uses built-in Python libraries (`csv`, `os`, `re`).

### **3. Prepare Company Data CSV**
Ensure you have a `company_data.csv` file in the following format:

```
Company Name,Ticker Symbol,Exchange Name,Aliases
Apple Inc.,AAPL,NASDAQ,Apple
Tesla,TSLA,NASDAQ,
Microsoft Corp.,MSFT,NYSE,Microsoft
Alphabet Inc.,GOOGL,NASDAQ,Google
```

### **4. Run the Script**
```sh
python name_disambiguator.py
```

## Usage Examples

### **Python Usage**
```python
from name_disambiguator import NameDisambiguator

disambiguator = NameDisambiguator("company_data.csv")

# Structured Input
print(disambiguator.disambiguate("NASDAQ:AAPL"))  # ('Apple Inc.', 'AAPL', 'NASDAQ')

# Unstructured Input
print(disambiguator.disambiguate("Google"))  # ('Alphabet Inc.', 'GOOGL', 'NASDAQ')

# Invalid Input
print(disambiguator.disambiguate("UnknownCorp"))  # None
```

## Error Handling
- If the CSV file is missing, the script will raise `FileNotFoundError`.
- If an input cannot be resolved, the function will return `None`.

## Author
Created by [Amaan Ali]

