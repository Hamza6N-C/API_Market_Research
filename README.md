# API_Market_Research - Dockerized Product Data Project

A portable, **Docker-based** system for **pulling daily product data** from an external API, storing it in **MySQL**, and offering an **interactive Streamlit dashboard** for visualization and exploration.

---

## Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Usage](#installation--usage)
- [Environment Variables](#environment-variables)
- [Screenshots](#screenshots-optional)
- [Future Improvements](#future-improvements)
- [License](#license)

---

## Features

- **Daily Data Ingestion**  
  - A Python script (e.g., `final_dev.py`) calls an external API to fetch product data, performs cleaning, and saves the results into MySQL.

- **MySQL Database Container**  
  - All data is managed via a Dockerized MySQL 8.0 service, with volumes for persistent storage.  
  - Ensures reliable, consistent data between runs.

- **Streamlit Dashboard**  
  - Filters: Easily narrow down data by categories, part numbers, manufacturers, distributors, etc.  
  - Aggregated charts (bar or line) for insights like average prices by distributor.  
  - Single-part view showing product images, buy links, and time-based price charts.  
  - Consistent color mapping for distributors across charts.

- **Docker Compose Orchestration**  
  - One command (`docker-compose up --build`) starts the entire system on any machine with Docker.  
  - Makes the environment fully **portable** and **reproducible**.

---

## Project Structure

```plaintext
my-docker-product-project/
├── docker-compose.yml        # Defines services (MySQL, Streamlit, etc.)
├── .env                      # Environment variables for MySQL & scripts
├── requirements.txt          # Python dependencies (pandas, streamlit, etc.)
├── final_dev.py              # Daily data ingestion script
├── streamlit_app.py          # Main Streamlit dashboard code
├── Dockerfile                # For building Python environment
├── README.md                 # This README
└── ...                       # Other scripts or data files as needed
```

### Key Files

- **`final_dev.py`**:  
  Pulls data from an external API, cleans it, and inserts into MySQL daily.

- **`streamlit_app.py`**:  
  Runs the Streamlit UI. Users can apply filters, view tables, and explore charts.

---

## Prerequisites

1. **Docker** (v20+ recommended).  
2. **Docker Compose** (v2+ or the Docker plugin).  
3. **(Optional) Python** if you want to run scripts outside Docker or debug locally.

---

## Installation & Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/<YourUsername>/my-docker-product-project.git
   cd my-docker-product-project
   ```

2. **Edit the `.env` file**:
   ```bash
   MYSQL_ROOT_PASSWORD=my-secret-pw
   MYSQL_USER=myuser
   MYSQL_PASSWORD=mypassword
   MYSQL_DATABASE=productcatalog
   ```
   Update passwords, database names, or API keys if needed.

3. **Build & Run**:
   ```bash
   docker-compose up --build
   ```
   This will:
   - Build images for MySQL and the Python environment.
   - Start MySQL, run your ingestion script (if configured), and launch the Streamlit dashboard.

4. **Access the dashboard**:
   - Open your browser to [http://localhost:8501](http://localhost:8501).  
   - Use the sidebar filters to slice/dice data.  
   - View average prices, see single-part details, or click "Buy Now" links (if available).

5. **Stopping**:
   ```bash
   docker-compose down
   ```
   Containers will stop and be removed. Data persists if you used volumes.

---

## Environment Variables

In `.env`:

```bash
MYSQL_ROOT_PASSWORD=my-secret-pw
MYSQL_USER=myuser
MYSQL_PASSWORD=mypassword
MYSQL_DATABASE=productcatalog
# (Optional) API keys for the ingestion script
# API_KEYS=key1,key2,...
```

Ensure `docker-compose.yml` references these variables (e.g., `MYSQL_USER: ${MYSQL_USER}`).

---

## Screenshots

### Main Dashboard
![image](https://github.com/user-attachments/assets/4fb9cbaa-c5a1-40c7-95bf-cff6821afb70)
![image](https://github.com/user-attachments/assets/78d0e804-09fc-4acb-9b8c-c7855a07b0da)

### Distributor vs. Unit Price
![image](https://github.com/user-attachments/assets/068966b4-b50a-42fa-8be6-1681b2b4235a)
![image](https://github.com/user-attachments/assets/2135b2b8-f942-4f0e-a531-2d0da667cbc3)

### Single-Part View
![image](https://github.com/user-attachments/assets/a9ad03d5-ebbb-4d6a-b33a-bc8c5035bb0f)

---

## Future Improvements

- **User Authentication**: Add security or login before accessing the dashboard.
- **Advanced Analytics**: Forecast or anomaly detection on pricing data.
- **Monitoring & Logging**: Track ingestion script runs for errors or timeouts.
- **Cloud Deployment**: Host on AWS, GCP, or similar with container orchestration for scaling.

---

## License

```plaintext
MIT License

Copyright (c) 2025 Hamza BEN HADDOU - Tugberk Erdogmus

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

Enjoy using this Dockerized Product Data Project! Happy coding!

