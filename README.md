[Goodfirms Scraper](https://apify.com/happitap/goodfirms-scraper?fpr=data)

# GoodFirms.co Company Scraper

Extract verified company profiles, ratings, reviews, contact info, and service details from [GoodFirms.co](https://www.goodfirms.co/). Perfect for B2B lead generation and market research.

## Features

- **Directory Scraping** — Scrape companies from any GoodFirms category/directory page
- **Search Queries** — Search for companies by keyword
- **Company Profiles** — Extract detailed company information including:

- Company name, tagline, and description
- Rating and review count
- Website, phone, and email
- Location, employees, founded year
- Hourly rate
- Service focus areas
- Industry focus areas
- **Client Reviews** — Extract verified client reviews with ratings
- **Portfolio/Case Studies** — Extract portfolio projects
- **Pagination** — Automatically follows pagination across listing pages
- **Anti-bot Protection** — Stealth mode with fingerprinting, session rotation, and human-like behavior

## Input Examples

### Search by keyword

```
{
    "searchQueries": ["Mobile App Development", "Web Development"],
    "maxItems": 50,
    "includeReviews": true,
    "maxReviewsPerCompany": 5
}
```

### Scrape a specific category

```
{
    "startUrls": [
        { "url": "https://www.goodfirms.co/directory/platform/app-development" }
    ],
    "maxItems": 100,
    "maxPages": 10,
    "includeReviews": true
}
```

### Scrape specific company profiles

```
{
    "startUrls": [
        { "url": "https://www.goodfirms.co/company/sapphire-software-solutions" },
        { "url": "https://www.goodfirms.co/company/openxcell" }
    ],
    "includeReviews": true,
    "includePortfolio": true
}
```

## Output Example

```
{
    "companyName": "Sapphire Software Solutions",
    "tagline": "Leading USA App Development Company",
    "description": "Sapphire Solutions is an ISO 27001:2013 certified Web & Mobile App Development Company...",
    "rating": 4.9,
    "reviewCount": 201,
    "website": "https://www.sapphiresolutions.net/",
    "phone": "+1-234-567-8900",
    "email": "info@sapphiresolutions.net",
    "location": "Ahmedabad, India",
    "employees": "50 - 249",
    "founded": "2002",
    "hourlyRate": "$25 - $49/hr",
    "serviceFocus": [
        { "service": "Mobile App Development", "percentage": "40%" },
        { "service": "Web Development", "percentage": "30%" }
    ],
    "industryFocus": ["Healthcare", "Education", "Finance"],
    "reviews": [
        {
            "rating": 5.0,
            "title": "Amazing work by team",
            "text": "Sapphire gave us the programme we needed...",
            "author": "John Doe",
            "date": "2024-01-15",
            "projectType": "Mobile App Development"
        }
    ],
    "portfolio": [
        {
            "title": "Healthcare App",
            "description": "Custom healthcare management platform...",
            "industry": "Healthcare",
            "cost": "$50,000 - $100,000"
        }
    ],
    "goodfirmsUrl": "https://www.goodfirms.co/company/sapphire-software-solutions",
    "scrapedAt": "2026-02-21T14:00:00.000Z"
}
```

## Proxy Recommendations

GoodFirms may block requests from datacenter IPs. **Residential proxies are recommended** for reliable scraping.

## Development

```
npm install
npm run dev
```

## Deployment

Push to Apify platform:

```
$apify push
```