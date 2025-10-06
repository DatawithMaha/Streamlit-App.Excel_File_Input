# Excel → Snowflake Loader App 📊❄️

A Streamlit app that lets you drag and drop Excel files and automatically loads all sheets into Snowflake as tables — with schema normalization, smart renaming, and live previews.

## 💡 What it Does  
- Upload an Excel file (`.xlsx`) via drag-and-drop or file picker  
- Automatically detects all sheets in the workbook  
- Converts each sheet into a Snowflake table, based on a defined mapping or fallback logic  
- Normalizes certain headers (e.g., renames `State` to `State/Province`)  
- Handles type conversions (e.g., dates, postal codes)  
- Replaces existing tables with new data  
- Displays a preview of the uploaded tables directly in the browser (first 10 rows)
   
## 🛠️ Technologies Used
- Python
- Streamlit – for the web app interface
- Pandas – for data manipulation
- openpyxl – for reading Excel files
- Snowflake Snowpark for Python — Data loading and querying

## 📦 Sheet → Table Mapping
- This app automatically maps Excel sheets to Snowflake tables using the following logic:

   TABLE_MAP = {
    "Orders":  "SUPERSTORE_FABRIC_ORDERS",
    "People":  "SUPERSTORE_FABRIC_PEOPLE",
    "Returns": "SUPERSTORE_FABRIC_RETURNS",
}
- Sheets not listed in TABLE_MAP will fallback to a generated name like:
SUPERSTORE_FABRIC_<SANITIZED_SHEET_NAME>

## 🔍 Schema Normalization Logic
- State → State/Province
- Country → Country/Region
- Converts Postal Code to string
- Converts Order Date and Ship Date to actual dates

## 🚀 Future Improvements
- Add schema validation and error reporting
- Let users select specific sheets before upload
- Support multiple databases/schemas dynamically
- Export schema logs or upload report

## 🧠 Notes
- Existing tables with the same name will be replaced
- Only .xlsx files are currently supported
