# 🌟 python-web-scraping
Robust Python web scraper that builds a data pipeline to extract GitHub trending repositories. Parses HTML via Requests/BeautifulSoup and engineers features like star counts into a Pandas DataFrame.

## Project Overview

**A robust Python-based web scraping and data pipelining project that systematically extracts and structures trending repository data from GitHub.** Utilizing **Requests** and **BeautifulSoup**, the pipeline collects, parses, and cleans repository names, user profiles, and star counts, organizing the output into a **Pandas DataFrame** for analysis. Demonstrates proficiency in multi-stage data acquisition and feature engineering from unstructured HTML data. 

## 1. ❓ Problem Statement

The goal of this project is to automate the acquisition of structured data from GitHub's trending topics section. Manually collecting and tracking the top repositories, their metadata, and performance metrics (like star counts) is time-consuming and inefficient. This solution provides an automated, scalable pipeline to transform the unstructured HTML content into a clean, analytical dataset.

---

## 💻 Technical Stack & Prerequisites

* **Language:** Python 3.x
* **Core Libraries:**
    * `requests` (For making HTTP requests)
    * `BeautifulSoup4` (For parsing HTML content)
    * `pandas` (For structuring and manipulating data)
* **Execution Environment:** Google Colab / Jupyter Notebook

### Setup Instructions

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/YourUsername/python-web-scraping.git](https://github.com/YourUsername/python-web-scraping.git)
    ```
2.  **Install Dependencies:**
    ```bash
    pip install requests beautifulsoup4 pandas
    ```

---

## 2. 🚀 Project Logic and Flow

The scraping process is executed in a sequential, two-phase approach to ensure data completeness and structure. The core logic is structured to first identify broad topics, then drill down into the specific details of the repositories within each topic.

### Phase I: High-Level Topic Extraction (HTTP Responses)

This phase targets the main GitHub topics index page to establish the foundation of the dataset.

* **3.1 Extracting the topics being discussed:** Retrieves the main title for each trending category (e.g., 'Data Science', 'Machine Learning').
* **3.2 Extracting the topics descriptions:** Captures the brief summary associated with each topic.
* **3.3 Extracting the topic links:** Collects the unique URL for each topic, which is used to initiate Phase II.

### Data Structuring (Creating a Pandas DataFrame)

* **4. Creating a Pandas DataFrame:** The high-level topic data is immediately structured into a DataFrame to serve as a navigable index for the next phase.

### Phase II: Detailed Repository Data Extraction

This phase iterates through the URLs collected in Phase I to gather specific information about the individual trending repositories within each topic.

* **5. Getting Information Out of a Single Page:** The script navigates to each topic-specific page.
* **5.1 Extracting the Repo tags:** Identifies the main HTML elements containing repository information.
* **5.2-5.5 Feature Engineering & Extraction:**
    * Extracts usernames and repository names from the anchor tags.
    * Extracts and cleans the **Star Counts** (a critical performance metric).
    * Constructs the full, functional repository URL by string concatenation.

---

## 6. 📊 Results and Output

The final deliverable is a clean, analytical dataset containing all trending repository information.

| Feature | Description | Example |
| :--- | :--- | :--- |
| `topic` | The broad category of the repository. | `machine-learning` |
| `username` | The GitHub user who owns the repository. | `tensorflow` |
| `repo_name` | The name of the project. | `models` |
| `stars` | The total number of stars (as of the scrape). | `50201` |
| `repo_url` | Direct link to the repository. | `https://github.com/tensorflow/models` |



---

## 7. 🗣 Technical Comments

* **HTML Parsing:** The structure of GitHub's page is relatively static, allowing for reliable extraction using standard **CSS selectors** and `BeautifulSoup` methods.
* **Robustness:** The use of separate functions for URL concatenation and string cleaning ensures that the scraping logic is modular and easier to debug if GitHub's HTML structure changes.
* **Rate Limiting:** This script relies on sequential HTTP requests and does not use GitHub's API, which is a consideration for large-scale, high-frequency scraping.


## 🚀 NEXT ACTIVITY

This activity focuses on executing the multi-stage data acquisition logic to generate structured, topic-specific datasets.

### Phase 1: Topic Index Acquisition

* **Target:** `https://github.com/topics` (The primary topic index page).
* **Action:** Programmatically get the list of all available topic names (e.g., "3D", "Python") and their corresponding URLs (e.g., `https://github.com/topics/3d`).

### Phase 2: Repository Data Extraction & File Generation

* **Process:** The script will loop through the list of topic URLs fetched in Phase 1.
* **Extraction Logic:** For each topic page (e.g., `https://github.com/topics/3d`), the scraper will:
    * Fetch the data from the individual topic page.
    * Extract the following repository information (repo info):
        * Repository Creator (Username)
        * Repository Name
        * Star Counts
* **Output:** For each topic, a dedicated CSV file will be generated, containing the structured list of top repositories for that topic.

---
