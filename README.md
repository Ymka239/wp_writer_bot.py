# wp_writer_bot.py
# RSS-to-Wordpress Automation Bot
This repository contains a Python-based automation bot designed to process RSS feeds, analyze content, and publish eligible articles as drafts directly to a WordPress platform using the WordPress REST API.
## Features
1. **HTML Cleaning:**
    - The bot utilizes `BeautifulSoup` to parse HTML and remove unnecessary tags like `<script>`, `<style>`, etc., ensuring clean, readable content.

2. **Article Filtering:**
    - Uses an AI model (or custom logic) to determine whether an article matches specific criteria (e.g., not promotional, related to specific topics like immigration, visas, etc.).

3. **Content Generation:**
    - Automatically generates titles and formatted post content suitable for WordPress drafts.

4. **Category and Tag Suggestions:**
    - Fetches existing categories and tags from WordPress and suggests the most relevant options for the content, helping with metadata optimization.

5. **Draft Publishing:**
    - Publishes articles directly to WordPress in draft status with metadata like focus keyphrases, categories, and tags.

6. **Continuous Execution:**
    - Operates in a loop, processing RSS feeds at regular intervals (default: 1 hour).

## Requirements
- **Python 3.7+**
- Libraries:
    - `requests`
    - `beautifulsoup4`
    - `feedparser`

Install dependencies with pip:
``` bash
pip install requests beautifulsoup4 feedparser
```
## Setup
1. **WordPress Application Password:**
    - Create a WordPress application password for your account to authenticate API requests.
    - Add your WordPress credentials to the following variables in the script:
        - `WORDPRESS_USER`
        - `WORDPRESS_APP_PASSWORD`
        - `WORDPRESS_URL` (your WordPress REST API endpoint, e.g., `https://example.com/wp-json/wp/v2/posts`)

2. **RSS Feeds:**
    - Specify the RSS feed URLs in the `RSS_FEEDS` list in the script.

3. **AI Client Implementation:**
    - Replace the `openai_client` or placeholders in code with your actual AI client or content-generation logic, if applicable.

## How It Works
1. The bot fetches articles from a given list of RSS feeds.
2. Each article's content is downloaded and cleaned of unnecessary HTML.
3. The bot filters articles using AI or predefined logic.
4. Eligible content is processed to generate titles, content body, and focus keyphrases.
5. The bot fetches existing categories and tags from WordPress and suggests relevant ones.
6. Finally, the article is published as a draft in WordPress for review.

## Example Configuration
``` python
RSS_FEEDS = [
    "https://example.com/rss-feed",
    "https://another-feed.com/rss"
]

WORDPRESS_URL = 'https://example.com/wp-json/wp/v2/posts'
WORDPRESS_USER = 'your_username'
WORDPRESS_APP_PASSWORD = 'your_application_password'
```
## Usage
Run the script to start processing RSS feeds continuously:
``` bash
python script_name.py
```
## Notes
- Ensure `WORDPRESS_APP_PASSWORD` is securely stored and not hardcoded when deploying in a production environment.
- If AI-based filtering or content generation is used, integrate your preferred model correctly (`openai_client` or another implementation).
- Customize the time interval between feed processing (default: 1 hour).

## License
This project is licensed under the MIT License. Feel free to use, modify, and distribute it as needed.
