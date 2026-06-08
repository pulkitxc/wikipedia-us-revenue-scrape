# wikipedia-us-revenue-scrape
A streamlined Python pipeline that handles raw data ingestion by bypassing default server blocks, then extracts, cleans, and structures the Top 100 US Companies data from Wikipedia into a ready-to-use CSV file.

# Wikipedia US Corporate Revenue Scraper 

Most tutorials teach you how to write slow code that freezes your machine the second you scale it. I built this lightweight Python pipeline to pull the top 100 US companies by revenue from Wikipedia, clean the raw HTML junk, and dump it straight into a structured CSV without the lag.

## 🎛️ The Setup
* **Requests:** Used custom identity headers to avoid getting instant-slapped by Wikipedia's firewall blocks.
* **BeautifulSoup:** Ripped through the messy DOM tree using `.find()` and `.find_all()` to target the exact `.wikitable`.
* **Pandas:** Handled the heavy transformation logic to convert raw data fields into a clean matrix.

## ⚡ Bypassing the Beginner Bottleneck
If you watch standard tutorials, you'll see people adding data row-by-row inside a loop using `df.loc[len(df)]`. That works fine for a tiny 5-row sample, but it's a terrible production habit. 

Every time you run that, Pandas has to rebuild the entire DataFrame in your RAM from scratch. If you try scaling that to thousands of rows, your computer will straight up choke on memory allocation overhead.

**How I optimized it:** I set up an automated list-append workflow. The script catches all incoming string arrays inside lightweight native Python lists first, quietly executing a single-hit compilation into Pandas at the finish line. It handles the entire dataset in less than 3 seconds.

## 📂 Repository Contents
* `us_revenue_scraper.ipynb` - The documented Jupyter Notebook with the live cells.
* `companies.csv` - The final, clean dataset exported with index counters turned off.
