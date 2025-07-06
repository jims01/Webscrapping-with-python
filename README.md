# Webscrapping-with-python
---
## Project Insight
---
This project involves webscrapping the list of Largest companies in the United Kingdom using Python (BeautifulSoup), according to [Wiki](https://www.wikipedia.org/) and saving in CSV format

### Website scrapped
For the Website Scrapped [Click here](https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_Kingdom
)

### Webscrapping 

```BeautifulSoup
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_Kingdom'
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')
for row in Column_data[1:]:
    row_data = row.find_all('td')
    individual_row_data = [data.text.strip() for data in row_data]    
    length = len(df)
    df.loc[length] = individual_row_data
df.to_csv(r'C:\Users\dubem\Desktop\Jupyter_Notebook\companies.csv', index = False)
```

### Result 
Companies.csv
