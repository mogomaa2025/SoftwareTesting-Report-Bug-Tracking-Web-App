# Comprehensive Software Testing Report & Bug Tracking Web App

This is a full-stack web application designed to manage software test cases and bug reports efficiently. It features a dynamic frontend built with HTML, Tailwind CSS, and JavaScript for an interactive user experience, backed by a Flask API for data persistence, export functionalities, and dynamic report generation.

## Features

### Frontend (User Interface)

-   **Dashboard Overview**: A summary dashboard displaying key metrics like overall pass rate, total test cases, failed tests, total bugs, and critical bugs, with breakdowns by platform (CRM/Web).
-   **Tabbed Navigation**: Organizes content into "Summary", "Test Cases", and "Bug Reports" for easy navigation.
-   **Search Functionality**: Allows users to quickly find specific test cases or bug reports.
-   **Data Management**:
    -   **Add/Edit/Delete**: Dynamically add new test cases or bug reports, and edit existing entries directly within the interface.
    -   **Move Items**: Reorder test cases and bug reports within their respective lists.
    -   **Import/Export CSV**: Import data from CSV files and export current data to CSV format.
    -   **Bulk Save**: A single button to save all changes back to the backend.
-   **Test Case Specifics**:
    -   **Pagination**: Efficiently browse through large numbers of test cases.
    -   **Status and Priority/Severity Tracking**: Assign status (e.g., PASS, FAIL, To Be Executed) and priority levels (Low, Medium, High, Critical).
    -   **Dynamic Styling**: Visual cues for test case status and priority/severity.
-   **Bug Report Specifics**:
    -   **Evidence Gallery**: Attach images and videos (including Google Drive links) as evidence for bug reports, with zoom functionality for images.
    -   **Related Test Cases**: Link bug reports to specific test cases.
    -   **ID Validation**: Enforces ID formatting (e.g., `CRM-TC001`, `WEB-BUG001`) and checks for duplicates.
    -   **Platform Auto-detection**: Automatically suggests the platform for a bug report based on its related test case.
-   **Responsive Design**: Optimized for various screen sizes using Tailwind CSS.

### Backend (Flask API)

-   **Data Persistence**: Stores and retrieves application data from a `.csv` file (`data/.test.csv`).
-   **XLSX Export**: Exports all data to a meticulously styled Excel (`.xlsx`) file, comprising three sheets:
    -   **Test Cases**: Formatted test cases with colored status (Pass/Fail) and priority.
    -   **Bug Reports**: Formatted bug reports with colored status (Open/In Progress/Closed) and priority, including clickable hyperlinks for attached evidence (images/videos).
    -   **Analysis**: Provides summary statistics, test case pass/fail rates, bug distribution by priority, and platform breakdown, all dynamically generated.
-   **Dynamic Styling in XLSX**: Applies conditional formatting, cell coloring (based on priority/status), and auto-fits columns/rows for readability, especially accommodating evidence links and descriptions.
-   **File Serving**: Serves static HTML and CSV data.

## Setup and Installation

To get this application up and running locally, follow these steps:

1.  **Clone the repository**:
    ```bash
    git clone <repository_url>
    cd bugreport-full-stack
    ```

2.  **Create a Python Virtual Environment** (recommended):
    ```bash
    python -m venv venv
    ```

3.  **Activate the Virtual Environment**:
    -   **Windows**:
        ```bash
        .\venv\Scripts\activate
        ```
    -   **macOS/Linux**:
        ```bash
        source venv/bin/activate
        ```

4.  **Install Dependencies**:
    The application uses `Flask`, `pandas`, and `openpyxl`. Install them using pip:
    ```bash
    pip install Flask pandas openpyxl
    ```

5.  **Run the Flask Application**:
    ```bash
    python flask_app.py
    ```
    The application will typically run on `http://127.0.0.1:5000/`.

6.  **Access the Web Interface**:
    Open your web browser and navigate to `http://127.0.0.1:5000/`.

## Data Structure (`data/.test.csv`)

The application uses a CSV file (`data/.test.csv`) to store all test cases and bug reports. The expected columns are:

-   `Type`: (`Test Case` or `Bug Report`)
-   `Platform`: (`Client` or `CRM`)
-   `Section`: (e.g., `HOMEPAGE`, `NAVIGATION Bar`)
-   `ID`: Unique identifier for the test case/bug (e.g., `WEB-TC001`, `CRM-BUG001`)
-   `Title/Objective`: A brief description of the test or bug.
-   `Test Steps`: Detailed steps to reproduce for test cases.
-   `Test Data`: Any data used during the test.
-   `Expected Result`: The anticipated outcome of the test.
-   `Actual Result`: The actual outcome observed.
-   `Priority/Severity`: (e.g., `None`, `Low`, `Medium`, `High`, `Critical`)
-   `Status`: (e.g., `PASS`, `FAIL`, `To Be Executed` for Test Cases; `Open`, `In Progress`, `Closed` for Bug Reports)
-   `Description`: Detailed description for bug reports.
-   `Evidence`: JSON array of objects `[{"url": "...", "type": "image"}]` for image/video links related to a bug.
-   `Related Test Case`: The ID of a test case linked to a bug report.

## Usage

1.  **View Data**: Upon loading the application, you'll see a summary dashboard. Navigate between "Test Cases" and "Bug Reports" tabs to view your data.
2.  **Add New Entries**: Use the "Add Test Case" or "Add Bug Report" buttons to create new entries. IDs are automatically generated based on platform and incremented.
3.  **Edit Data**: Click directly on most table cells or card fields to edit their content. Dropdowns are provided for `Platform`, `Priority/Severity`, and `Status`.
4.  **Manage Evidence**: For bug reports, use the "Add Evidence" button to attach image or video URLs. Images can be zoomed in.
5.  **Save Changes**: Click the "Save Changes" button to persist all modifications to the `data/.test.csv` file.
6.  **Export to XLSX**: Use the "Export as XLSX" button to download a comprehensive Excel report with styled sheets.
7.  **Import Data**: Use "Import Test Cases" or "Import Bug Reports" to load data from a CSV file.

## Screenshot Examples

_(Note: Replace these placeholders with actual screenshots of your application's UI)_

### Summary Dashboard
![Summary Dashboard Placeholder](https://via.placeholder.com/800x450?text=Summary+Dashboard+Screenshot)
*An overview of key metrics and statistics.*

### Test Cases View
![Test Cases View Placeholder](https://via.placeholder.com/800x450?text=Test+Cases+View+Screenshot)
*Table view of test cases with inline editing and status indicators.*

### Bug Reports View with Evidence
![Bug Reports View Placeholder](https://via.placeholder.com/800x450?text=Bug+Reports+View+with+Evidence+Screenshot)
*Bug report cards showing title, description, priority, and attached evidence.*

### XLSX Export Example
![XLSX Export Example Placeholder](https://via.placeholder.com/800x450?text=XLSX+Export+Screenshot)
*A sample of the generated Excel report with colored cells and formatted data.*
