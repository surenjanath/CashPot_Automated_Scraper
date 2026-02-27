# NLCB Cash Pot Results Web Scraper

This is a Python web scraper designed to fetch NLCB (National Lotteries Control Board) Cash Pot results from [https://www.nlcbplaywhelotto.com/nlcb-cashpot-results/](https://www.nlcbplaywhelotto.com/nlcb-cashpot-results/) and store them in a SQLite database. It utilizes asyncio and aiohttp for asynchronous web scraping and SQLAlchemy for database operations.

## About NLCB Cash Pot

The NLCB Cash Pot is a lottery game in Trinidad and Tobago that draws Monday to Saturday at 7:00 PM. The game involves selecting 5 numbers from 1-20, with various prize tiers based on matching numbers.

## Features

- **Robots.txt Compliant**: Fully respects the website's robots.txt guidelines including crawl delays and visit time restrictions
- **Asynchronous Scraping**: Efficient fetching of Cash Pot results using asyncio and aiohttp
- **BeautifulSoup Parsing**: Robust HTML parsing using BeautifulSoup for reliable data extraction
- **SQLite Database Storage**: Structured storage of historical lottery data using SQLAlchemy ORM
- **Rate Limiting**: Implements proper rate limiting (1 request per 5 seconds) as per robots.txt
- **Visit Time Compliance**: Only scrapes during allowed hours (6 AM - 10 AM) as specified in robots.txt
- **Error Handling**: Comprehensive error handling with retry logic and connection recovery
- **HTML Response Saving**: Saves raw HTML responses for debugging and verification
- **Data Analysis**: Generates comprehensive analysis reports including frequency analysis and statistics
- **Automated Scheduling**: GitHub Actions integration for automated runs (Thursdays and Sundays at 12 AM)

## Requirements

- Python 3.7 or higher
- aiohttp
- pandas
- SQLAlchemy
- beautifulsoup4
- lxml
- html5lib

## Installation

1. Clone the repository.
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. The scraper is pre-configured to scrape NLCB Cash Pot results from the official website.
2. Run the scraper:
   ```bash
   python async_scraper.py
   ```
3. The scraper will:
   - Check if current time is within allowed visiting hours (6 AM - 10 AM)
   - Fetch Cash Pot results with proper rate limiting (1 request per 5 seconds)
   - Parse the HTML data using BeautifulSoup
   - Store results in the SQLite database
   - Generate analysis reports
   - Save HTML responses for debugging

## Robots.txt Compliance

This scraper strictly follows the website's robots.txt guidelines:

- **Crawl-delay: 5** - 5-second delay between requests
- **Request-rate: 1/5** - Maximum 1 request per 5 seconds  
- **Visit-time: 0600-1000** - Only visits during 6 AM to 10 AM
- **User-agent identification** - Proper bot identification in headers

The scraper includes built-in checks to ensure compliance and will warn users if running outside allowed hours.

## Configuration

- **Database Settings**: Customize database name and location by modifying `Database_Name` and `Location` variables
- **Date Range**: Adjust scraping range by modifying `YEAR` and `MONTH` variables (currently set to 2000-2024)
- **Rate Limiting**: Built-in rate limiting ensures compliance with robots.txt (1 request per 5 seconds)
- **Visit Time**: Automatic time checking ensures scraping only during allowed hours (6 AM - 10 AM)

## Data Structure

The scraper extracts the following data for each Cash Pot draw:

- **Draw Date**: Date of the draw
- **Draw Number**: Unique draw identifier
- **Numbers**: The 5 winning numbers (1-20)
- **Multiplier**: Multiplier value for the draw
- **Jackpot**: Jackpot amount for the draw
- **Wins**: Number of winners for the draw

## Output Files

- **Database**: `Database/Lotto_Results_Database.db` - SQLite database with all scraped data
- **HTML Reports**: `analysis_report.html` - Generated analysis report
- **Debug Files**: `response_{month}_{year}.html` - Raw HTML responses for debugging

## Contributing

Contributions are welcome! If you find any bugs or have suggestions for improvement, please open an issue or submit a pull request.

## GitHub Actions

This repository includes a GitHub Actions workflow that automatically performs analysis on the scraped Cash Pot results. The workflow is triggered on each push to the `main` branch and runs every Thursday and Sunday at 12 AM. It analyzes the data and generates comprehensive reports.

## Technical Details

### Scraping Method
- Uses POST requests with form data to search for specific month/year combinations
- Implements BeautifulSoup for robust HTML parsing
- Handles dynamic content and table structures
- Saves raw HTML responses for debugging and verification

### Error Handling
- Retry logic for connection failures (3 attempts)
- Graceful handling of parsing errors
- Comprehensive logging for debugging
- Rate limiting to prevent server overload

### Database Schema
- Uses SQLAlchemy ORM for data management
- Primary key on DrawDate for data integrity
- Automatic timestamp tracking for data freshness
- Unique ID generation for each record

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- This project was inspired by the need to automate the collection of NLCB Cash Pot results for analysis and historical record-keeping.
- Special thanks to the developers of aiohttp, pandas, SQLAlchemy, and BeautifulSoup for their excellent libraries.
- Respectful web scraping practices following robots.txt guidelines and ethical data collection standards.


## Analysis Results

<!--START_SECTION:analysis-->
{{analysis_placeholder}}
<h1>Cashpot Analysis Report</h1>
            <div class="basic-analysis">
                <h2>Basic Analysis:</h2>
                <p>Total number of draws: 52<br></p>
            </div>
            <div class="average-jackpot">
                <h2>Average Jackpot Amount:</h2>
                <p>$0.00</p>
            </div>
            <div class="most-common-numbers">
                <h3>Top 5 Most Common Numbers Drawn:</h3>
                <table>
                    <tr>
                        <th>Number</th>
                        <th>Frequency</th>
                    </tr>
                    <tr><td>13</td><td>22 times
</td></tr><tr><td>9</td><td>21 times
</td></tr><tr><td>19</td><td>17 times
</td></tr><tr><td>11</td><td>16 times
</td></tr><tr><td>2</td><td>14 times
</td></tr>
                </table>
            </div>
            <div class="additional-analysis">
                <h2>Latest NLCB CashPot Results:</h2>
                <div class="draw-date">
                    <h3>Draw Date:</h3>
                    <p>26 February 2026</p>
                </div>
                <div class="numbers-drawn">
                    <h3>Numbers Drawn:</h3>
                    <p>6, 11, 16, 17, 18</p>
                </div>
                <br/>
                <h3>Other Information:</h3>
                <p>Power Ball: 1<br>Multiplier: 2<br>Jackpot: 0<br>Wins: -1<br></p>



        