[Goodfirms Scraper](https://apify.com/alizarin_refrigerator-owner/goodfirms-scraper?fpr=data)

# GoodFirms Directory Scraper

Scrape B2B company profiles from GoodFirms directory. Extract company info, reviews, ratings, services, and portfolios. Find IT companies, agencies, and software providers. Built by John Rippy ([https://www.linkedin.com/in/johnrippy/](https://www.linkedin.com/in/johnrippy/) | [https://johnrippy.link/](https://johnrippy.link/)).

---

## Quick Start

### Test with Demo Mode (free, no API key needed)

```
{
  "demoMode": true,
  "searchQuery": "software development company"
}
```

### Run with real data

```
{
  "demoMode": false,
  "searchQuery": "software development company",
  "maxResults": 50
}
```

---

## Input Parameters

| Parameter | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `demoMode` | boolean | `true` | No | Run with sample data without making API calls. Great for testing the actor. |
| `searchQuery` | string | - | No | Search term (e.g., 'software development', 'web design', 'mobile app'). |
| `category` | string | - | No | Filter by company category. |
| `location` | string | - | No | Filter by location (e.g., 'USA', 'India', 'UK'). |
| `maxResults` | integer | `50` | No | Maximum number of companies to scrape. |
| `webhookUrl` | string | - | No | URL to POST results when scraping completes (Zapier, Make, n8n, custom endpoint) |

---

## Pricing

This actor uses **pay-per-event** billing:

| Event | Description | Price |
| --- | --- | --- |
| Company Scraped | Each GoodFirms company profile scraped | $0.08 |

**Demo mode is free** -- no charges for sample data.

---

## Troubleshooting

### "API error 429" or "Rate limit"

Too many requests. Wait a minute and try again, or reduce the number of items per run.

### No results or empty dataset

Check the run log for error messages. Common causes:

- Invalid input format (check the examples above)
- The target data doesn't exist or is too small to track

### How do I test without an API key?

Enable **Demo Mode** in the input. This returns realistic sample data so you can verify the output format works for your workflow.

---

**Built by John Rippy | [Actor Arsenal](https://actorarsenal.com)**