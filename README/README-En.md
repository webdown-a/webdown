# WebDown User Guide

Save web pages for real — browse them offline, anytime.

## What It Does

WebDown is a Chrome extension that packages web pages and their resources (images, styles, fonts, scripts, etc.) into ZIP files you can browse offline.

Two modes are available:
- **Save Current Page** — save the page you're viewing right now
- **Site Crawl** — start from one page and automatically follow links to capture multiple pages and resources

## Install

1. Download the latest `webdown-extension-vX.X.X.zip` from [Releases](https://github.com/webdown-a/webdown/releases)
2. Unzip to a permanent folder (don't delete it)
3. Open Chrome, go to `chrome://extensions`
4. Enable **Developer mode** (top-right toggle)
5. Click **Load unpacked** and select the unzipped folder
6. The WebDown icon appears in your toolbar — you're ready

## How to Use

### Save Current Page

1. Open the web page you want to save
2. Click the WebDown icon in the toolbar
3. Make sure the mode is set to **Save Current Page**
4. Click **Start**
5. A ZIP file downloads automatically — unzip it and open `index.html` to browse offline

### Site Crawl

1. Open any page on the target site
2. Click the WebDown icon and switch to **Site Crawl** mode
3. Set the start URL (defaults to the current page)
4. Adjust options as needed:
   - **Crawl Depth** — how many link levels to follow from the start page (0 = start page only)
   - **Page Scope** — control which pages get crawled
     - Current Origin Only: same domain only
     - Same Site/Subdomains: includes subdomains (e.g., blog.example.com)
     - Any Domain: follow links to any site (use allowlist/blocklist to fine-tune)
   - **Allowed Domains** — in Any Domain mode, restrict crawling to specific domains
   - **Excluded Domains** — skip these domains entirely (highest priority)
5. Click **Start**

### Resource Controls

- **Allow External Resources** — download images, styles, etc. from other domains
- **Download Third-party Scripts** — include external JavaScript files
- **Download Media Files** — include video and audio files

### Dynamic Pages

For pages built with JavaScript frameworks (React, Vue, etc.):
- Enable **Wait for Rendering**
- Increase the **Render Wait** time (in milliseconds) as needed

### Performance

- **Sequential Mode** — download one file at a time; slower but more stable
- **Concurrent Downloads** — number of simultaneous downloads; higher = faster, but puts more load on the target server

### Task Controls

During a crawl you can:
- **Pause** — stop crawling; everything downloaded so far is packaged into a ZIP and saved immediately
- **Cancel** — stop crawling; everything downloaded so far is packaged into a ZIP and saved immediately

### Batch Downloads

When dealing with large sites, WebDown automatically splits the output:
- Once a batch reaches a certain file count or size, it's packaged as a separate ZIP (e.g., `site-part1.zip`, `site-part2.zip`)
- Completed batches are safe — even if something goes wrong later, you keep what was already saved
- For smaller sites, a single ZIP is generated as usual

### Viewing Results

- ZIP files contain complete pages with all resources — unzip and open `index.html`
- To browse multiple HTML files, use a local server:
  ```
  python3 -m http.server 8080
  ```
  Then visit `http://localhost:8080`

## Use Cases

- Save articles before the link goes dead
- Download reference materials for offline reading on flights or commutes
- Archive research pages organized by project
- Build a local knowledge base from tutorials and documentation
- Share page content with your team without worrying about the original being changed or deleted

## Tips

| Scenario | Recommendation |
|----------|----------------|
| Static sites | Increase concurrency for faster downloads |
| Dynamic sites (SPA) | Enable render wait and increase the timeout |
| Large sites | Start with a low depth to test, then increase gradually |
| Unstable network | Pause the task; already-downloaded content is preserved |

## Contact

Email: ctzl2022@gmail.com

## Disclaimer

This tool is for lawful learning and technical communication only. Any illegal use is strictly prohibited. Users must comply with local laws and regulations. The developer assumes no legal liability for misuse.
