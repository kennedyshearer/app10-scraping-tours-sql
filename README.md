# Web Scraping Tours Monitor

A Python web scraping application that monitors a tours website for new events and sends email notifications when new tours are discovered. The application now uses SQLite database for robust data storage and management.

## 🚀 Features

- **Automated Web Scraping**: Continuously monitors the target website for new tour events
- **Email Notifications**: Sends email alerts when new tours are found
- **SQLite Database Storage**: Stores discovered tours in a SQLite database for reliable data persistence
- **Duplicate Prevention**: Prevents duplicate notifications by checking database records
- **Configurable Extraction**: Uses YAML-based extraction rules for easy customization
- **Database Query Examples**: Includes example scripts for database operations

## 📋 Requirements

- Python 3.6+
- Required packages (install via `pip install -r requirements.txt`):
  - `requests`
  - `selectorlib`
  - `sqlite3` (included with Python standard library)

## 🛠️ Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd app10-scraping-tours-sql
```

2. Install dependencies:
```bash
pip install requests selectorlib
```

3. Configure email settings (optional):
   - Update the email configuration in `main.py` with your own SMTP settings
   - Currently configured to use Gmail SMTP

## 🚀 Usage

Run the application:
```bash
python main.py
```

The application will:
1. Start monitoring the target website every 2 seconds
2. Extract tour information using the YAML configuration
3. Check for new tours by querying the SQLite database
4. Send email notifications for new discoveries
5. Store tour data in `data.db` SQLite database

## 📁 Project Structure

```
app10-scraping-tours-sql/
├── main.py          # Main application logic
├── extract.yaml     # YAML configuration for data extraction
├── example.py       # Database query examples and operations
├── data.db          # SQLite database for storing tours
├── data.txt         # Legacy text file (still maintained for compatibility)
└── README.md        # This file
```

## ⚙️ Configuration

### Email Settings
Update the email configuration in `main.py`:
```python
username = "your-email@gmail.com"
password = "your-app-password"
receiver = "your-email@gmail.com"
```

### Extraction Rules
Modify `extract.yaml` to change what data is extracted:
```yaml
tours:
  css: '#displaytimer'  # CSS selector for tour information
```

## 🔧 How It Works

1. **Scraping**: The application fetches the webpage using requests
2. **Extraction**: Uses selectorlib to extract tour data based on CSS selectors
3. **Database Check**: Queries SQLite database to check if the tour already exists
4. **Storage**: Saves new tours to SQLite database with structured data
5. **Notification**: Sends email alerts for new discoveries
6. **Loop**: Repeats the process every 2 seconds

## 🗄️ Database Schema

Tours are stored in SQLite database (`data.db`) with the following structure:
- **Table**: `events`
- **Columns**: 
  - `band` (TEXT) - Tour/band name
  - `city` (TEXT) - Location/city
  - `date` (TEXT) - Event date

Example data:
```
Lions of the IDE | Clone City | 6.5.2088
Dog | Dog City | 1.26.2044
Cat | Tiger City | 12.17.2022
```

## 📊 Database Operations

Use `example.py` to perform database operations:
- Query events by specific date
- Select specific columns
- Insert new events
- View all stored events

Run example queries:
```bash
python example.py
```

## 🔒 Security Notes

- Email credentials are hardcoded in the script (consider using environment variables for production)
- The application uses a 2-second delay between requests to be respectful to the target server
- SQLite database file (`data.db`) contains all tour data and should be backed up regularly
- Database connection is persistent throughout the application lifecycle 