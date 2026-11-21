# Web Scraping with Python: Largest UK Companies

A Python scraper that collects the table of the largest companies in the United Kingdom from Wikipedia using Beautiful Soup, and saves it as a CSV file ready for analysis.

**Source:** [List of largest companies in the United Kingdom (Wikipedia)](https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_Kingdom)

## What it collects
The table's columns: [list them, e.g. rank, company name, industry, revenue, profit, employees].

**Result:** `companies.csv` with [number] rows.

## Tools
Python · requests · Beautiful Soup (`bs4`) · pandas

## How it works
1. **Request the page** with `requests` and parse the HTML with Beautiful Soup.
2. **Find the table** and read its column headings to create an empty DataFrame.
3. **Loop through the table rows,** skipping the header row, take the text from each cell and strip the whitespace.
4. **Append each row** to the DataFrame.
5. **Save** the DataFrame to `companies.csv`.

```python
import requests
import pandas as pd
from bs4 import BeautifulSoup

url = "https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_Kingdom"
page = requests.get(url)
soup = BeautifulSoup(page.text, "html.parser")

# [Find the table and its rows; create df with the table's column headings.
#  Paste your own lines for table, Column_data and df here.]

for row in Column_data[1:]:
    row_data = row.find_all("td")
    individual_row_data = [data.text.strip() for data in row_data]
    df.loc[len(df)] = individual_row_data

df.to_csv("companies.csv", index=False)
```

## Notes
- Wikipedia text is available under the Creative Commons Attribution-ShareAlike licence, and the data here comes from that page.
- The table is a snapshot, so figures reflect the date of the Wikipedia edition scraped [add the date you ran it].
- The scraper depends on the page's current layout and will break if the table structure changes.
