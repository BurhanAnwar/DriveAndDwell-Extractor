# DriveAndDwell Extractor

## Overview
The **DriveAndDwell Extractor** is a web scraping project that collects data from three platforms: **PakWheels** (a Pakistani car marketplace), **Saudi Sale** (a Saudi Arabian car sales platform), and **Ekar Plus** (a real estate platform). The project is implemented in a Jupyter Notebook (`DriveAndDwell_Extractor.ipynb`) using Python, leveraging libraries like `requests`, `BeautifulSoup`, and `selenium` to scrape and process data for automotive and real estate market analysis.

## Repository Contents
- **DriveAndDwell_Extractor.ipynb**: Jupyter Notebook containing the web scraping implementation for PakWheels, Saudi Sale, and Ekar Plus.
- **README.md**: This file, providing an overview, setup instructions, and project details.

## Prerequisites
To run the notebook, ensure the following dependencies are installed:
- Python 3.10+
- `requests`
- `beautifulsoup4`
- `selenium`
- `chromium-chromedriver` (for Selenium WebDriver)
- Jupyter Notebook

Install the required packages using:
```bash
pip install requests beautifulsoup4 selenium jupyter
```
## Project Components
The DriveAndDwell_Extractor.ipynb notebook includes three main sections:

1- **PakWheels (Car Marketplace)**
- `Objective:` Scrape seller contact information for a specific car listing.
- `Implementation:`
* Uses requests to send a GET request to the PakWheels login page and a specific listing's seller contact info page (https://www.pakwheels.com/used-cars/8871744/seller_contact_info).
* Handles cookies to maintain session authentication.
- `Outputs:` Seller details (name, phone, WhatsApp, etc.) in JSON format.

- `Example Output:`
```bash
{
    "name": "Rolling Wheels",
    "phone": "03017557451",
    "phone_1": "03001557451",
    "whatsapp": "03017557451",
    "text_message": "03017557451",
    "error": "",
    "mobile_verified": true
}
```

2- **Ekar Plus (Real Estate)**
- `Objective:` Extract real estate listing details for a specific property.
- `Implementation:`
* Uses requests and BeautifulSoup to scrape a property listing page (https://ekarplus.com/realEstate-card.xhtml?id=39812).
* Extracts description, location, agent information, and additional details (e.g., price, space, rooms) from specific HTML elements.
* Stores data in a dictionary for structured output.
  
- `Example Output:`
```bash
  Description: ['شقة للبيع ب بعبدا مساحة ١٤٠ متر / سند اخضر / موقف خاص / اطلالة عالبحر / ديكور كتير رايق / سعر لقطة']
Location: ['location: بعبدا/ بعبدا/ جبل لبنان']
Person_Info: ['agenthassan ibrahimWhatsApp 96170032352']
Price($): 166,000
Space(m²): 140
Rooms: 2
Bathrooms: 2
Floor: THIRD
Car Park: 1
```

3- **Saudi Sale (Car Sales)**
- `Objective:` Scrape car listings from the Saudi Sale website.
- `Implementation:`
* Uses requests and BeautifulSoup to scrape car listing links from the main page (https://cars.saudisale.com/).
* Iterates through each listing to extract car information (name, showroom, listing number, location, insurance) and detailed specifications (e.g., manufacturer, model, year, price).
* Stores data in a list of dictionaries for each car listing.
- `Example Output:`
```bash
Name: فيات 500
showroom: معرض يو كارز للسيارات
Listing Number: 211243
Location: السعودية ,الرياض ,الرياض ,الصالات
Insurance: لا
المصنع: فيات
الفئة: 500
الموديل: عادي
نوع السيارة: سبورت \ كوبيه
السنة: 2021
نوع القير: اتوماتيك
المسافات المقطوعه: 13,000 كم
تحت الضمان: لا
السعر: غير محدد
```
## Expected Outcomes
- `PakWheels:` Seller contact details for a specified car listing.
- `Ekar Plus:` Structured real estate listing data, including price, location, and property features.
- `Saudi Sale:` A comprehensive list of car listings with detailed specifications and pricing.
- Data Use: The scraped data can be used for market analysis, price comparison, or building datasets for automotive and real estate research.
## Limitations and Notes
- Authentication: The PakWheels scraper uses `hardcoded credentials (email and password)`, which may not work without valid user authentication. Update with valid credentials or implement a login flow using Selenium.
- Rate Limiting: Websites may `block requests` due to excessive scraping. Implement delays or proxies if needed.
- Data Duplication: The Saudi Sale scraper outputs duplicate entries due to a loop printing issue. Modify the code to print each listing only once by moving the print loop outside the scraping loop.
- Ethical Scraping: Ensure compliance with the terms of service of PakWheels, Saudi Sale, and Ekar Plus. Avoid overloading servers with requests.
## Future Improvements
- Deduplication: Fix the Saudi Sale scraper to avoid duplicate outputs by restructuring the print loop.
- Dynamic Authentication: Implement Selenium-based login for PakWheels to handle authentication dynamically.
- Data Storage: Save scraped data to CSV/JSON files for easier analysis.
- Error Handling: Add robust error handling for failed requests or missing HTML elements.
- Visualization: Add plots (e.g., using `matplotlib` or `seaborn`) to compare car prices or property features across platforms.
- Expanded Scope: Scrape additional pages or listings from each platform for a larger dataset.

## Author
- M Burhan ud din
