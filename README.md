# Process Mining Analysis of a Loan Application Process

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

This repository contains a process mining analysis of a loan application process, based on the **BPI Challenge 2012** event log. The primary goal is to dissect the process flow, identify inefficiencies, bottlenecks, and rework loops using Python and the `pm4py` library.

The complete findings and business recommendations are detailed in the accompanying PDF report. The Jupyter Notebook provides the full technical implementation of the analysis.

## Analysis Workflow in the Notebook

The `bpi_2012_loan_analysis.ipynb` notebook follows a systematic approach to derive insights from the raw event data:

1.  **Data Loading and Exploration**: The `financial_log.xes` event log is loaded, and initial statistics such as the number of cases, events, and variants are computed.
2.  **Data Cleaning and Preprocessing**:
    -   Incomplete cases (those without a definitive end state) are filtered out to ensure a clean end-to-end analysis.
    -   Redundant activities (e.g., `A_PARTLYSUBMITTED`) that represent system noise are removed.
3.  **Process Segmentation**: The cleaned log is segmented into three distinct sub-logs based on the final case outcome: `Approved`, `Declined`, and `Cancelled`.
4.  **Comparative KPI Analysis**: Key Performance Indicators (KPIs) are calculated for each segment, including:
    -   Average case duration
    -   Average requested loan amount
    -   Average number of manual work items (a proxy for effort and rework).
5.  **Directly-Follows Graph (DFG) Analysis**: The DFG is used to quantitatively identify the most frequent transitions and self-loops (rework) within each segment, revealing the core process inefficiencies.

## Repository Structure
```
.
├── data/
│ └── financial_log.xes.gz
├── bpi_2012_loan_analysis.ipynb
├── LICENSE
├── requirements.txt
└── README.md
```


## 🛠️ Technology Stack

-   **Python 3.8+**
-   **pm4py**: The primary library for process mining analysis.
-   **pandas**: For data manipulation and KPI aggregation.
-   **Matplotlib & Seaborn**: For data visualization.
-   **Jupyter Notebook**: As the interactive development environment.

## 🚀 Setup and Installation

Follow these steps to set up the environment and run the analysis.

1.  **Clone the repository:**
    ```bash
    git clone <your-repository-url>
    cd <repository-folder>
    ```

2.  **Create and activate a virtual environment (recommended):**

    *   On macOS/Linux:
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```

    *   On Windows:
        ```bash
        python -m venv venv
        .\venv\Scripts\activate
        ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

## ▶️ Running the Analysis

1.  Ensure your virtual environment is activated.
2.  Start the Jupyter Notebook server:
    ```bash
    jupyter notebook
    ```
3.  In the browser window that opens, navigate to and open `bpi_2012_loan_analysis.ipynb`.
4.  You can run the cells sequentially to reproduce the entire analysis.

## File Descriptions

-   `bpi_2012_loan_analysis.ipynb`: The core of the project, containing all Python code for the process mining analysis.
-   `data/financial_log.xes`: The raw event log data from the BPI Challenge 2012.
-   `report_pdf.pdf`: A formal report summarizing the key findings, data visualizations, and business recommendations derived from the analysis.
-   `Scenario13.06.2025.pdf`: The original case study description and assignment requirements.
-   `requirements.txt`: A list of all Python packages required to run the notebook.
