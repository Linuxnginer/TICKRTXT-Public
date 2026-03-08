# TICKRTXT (www.tickrtxt.com)

A lightweight **FastAPI-based web application** that scans financial markets for **high-volume stocks and high-volume out-of-the-money (OTM) options activity**.  

The application automatically runs background scans, caches the results, and displays them through a fast web interface powered by **Jinja2 templates**.

This project is designed for traders, analysts, and developers who want a **simple market intelligence dashboard** without complex infrastructure.

---

# 🚀 Features

## Stock Volume Scanner
- Retrieves **top trading volume stocks**
- Displays results on the homepage
- Data cached in memory for fast loading

## Options Activity Scanner
- Scans multiple tickers for **highest volume OTM options**
- Aggregates results across tickers
- Filters out invalid or empty responses

## Background Data Refresh
- Runs automated scans every **4 hours**
- Uses asynchronous background tasks
- Prevents blocking API requests

## Web Interface
- Built with **FastAPI + Jinja2**
- Clean routes and template rendering
- Simple navigation structure

## Session Support
- Stores the user's **last viewed ticker**
- Uses secure session middleware

## CORS Enabled
- Allows integration with other services or APIs.

---

# 🏗 Project Structure

```
project/
│
├── main.py
├── file1.py
├── file3.py
│
├── templates/
│   ├── home.html
│   ├── options.html
│   └── about.html
│
├── static/
│   ├── css/
│   ├── js/
│   └── images/
│
└── README.md
```

### File Descriptions

| File | Description |
|-----|-------------|
| `main.py` | FastAPI application and routes |
| `file1.py` | Contains the `get_top_volume()` scanner |
| `file3.py` | Contains ticker retrieval and options scan logic |
| `templates/` | HTML templates rendered by Jinja2 |
| `static/` | Static assets (CSS, JS, images) |

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone https://github.com/yourusername/market-scanner.git
cd market-scanner
```

---

## 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

### Mac / Linux
```bash
source venv/bin/activate
```

### Windows
```bash
venv\Scripts\activate
```

---

## 3. Install Dependencies

```bash
pip install fastapi uvicorn jinja2 python-multipart
```

---

# 🔑 Environment Variables

The application uses a session secret for security.

Set it before running the server:

```bash
export SESSION_SECRET="your_secure_secret_key"
```

Windows:

```bash
set SESSION_SECRET=your_secure_secret_key
```

If not provided, the app defaults to:

```
supersecretkey
```

⚠️ **Always use a strong secret key in production.**

---

# ▶️ Running the Application

Start the development server using **Uvicorn**:

```bash
uvicorn main:app --reload
```

Open your browser:

```
http://127.0.0.1:8000
```

---

# 🌐 Application Routes

| Route | Description |
|------|-------------|
| `/` | Homepage showing high-volume stocks |
| `/options` | Displays highest volume OTM options |
| `/about` | Information page |

---

# 🔄 Background Scanning System

The application automatically refreshes market data using an asynchronous loop.

### Startup Process

1. Server starts
2. Initial scan runs immediately
3. Background task begins periodic updates

### Scan Interval

```
Every 4 hours
```

### Cached Data

Two in-memory datasets are maintained:

```python
cached_volume_data
cached_options_data
```

Benefits:

- Faster page rendering
- Reduced API usage
- Efficient resource utilization

---

# 📊 Data Flow

```
Ticker Source
     ↓
get_tickers_page1()
     ↓
Options Scanner
get_highest_volume_otm()
     ↓
Aggregate Results
     ↓
Cache Data
     ↓
Display in Web Interface
```

---

# 🧠 Error Handling

The scanner is designed to **fail gracefully**.

Examples:

- Individual ticker scan errors are skipped
- Global scan failures are logged
- Background loop continues running

Example log output:

```
Error updating volume scan: ...
Error updating options scan: ...
Error in periodic scan loop: ...
```

---

# 🔒 Security Notes

Recommended improvements for production deployments:

- Restrict CORS origins
- Use a strong `SESSION_SECRET`
- Implement logging and monitoring
- Add authentication if needed
- Rate limit API access

---

# 📈 Possible Future Improvements

Potential enhancements include:

- Real-time updates with WebSockets
- Redis or database caching
- User watchlists
- Alerts for unusual options activity
- Chart integrations
- Authentication system
- Docker containerization
- Cloud deployment

---

# 🛠 Tech Stack

- **Python**
- **FastAPI**
- **Jinja2**
- **Uvicorn**
- **Starlette Middleware**
- **AsyncIO**

---

# 🧪 Example Workflow

1. User opens homepage:

```
/
```

2. Cached high-volume stock data is displayed.

3. User navigates to:

```
/options
```

4. Options scanner results appear instantly.

5. Background tasks refresh market data every **4 hours**.

---

# 📜 License

MIT License

---

# 👨‍💻 Author

Developed as a lightweight **market scanning dashboard for identifying high-volume stocks and options activity.**

Contributions, improvements, and feature suggestions are welcome.
