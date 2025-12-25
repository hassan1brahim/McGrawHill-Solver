# McGrawHill Quiz Automation

An automated quiz-solving and note-taking tool for McGrawHill Connect. The tool solves quiz questions using DeepSeek AI and saves all questions and answers to a text file, perfect for quick revision before exams without redoing all the questions manually.

## Purpose

This tool helps you:
- **Complete practice quizzes** efficiently using AI
- **Generate study notes** automatically from quiz questions and answers
- **Quick revision** the day before an exam by reviewing the saved Q&A file instead of retaking the entire quiz
- **Save time** on homework while still learning the material through reviewing the notes

## Features

- Automated login to McGrawHill Connect
- Handles multiple question types:
  - Multiple choice
  - True/False
  - Fill-in-the-blank
- Uses DeepSeek AI API to generate answers
- Saves all questions and answers to `quiz_answers.txt` for easy revision
- Automatic error handling and page refresh on failures
- Session recovery if browser crashes

## Requirements

### Software Requirements
- **Python 3.x**
- **Chrome browser** (version 143+ recommended)
- **ChromeDriver** (automatically managed by webdriver-manager)
- **DeepSeek API key** ([Get one here](https://platform.deepseek.com/))

### Python Dependencies
Install all dependencies with:
```bash
pip install -r requirements.txt
```

The requirements.txt includes:
- selenium==4.38.0
- webdriver-manager==4.0.2
- beautifulsoup4==4.14.2
- requests==2.32.5

## Installation

1. Clone the repository:
```bash
git clone https://github.com/hassan1brahim/McGrawHill-Solver.git
cd McGrawHill-Solver
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Get a DeepSeek API key from [DeepSeek](https://platform.deepseek.com/)

## Setup

1. Open `test.ipynb` in Jupyter Notebook

2. In **Cell 2**, update your login credentials:
```python
driver.find_element(By.ID, "login-email").send_keys("your_email@example.com")
driver.find_element(By.ID, "login-password").send_keys("your_password")
```

3. In **Cell 3**, add your DeepSeek API key:
```python
API_KEY = "your-deepseek-api-key-here"
```

## Usage

### Step-by-Step Guide

1. **Open Jupyter Notebook:**
```bash
jupyter notebook
```

2. **Open `test.ipynb`**

3. **Run Cell 1** - Imports and driver setup
   - This initializes the Chrome browser

4. **Run Cell 2** - Login
   - This logs you into McGrawHill Connect
   - **IMPORTANT:** After login, manually navigate to the quiz you want to complete
   - Don't close the browser window

5. **Run Cell 3** - Start automation
   - The script will automatically:
     - Answer all quiz questions using AI
     - Save questions and answers to `quiz_answers.txt`
     - Click through all questions until the quiz is complete
   
6. **Review your notes**
   - Open `quiz_answers.txt` to see all questions and answers
   - Use this file for quick revision before your exam

7. **Run Cell 4** (when finished) - Close browser

### Workflow Example

**During homework/practice:**
```bash
# Run the automation → generates quiz_answers.txt with all Q&A
```

**Day before exam:**
```bash
# Just read quiz_answers.txt for quick revision
# No need to redo the entire quiz!
```

## Output

All questions and answers are saved to `quiz_answers.txt` in the following format:
```
Question: What is 2 + 2?
Answer: 4
--------------------------------------------------------------------------------
Question: True or False: Python is a programming language.
Answer: True
--------------------------------------------------------------------------------
```

## Notes

- **Educational purposes only** - Use responsibly for practice and note-taking
- ChromeDriver version is automatically managed by webdriver-manager
- The script handles session recovery if the browser crashes
- Confidence buttons are clicked automatically when available
- Add `quiz_answers.txt` to `.gitignore` to avoid committing your quiz data
- Perfect for generating study materials from practice quizzes

## File Structure
```
McGrawHill-Solver/
├── test.ipynb              # Main Jupyter notebook
├── requirements.txt        # Python dependencies
├── README.md              # This file
├── .gitignore             # Git ignore file
```

## Troubleshooting

**ChromeDriver version mismatch:**
- The webdriver-manager package automatically downloads the correct ChromeDriver version
- If issues persist, try: `pip install --upgrade webdriver-manager`

**API errors:**
- Verify your DeepSeek API key is valid
- Check your API quota/credits

**Element not found errors:**
- McGrawHill may have updated their HTML structure
- Check the CSS selectors in the code

## License

MIT License - Feel free to use and modify as needed.

## Disclaimer

This tool is for educational purposes and creating study materials. Use responsibly and in accordance with your institution's academic integrity policies. The purpose is to help generate revision notes from practice quizzes, not to cheat on graded assessments.
