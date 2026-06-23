[Goodfirms Scraper](https://apify.com/jungle_synthesizer/goodfirms-scraper?fpr=data)

# GoodFirms IT Services Directory Scraper

Scrape B2B company profiles from [GoodFirms.co](https://www.goodfirms.co/), a directory of IT services firms, software agencies, and digital product companies with 100K+ listings. Returns company names, contact details, websites, founded year, employee count, hourly rates, service focus, industry focus, client focus, and social links.

---

## GoodFirms Scraper Features

- Extracts 20+ fields per company profile including email, phone, hourly rate, and employee count
- Scrapes both IT service companies and software product listings
- Discovers profiles automatically via the GoodFirms sitemap, or accepts direct profile URLs
- Pulls data from JSON-LD structured metadata and DOM elements for maximum coverage
- Handles Cloudflare JS challenge with browser-based scraping and residential proxies
- Outputs to JSON, CSV, or the Apify API

---

## Who Uses GoodFirms Data?

- **Sales teams** -- Build prospect lists of IT agencies filtered by size, hourly rate, and service specialty
- **Market researchers** -- Analyze the B2B services landscape by industry focus, geography, and pricing tier
- **Procurement teams** -- Screen potential vendors by employee count, founding year, and client focus before RFP
- **Competitive intelligence** -- Monitor how competitors position themselves on GoodFirms and what services they highlight
- **CRM enrichment** -- Backfill company records with founded year, social links, and service breakdowns

---

## How the GoodFirms Scraper Works

1. **Pick your mode** -- Provide specific GoodFirms company or software URLs, or let the scraper discover profiles from the sitemap
2. **Sitemap discovery** -- When no URLs are provided, the scraper fetches the GoodFirms sitemap index from inside a browser session (required to bypass Cloudflare) and collects company and/or software profile URLs
3. **Profile extraction** -- Each profile page is visited with a stealth browser. Data is pulled from JSON-LD LocalBusiness metadata and supplemented with DOM selectors for pricing, employee count, and focus breakdowns
4. **Export** -- Records land in the Apify dataset for download or API access

---

## Input

```
{
  "searchUrls": [
    { "url": "https://www.goodfirms.co/company/bluehost" },
    { "url": "https://www.goodfirms.co/company/toucan" }
  ],
  "scrapeMode": "companies",
  "maxItems": 50
}
```

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| searchUrls | object[] | `[]` | GoodFirms profile URLs to scrape directly. Each entry is `{ "url": "..." }`. Leave empty to discover profiles from the sitemap. |
| scrapeMode | string | `"companies"` | Which entity type to discover from the sitemap: `"companies"`, `"software"`, or `"both"`. Ignored when searchUrls are provided. |
| maxItems | integer | `50` | Maximum number of profiles to scrape. Keep low for test runs -- GoodFirms is slow due to Cloudflare and residential proxy overhead. |
| proxyConfiguration | object | Residential | Proxy settings. GoodFirms requires residential proxies to bypass Cloudflare. |

### Sitemap Discovery Mode

Omit searchUrls to crawl the full directory up to your maxItems limit:

```
{
  "scrapeMode": "both",
  "maxItems": 100
}
```

---

## GoodFirms Scraper Output Fields

```
{
  "profileUrl": "https://www.goodfirms.co/company/bluehost",
  "entityType": "company",
  "companyName": "Bluehost",
  "description": "Bluehost is a leading web hosting solutions company...",
  "website": "https://www.bluehost.com",
  "logo": "https://assets.goodfirms.co/images/bluehost-logo.png",
  "phone": "+1 (888) 401-4678",
  "email": "support@bluehost.com",
  "streetAddress": "1500 N Priest Dr",
  "city": "Tempe",
  "region": "AZ",
  "country": "US",
  "postalCode": "85281",
  "foundedYear": 2003,
  "companySize": "1,000 - 9,999",
  "hourlyRate": "< $25/hr",
  "priceRange": "$",
  "services": ["Web Hosting: Shared Hosting, VPS Hosting, Dedicated Hosting"],
  "industryFocus": ["Information Technology - 40%", "E-commerce - 30%"],
  "clientFocus": ["Small Business - 60%", "Midmarket - 30%"],
  "socialLinks": ["https://www.facebook.com/bluehost", "https://twitter.com/bluehost"],
  "scrapedAt": "2026-04-14T12:00:00.000Z"
}
```

| Field | Type | Description |
| --- | --- | --- |
| profileUrl | string | GoodFirms profile URL |
| entityType | string | Entity type: `"company"` or `"software"` |
| companyName | string | Company or product name |
| description | string | Profile description / bio |
| website | string | Company website URL |
| logo | string | Logo image URL |
| phone | string | Primary phone number |
| email | string | Primary contact email |
| streetAddress | string | Headquarters street address |
| city | string | Headquarters city |
| region | string | Headquarters state / region |
| country | string | Headquarters country code (ISO) |
| postalCode | string | Headquarters postal code |
| foundedYear | number | Year the company was founded |
| companySize | string | Employee count bracket (e.g., `"250 - 999"`) |
| hourlyRate | string | Hourly rate bracket (e.g., `"< $25/hr"`) |
| priceRange | string | Price range indicator from JSON-LD |
| services | string[] | Services offered, formatted as `"Category: subtype, subtype"` |
| industryFocus | string[] | Industry focus with percentage (e.g., `"Financial Services - 30%"`) |
| clientFocus | string[] | Client size focus with percentage (e.g., `"Small Business - 60%"`) |
| socialLinks | string[] | Social media and external profile links |
| scrapedAt | string | ISO timestamp when the record was scraped |

---

## FAQ

### How do I scrape company data from GoodFirms?

The GoodFirms Scraper handles it. Paste specific company URLs into the searchUrls field, or leave it empty to let the scraper discover profiles from the GoodFirms sitemap. Set your maxItems limit and run.

### How much does the GoodFirms Scraper cost to run?

The GoodFirms Scraper uses pay-per-event pricing: $0.10 per actor start plus $0.001 per record. A 50-company run costs roughly $0.15. The main cost driver is residential proxy usage, since GoodFirms requires Cloudflare bypass.

### Can I scrape both companies and software products?

Yes. Set `scrapeMode` to `"both"` and the GoodFirms Scraper will interleave company and software profiles from the sitemap. Each record includes an `entityType` field so you can filter downstream.

### Does the GoodFirms Scraper need proxies?

Yes. GoodFirms.co uses Cloudflare JS challenges, so residential proxies are required. The actor configures Apify's residential proxy group automatically.

### How many companies are on GoodFirms?

GoodFirms indexes over 100,000 company and software profiles. The sitemap discovery mode can access them all, capped by your maxItems setting.

---

## Need More Features?

Need custom fields, category filtering, or a scraper for a different B2B directory? [File an issue](https://console.apify.com/actors/issues) or get in touch.

## Why Use the GoodFirms Scraper?

- **Rich data** -- 20+ fields per profile including email, phone, hourly rate, employee count, and focus breakdowns that most directories hide behind clicks
- **Dual extraction** -- Combines JSON-LD structured data with DOM scraping for fields that only exist in the rendered page
- **Flexible** -- Scrape specific profiles by URL or discover thousands via sitemap, with company and software modes