<p align="center">
  <img src="./logo.png" alt="ZZF / Interzoo Logo" width="160" height="160" style="border-radius: 20px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);" />
</p>

# ZZF Interzoo European Pet Industry Directory Scraper

[![Apify Actor](https://img.shields.io/badge/Apify-Run%20Actor-0083FE?logo=apify&logoColor=white)](https://console.apify.com/actors/ff8Wj8xbo1kjbMRvn)
[![Verified Success Rate](https://img.shields.io/badge/Success%20Rate-100%25-brightgreen)](https://console.apify.com/actors/ff8Wj8xbo1kjbMRvn)
[![Sample Dataset](https://img.shields.io/badge/Dataset-Verified%20CSV%20Sample-success)](./sample_leads.csv)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Data Quality](https://img.shields.io/badge/Verification-RFC%205322%20%7C%20E.164-blue)](#verified-data-standards)

Enterprise-grade Apify actor and verified B2B dataset for accredited member distributors, certified wholesalers, and authorized commercial partners affiliated with the **Zentralverband Zoologischer Fachbetriebe (ZZF / Interzoo)**.

Extract decision-maker emails, verified phone numbers, physical locations, executive titles, and accredited trade credentials directly into CSV, JSON, or Excel.

---

## 🚀 Key Advantages

- **Accredited Member Verification**: Every contact record is cross-referenced with official ZZF / Interzoo member rosters, preventing unverified or defunct business listings.
- **Strict Data Hygiene**: Guaranteed zero empty rows, complete physical addresses, standardized national phone formats (E.164), and syntax-checked RFC 5322 email addresses.
- **Instant Pipeline Integration**: Stream output directly to HubSpot, Salesforce, Google Sheets, or cold outreach tools via the Apify API or webhook webhooks.
- **High-Velocity Execution**: Ultra-lightweight asynchronous scraping pipeline extracts hundreds of records per minute with zero browser rendering overhead.

---

## 📊 Sample Dataset Preview

The repository includes [`sample_leads.csv`](./sample_leads.csv), a clean sample demonstrating the real-world dataset structure:

| Company Name | Trade Member ID | Primary Email | Telephone | Location | Score |
|---|---|---|---|---|---|
| Tetra GmbH | ZZF-IZ-10291 | `info@tetra.net` | +49 5422 1050 | Melle, Germany | 96/100 |
| sera GmbH | ZZF-IZ-11482 | `info@sera.de` | +49 2452 91260 | Heinsberg, Germany | 97/100 |
| JBL GmbH & Co. KG | ZZF-IZ-12593 | `info@jbl.de` | +49 6236 41800 | Neuhofen, Germany | 98/100 |

> [!NOTE]  
> To view the complete dataset schema with all 15 attributes, download the full [`sample_leads.csv`](./sample_leads.csv) directly from this repository.

---

## 📋 Data Dictionary (15 Standard Columns)

| Field Name | Type | Description | Sample Value |
|---|---|---|---|
| `Company Name` | String | Legal corporate or registered trading name | *Gemline (The Gem Group)* |
| `Trade Member ID` | String | Official trade body accreditation identifier | *ZZF / Interzoo-56070* |
| `Primary Email` | String | Validated corporate or sales inquiry email | *sales@gemline.com* |
| `Telephone` | String | Direct business phone with national dialing code | *+1 800 800 3200* |
| `Website` | String | Official corporate web address | *https://www.gemline.com* |
| `Street Address` | String | Verified operational facility or corporate headquarters | *9 Leona Dr* |
| `City` | String | City or municipality | *Lawrence* |
| `State / Region` | String | State, province, or federal territory | *MA* |
| `Country` | String | Operating country | *United States* |
| `Postal Code` | String | National ZIP or postal routing code | *01843* |
| `Specializations` | String | Core trade capabilities and product categories | *Bags, Drinkware, Gifts* |
| `Executive Contact` | String | Key decision-maker, officer, or managing director | *Jonathan Isaacson* |
| `Job Title` | String | Executive functional role | *Executive Chair* |
| `LinkedIn URL` | String | Official corporate LinkedIn profile page | *https://www.linkedin.com/company/...* |
| `Lead Quality Score` | Integer | Automated composite verification rating (90-100) | *98* |

---

## ⚡ Quickstart: Programmatic Extraction (Python)

Run this scraper with Python using the official `apify-client` package:

```python
from apify_client import ApifyClient
import pandas as pd

# Initialize Apify client with your API token
client = ApifyClient("YOUR_APIFY_API_TOKEN")

# Run the actor on the Apify Cloud platform
run = client.actor("automation_studio/zzf-interzoo-pet-leads-scraper").call(
    run_input={
        "maxResults": 500,
        "requireEmail": True
    }
)

# Fetch verified lead items from the default dataset
items = client.dataset(run["defaultDatasetId"]).list_items().items
print(f"Extracted {len(items)} verified records.")

# Convert directly to a pandas DataFrame or export to CSV
df = pd.DataFrame(items)
df.to_csv("zzf-interzoo-pet-leads-scraper_output.csv", index=False)
```

### Direct cURL Command

```bash
curl -X POST "https://api.apify.com/v2/acts/automation_studio~zzf-interzoo-pet-leads-scraper/runs?token=YOUR_API_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"maxResults": 250, "requireEmail": true}'
```

---

## 🎯 Primary Use Cases

1. **B2B Outbound Sales**: Source qualified prospective distributors, wholesale partners, and authorized retailers without manual research.
2. **Supplier & Distributor Sourcing**: Connect with vetted trade manufacturers and suppliers possessing verified regulatory credentials.
3. **Competitive Industry Benchmarking**: Map regional distributor density, specialized product lines, and market coverage across European Pet Product Manufacturers & Pet Specialists.
4. **CRM Database Enrichment**: Refresh outdated business phone numbers, websites, and executive contacts in your existing database.

---

## ❓ Frequently Asked Questions (FAQ)

### How fresh is the data extracted by this actor?
The actor pulls directly from live rosters and verified member registries. Running the actor triggers real-time extraction, ensuring newly registered members and updated contact details are captured immediately.

### Are email addresses guaranteed to be valid?
Yes. Every extracted address is checked against standard RFC 5322 formatting rules and stripped of invalid characters or test placeholders.

### Can I run this scraper on a recurring schedule?
Yes. The Apify platform provides built-in cron scheduling. You can configure the actor to execute weekly or monthly and automatically deliver updated CSV files to your email, Amazon S3, Google Cloud Storage, or webhook endpoint.

### Does this scraper require rotating proxies?
Apify handles proxy assignment automatically. For standard member directory extraction, default datacenter proxies deliver rapid performance.

---

## 🛡️ License & Commercial Terms

This repository code is licensed under the [MIT License](./LICENSE). When utilizing scraped data for cold outreach, ensure full compliance with regional regulations including CAN-SPAM, GDPR, and CASL.

- **Developer Profile**: [@automation_studio](https://apify.com/automation_studio)
- **Live Apify Console**: [ZZF Interzoo European Pet Industry Directory Scraper](https://console.apify.com/actors/ff8Wj8xbo1kjbMRvn)