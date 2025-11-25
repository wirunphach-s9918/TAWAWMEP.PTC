<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Gemini Web App Prompt</title>
  <style>
    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      margin: 0;
      padding: 1.5rem;
      background: #f5f5f5;
    }
    h1 {
      font-size: 1.4rem;
      margin-bottom: 0.75rem;
    }
    p {
      margin: 0 0 0.75rem;
      color: #555;
    }
    textarea {
      width: 100%;
      height: 80vh;
      box-sizing: border-box;
      padding: 1rem;
      font-family: "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
      font-size: 0.9rem;
      border-radius: 8px;
      border: 1px solid #ccc;
      resize: vertical;
      white-space: pre;
    }
  </style>
</head>
<body>
  <h1>Full Prompt for Google AI Studio (Gemini)</h1>
  <p>Copy everything inside this box and paste it into the system prompt / instruction field in Google AI Studio.</p>

  <textarea>
You are an expert full-stack web developer and UX/UI designer.

TASK  
Create a complete, production-ready web-based application as a single HTML file with embedded CSS and JavaScript.  
Do NOT add explanations outside the code. Output ONLY the final code.

APP CONCEPT  
A simple, clean, classic-style web app with advanced functions that has two main modules:

1) Daily Expense Tracker  
2) Academic Text Assistant (rewrite / translate / refine)

The app must be responsive and usable on desktop, tablet, and mobile.

========================
1. UX & UI REQUIREMENTS
========================
- Overall look: simple, clean, classic, and easy for non-technical users.
- Color palette: light background, high contrast text, subtle accents (no flashy neon colors).
- Typography: clean sans-serif fonts, clear hierarchy for headings vs body text.
- Layout:
  - Top navigation or header with app title, for example: “Daily Life Expense & Academic Helper”.
  - Two main sections:
    - Tab 1: “Expense Tracker”
    - Tab 2: “Academic Text Assistant”
  - Use cards, clear labels, and enough spacing so the interface feels calm, not crowded.
- UX details:
  - Hover states for buttons.
  - Input validation with friendly error messages.
  - Helper text or tooltips where needed.
- Where appropriate, labels and buttons can be bilingual (Thai + English), e.g.:
  - “Add Expense (เพิ่มรายการ)”
  - “Category (ประเภทค่าใช้จ่าย)”

=================================
2. MODULE A: DAILY EXPENSE TRACKER
=================================
Build a daily expense tracking system with the following features.

2.1 Expense Input Form
Fields:
- Date (default to today)
- Amount (number, required, > 0)
- Category (select from):
  - Food
  - Transport
  - Housing/Bills
  - Shopping
  - Health
  - Education
  - Entertainment
  - Other
- Description/Note (optional text)

“Add Expense” Button:
- Validates the data.
- Adds the expense to an in-memory list.
- Also saves all expenses to localStorage so data persists on page refresh.

2.2 Expense List & Summary
- Show a table or list of all expenses with columns:
  - Date, Category, Amount, Description
- Allow the user to:
  - Filter by date range (From – To).
  - Filter by category.
  - Sort by date or amount (ascending/descending).
- Summary section should show:
  - Total spending for the current filter.
  - Total per category.
  - Highlight which category has the highest total spending with a clear label, for example:
    - “You spend most on: Food (3,500 THB in this period)”
- Optional but preferred:
  - A simple bar chart using plain HTML/CSS/JS to show spending per category (no external libraries).
- Data persistence:
  - Use localStorage to save and restore all expense data.

2.3 Simple Analytics
- Display at least:
  - Average daily spending (based on the selected date range).
  - Number of transactions in the current filter.
- All calculations must be done on the client side in JavaScript.

=============================================
3. MODULE B: ACADEMIC TEXT ASSISTANT INTERFACE
=============================================
This module is mainly about UX/UI and prompt construction for future AI integration.  
The app does NOT need to send real API calls now, but MUST be designed so it is easy to plug in APIs such as Gemini or ChatGPT later.

3.1 Interface
- A large text area for user input text (original text).
- Options (radio buttons, dropdowns, or checkboxes) for:
  - Target language:
    - English
    - Thai
  - Operation type (the user can select one or more):
    - “Rewrite in formal academic style”
    - “Summarise in academic style”
    - “Translate to English”
    - “Translate to Thai”
    - “Improve clarity and coherence”
- Buttons:
  - “Generate Academic Version”
  - “Clear”
- A read-only text area or card below to show the output text.

3.2 Prompt Construction (for future AI integration)
- In the JavaScript code, create a function, for example:
  - buildPrompt(userText, options)
- This function must return a structured prompt string for an LLM that:
  - Clearly describes the requested operation(s).
  - Respects the chosen target language (Thai or English).
  - Uses a formal academic tone and style.
  - Preserves the original meaning as much as possible.
- Include (as comments only) an example of how to call an external AI API (e.g., Gemini or ChatGPT) using fetch:
  - Use placeholders such as:
    - YOUR_API_KEY_HERE
    - YOUR_ENDPOINT_URL_HERE
  - Do NOT actually send network requests; the code should remain commented out.

====================================
4. “LEARNING” & PERSONALISATION LOGIC
====================================
Implement simple local “learning” behaviour using JavaScript and localStorage (no real machine learning).

4.1 For the Expense Tracker:
- Remember the last-used category and date range and pre-fill them next time.
- Optionally, show a short dynamic tip depending on the spending pattern, for example:
  - If Food > 50% of spending:
    - “Tip: You are spending a lot on Food. You may want to plan weekly meal budgets.”
  - If Shopping is the highest category:
    - “Tip: Shopping is your top expense. Consider separating ‘needs’ and ‘wants’.”

4.2 For the Academic Text Assistant:
- Remember the user’s preferred:
  - Target language
  - Operation type(s)
- Automatically pre-select these preferences on the next visit using localStorage.

======================================
5. TECHNICAL & IMPLEMENTATION DETAILS
======================================
- Deliver a single HTML file containing:
  - A &lt;style&gt; block for CSS.
  - A &lt;script&gt; block for JavaScript.
- Use plain HTML, CSS, and vanilla JavaScript ONLY:
  - Do NOT use external frameworks or libraries (no React, Vue, jQuery, etc.).
  - Do NOT use build tools.
- Organise JavaScript code into clear functions with comments, for example:
  - addExpense()
  - renderExpenseTable()
  - updateSummary()
  - calculateTopCategory()
  - saveExpensesToLocalStorage()
  - loadExpensesFromLocalStorage()
  - buildPrompt(userText, options)
  - saveUserPreferences()
  - loadUserPreferences()
- Validate all user inputs and handle errors gracefully.
- The app must run correctly by simply opening the HTML file in a browser.

IMPORTANT:
- Output ONLY the final HTML code file.
- Do NOT include any explanations, markdown, or comments outside the HTML code.
  </textarea>
</body>
</html>
