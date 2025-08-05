# Web Scraping Tours Monitor

A Python web scraping application that monitors a tours website for new events and sends email notifications when new tours are discovered.

## 🚀 Features

- **Automated Web Scraping**: Continuously monitors the target website for new tour events
- **Email Notifications**: Sends email alerts when new tours are found
- **Duplicate Prevention**: Prevents duplicate notifications by tracking previously discovered tours
- **Data Persistence**: Stores discovered tours in a local text file
- **Configurable Extraction**: Uses YAML-based extraction rules for easy customization

## 📋 Requirements

- Python 3.6+
- Required packages (install via `pip install -r requirements.txt`):
  - `requests`
  - `selectorlib`

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
3. Check for new tours and avoid duplicates
4. Send email notifications for new discoveries
5. Store tour data in `data.txt`

## 📁 Project Structure

```
app10-scraping-tours-sql/
├── main.py          # Main application logic
├── extract.yaml     # YAML configuration for data extraction
├── data.txt         # Storage file for discovered tours
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
3. **Validation**: Checks if the extracted data represents a new tour
4. **Storage**: Saves new tours to `data.txt`
5. **Notification**: Sends email alerts for new discoveries
6. **Loop**: Repeats the process every 2 seconds

## 📊 Data Format

Tours are stored in `data.txt` with the format:
```
Tour Name, Location, Date
```

Example:
```
Lions of the IDE, Clone City, 6.5.2088
```

## 🔒 Security Notes

- Email credentials are hardcoded in the script (consider using environment variables for production)
- The application uses a 2-second delay between requests to be respectful to the target server 