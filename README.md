# 🧬 ProteinAI — Intelligent Protein Supplement Deal Finder

ProteinAI is a **data-driven, AI-assisted platform** that discovers, compares, and ranks protein supplements across multiple e-commerce platforms based on **value, quality, and trust metrics** — not just price.

Inspired by platforms like Flash.co, this system is specifically built for **fitness enthusiasts** who want the **best protein deals without compromising quality**.

---

# 🚀 Key Features

## 🔍 Multi-Source Product Aggregation

* Scrapes protein supplements from multiple platforms:

  * Amazon
  * Nutrabay
  * HealthKart
  * Flipkart
* Extracts:

  * Product name
  * Price
  * Ratings
  * Review count
  * Brand

---

## 📊 Advanced Ranking Engine (Core Feature)

Unlike basic comparison tools, ProteinAI ranks products using a **multi-metric scoring algorithm**:

### Score Formula:

```
score =
0.40 * protein_per_rupee
+ 0.25 * rating
+ 0.20 * log(review_count)
+ 0.15 * brand_trust_score
```

### Metrics Considered:

* 💰 Protein per rupee (value)
* ⭐ Customer ratings
* 📈 Review volume (trust reliability)
* 🏷️ Brand trust score
* 🧪 Ingredient quality (extensible)

---

## 🧠 Intelligent Deal Detection

* Detects:

  * Best value protein
  * Highest rated products
  * Budget-friendly options
  * Price drops (future extension)
* Highlights **top deals automatically**

---

## 🗄️ Normalized Database Design

Relational PostgreSQL schema:

```
brands
products
prices
reviews
```

### Why this matters:

* Tracks price history across websites
* Stores multi-source reviews
* Avoids data duplication
* Enables advanced analytics

---

## 🔄 Automated Data Pipeline

```
Scraper → Data Cleaning → Database → Ranking Engine → API
```

* Cleans raw scraped data
* Prevents duplicate entries
* Automatically updates price & review history

---

## 🌐 REST API (FastAPI)

Endpoints include:

* `GET /products` → Fetch all products
* `POST /products` → Add new product
* `GET /best-proteins` → Ranked protein list

Interactive API docs:

```
http://127.0.0.1:8000/docs
```

---

## 🤖 Scalable Scraping Architecture

```
Search Scraper
     ↓
Product URL Queue
     ↓
Product Scraper Workers
     ↓
Data Pipeline
     ↓
PostgreSQL
```

Supports:

* Parallel scraping (future)
* Multi-platform expansion
* Automation with n8n

---

## ⏱️ Automation with n8n

* Schedule scraping jobs:

  * Every 6 hours / daily
* Workflow:

```
Trigger → Scraper → DB Update → Ranking → Alerts
```

Future:

* Email alerts
* Telegram notifications
* Deal tracking dashboard

---

# 🛠️ Tech Stack

## Backend

* Python 3.x
* FastAPI
* SQLAlchemy ORM

## Database

* PostgreSQL

## Web Scraping

* Playwright (dynamic scraping)
* BeautifulSoup (HTML parsing)
* Requests (optional)

## Automation

* n8n

## Data Processing

* Custom ETL pipeline
* Python data cleaning logic

## Dev Tools

* pgAdmin
* Uvicorn
* Virtual Environment (venv)

---

# 📁 Project Structure

```
protein-deal-finder/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── create_tables.py
│   │   ├── test_connection.py
│   │   │
│   │   ├── api/
│   │   │   └── routes/
│   │   │       └── products.py
│   │   │
│   │   ├── db/
│   │   │   ├── database.py
│   │   │   └── session.py
│   │   │
│   │   ├── models/
│   │   │   ├── product.py
│   │   │   ├── brand.py
│   │   │   ├── price.py
│   │   │   └── review.py
│   │   │
│   │   ├── services/
│   │   │   ├── ranking_engine.py
│   │   │   ├── product_service.py
│   │   │   └── data_pipeline.py
│   │   │
│   │   └── scrapers/
│   │       ├── amazon_search_scraper.py
│   │       ├── amazon_product_scraper.py
│   │       └── scraper_manager.py
│   │
│   └── requirements.txt
│
├── database/
│   └── seed_data.sql
│
├── n8n/
│   └── workflows/
│
├── frontend/   (future)
│
└── README.md
```

---

# ⚙️ Installation & Setup

## 1. Clone the repository

```
git clone <repo-url>
cd ProteinAI
```

---

## 2. Create virtual environment

```
python -m venv venv
venv\Scripts\activate
```

---

## 3. Install dependencies

```
pip install -r requirements.txt
```

---

## 4. Install Playwright browsers

```
python -m playwright install
```

---

## 5. Setup PostgreSQL

* Create database:

```
protein_deals
```

* Update `.env`:

```
DATABASE_URL=postgresql://postgres:YOUR_PASSWORD@localhost:5432/protein_deals
```

---

## 6. Create tables

```
python create_tables.py
```

---

## 7. Run server

```
uvicorn app.main:app --reload
```

---

## 8. Access API

```
http://127.0.0.1:8000/docs
```

---

# 🧪 Running the Scraper

```
python run_scraper.py
```

This will:

* scrape products
* clean data
* insert into PostgreSQL

---

# 📈 Future Improvements

* 🔁 Real-time price tracking
* 📉 Price drop alerts
* 🤖 AI-based review sentiment analysis
* 📊 Dashboard with charts
* 🔍 Natural language search ("best whey under ₹2000")
* ⚡ Async scraping with queues
* 🧠 ML-based recommendation system

---

# 💡 Why This Project Stands Out

This is not just a scraper — it is a **full data pipeline system**:

✔ Multi-source data aggregation
✔ Intelligent ranking algorithm
✔ Normalized relational database
✔ Automated ETL pipeline
✔ API-first architecture
✔ Scalable scraping system

---

# 👨‍💻 Author

Vaibhav Mohanty

---

# 📜 License

MIT License

---

# ⚠️ Disclaimer

* This project is for **educational purposes only**
* Scraping policies vary per website — ensure compliance with terms of service
