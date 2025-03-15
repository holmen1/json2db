# JSON-SQL-JSON Transformation Tool

A simple Python utility that demonstrates transforming nested JSON data to SQL tables and back, allowing data manipulation in between.

## Features

- Convert nested JSON data to tabular pandas DataFrame
- Store data in SQLite database
- Update values using SQL queries
- Convert modified data back to the original nested JSON structure

## Technologies

- Python 3.x
- pandas
- SQLAlchemy
- SQLite

## Usage

The project demonstrates the workflow in a Jupyter notebook:

1. Read JSON data from a file
2. Flatten the nested structure into a pandas DataFrame
3. Store the DataFrame in an SQLite database
4. Modify data using SQL queries
5. Convert the modified data back to the original JSON structure

## Installation

1. Clone the repository
   ```bash
   git clone https://github.com/holmen1/json-sql-json.git
   cd json-sql-json
   ```

2. Create and activate virtual environment
   ```bash
   # Create virtual environment
   python -m venv venv
   
   # Activate virtual environment
   # On macOS/Linux:
   source venv/bin/activate
   # On Windows:
   # venv\Scripts\activate
   ```

3. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```


## File Structure

- `demo.ipynb` - Jupyter notebook with the full demonstration
- `Data/assumptions.json` - Original JSON data
- `Data/assumptions_updated.json` - Modified JSON data after processing
- `.gitignore` - Configured to ignore database files and common Python artifacts

## Example

The workflow allows you to modify values in a database and preserve the nested structure when converting back to JSON:

```python
# Read data, make modifications in SQL, then rebuild the JSON structure
with engine.connect() as conn:
    conn.execute(text("""
        UPDATE assumptions
        SET Value = 10.0
        WHERE Risk = 'HR' AND Type = 'Investment'
    """))
    conn.commit()
```