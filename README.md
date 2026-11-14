MonieControl lets users log income and expenses, set spending limits per category, and watch their budgets update in real time. It began as an idea during my internship at DecodeLabs and is being built out into a larger product, with multi-currency support planned.

Features

Dashboard

Live balance, income, and expense summary cards
Real-time transaction ledger, sorted newest first
Budget "vaults" with progress bars calculated from actual spending per category
Log transactions with a type-aware category dropdown (income vs. expense)
Create new budget vaults with a custom allocation cap and color

Authentication UI

Tabbed Log In / Sign Up interface
Client-side validation: email format, password length, password confirmation
Inline error messages and a show/hide password toggle

Profile

Profile modal with auto-generated avatar initials
Edit name, email, and preferred currency
Falls back to localStorage when the server is offline

Design and UX

Design-token system built on CSS custom variables
Light and dark mode, saved to localStorage and applied before first paint to avoid flicker
Responsive layouts from desktop down to 250px screens

REST API

Modular Express routes for budgets, transactions, contact/waitlist, and profile
Server-side validation (syntactic and semantic) with proper HTTP status codes
Query filtering on transactions (type, category, limit)
Computed fields: percentage used, remaining amount, and budget status (on_track, warning, over_budget)
CORS, request logging, a health-check endpoint, and centralized error handling
Tech Stack
Layer	Technology
Frontend	HTML5, CSS3, JavaScript (ES6+, no framework)
Backend	Node.js, Express.js
Tooling	npm, nodemon, cors
Data	In-memory store (database planned)
Font	Plus Jakarta Sans
Project Structure
MonieControl/
├── index.html              # Landing page
├── style.css               # Global styles and design tokens
├── script.js               # Landing page logic
├── login.html              # Log in / Sign up page
├── login.css
├── login.js
├── pages.css               # Shared styles for sub-pages
├── server.js               # Express entry point
├── package.json
├── app-resources/
│   ├── app-dashboard.html  # Main dashboard
│   ├── app-dashboard.css
│   ├── app-dashboard.js
│   └── profile.js          # Profile modal logic
├── routes/
│   ├── budgets.js
│   ├── transactions.js
│   ├── contact.js
│   └── profile.js
└── images/
Getting Started
Prerequisites
Node.js v16 or higher
npm
Installation
bash
# Clone the repository
git clone https://github.com/<your-username>/MonieControl.git
cd MonieControl



Health
Method	Endpoint	Description
GET	/health	Server status check
Budgets
Method	Endpoint	Description
GET	/budgets	List all budgets with computed status/summary
GET	/budgets/:id	Get a single budget
POST	/budgets	Create a budget
PUT	/budgets/:id	Update a budget

POST body: { "category": "Food", "allocated": 600, "spent": 0, "currency": "USD", "color": "#A5856E" }

Transactions
Method	Endpoint	Description
GET	/transactions	List transactions (?type=, ?category=, ?limit=)
GET	/transactions/:id	Get a single transaction
POST	/transactions	Log a transaction

POST body: { "description": "Groceries", "amount": 85.5, "type": "expense", "category": "Food", "date": "2026-06-02" }

Contact / Waitlist
Method	Endpoint	Description
GET	/contact	List waitlist submissions
POST	/contact	Join the waitlist
Profile
Method	Endpoint	Description
GET	/profile	Get current profile
PUT	/profile/update	Update name, email, currency
Response format
json
{
  "status": "success",
  "count": 4,
  "summary": { "totalAllocated": 4400, "totalSpent": 2640 },
  "data": []
}

Errors return { "status": "error", "code": 400, "message": "...", "errors": [] }.

Roadmap
[ ] Currency exchange and saving in native currency (in progress)
[ ] Persistent database (replace the in-memory store)
[ ] Real authentication (JWT/session-based) with protected routes
[ ] Spending analytics and charts
[ ] Edit and delete transactions from the dashboard
[ ] Budget alerts when nearing or exceeding limits
Author

Snow Works | Founder, Works Technology Computer Engineering student, University of Uyo











# MonieControl
A web based application that enables users monitor, control, manage, supervise  and track  expenses, exchange currencies and save it in native currency while helping you control wasteful spending.  The currency exchange phase is a part of the product that is in progress.

Now i got this idea in during my internship at decode labs and looking forward to bilding it deep and scalling it .

