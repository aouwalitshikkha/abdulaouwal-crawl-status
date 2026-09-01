# abdulaouwal.com — Blog Crawl Status Tracker

Live page: **https://aouwalitshikkha.github.io/abdulaouwal-crawl-status/**

Interactive table of every published (free) blog article on [abdulaouwal.com](https://abdulaouwal.com), showing:

| Column | Meaning |
|---|---|
| URL | Article slug + title (linked) |
| Last Modified | Last CMS edit, in Dhaka time (UTC+6) |
| Last Crawled by Google | Last Google crawl from Search Console URL Inspection, in Dhaka time |
| Status | OK / STALE / NOT CRAWLED |

## Features

- **Filters** — search by URL/title, filter by status, filter by date range (Last Modified and Last Crawled, independently)
- **Sortable columns** — click any header to sort
- **Live summary cards** — OK / Stale / Not crawled counts update with every filter

## Data pipeline

This page is rebuilt **daily at 3:00 AM Bangladesh time** by a scheduled job that:

1. Fetches all published articles from the `abdulaouwal.com` CMS API
2. Runs Google Search Console **URL Inspection** for each URL to get its last crawl time
3. Excludes paid and draft articles
4. Builds this filterable HTML page and pushes it to this repo (GitHub Pages auto-deploys)

**Last modified** = the article's `updated_at` from the CMS.  
**Status** = OK when Google's last crawl is newer than the article's last edit; STALE when the edit is newer than the crawl; NOT CRAWLED when Google has never crawled the URL.

*Crawl and edit times are shown in Dhaka (Asia/Dhaka, UTC+6).*
