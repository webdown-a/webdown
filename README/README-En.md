# WebDown User Guide (English)

## What It Does

WebDown is a browser extension for saving websites as offline packages. It supports:
- Saving the current page
- Crawling a whole site
- Exporting ZIP files for local backup, sharing, and archiving

## Main Features

- Dual archive modes: current page / full-site crawl
- Resource capture: CSS, JS, images, fonts, and media
- Scope controls: depth, domain scope, external resource toggle
- Performance controls: sequential/concurrent mode, concurrency count, render wait
- Task controls: start, pause, resume
- Live progress: current stage, current URL, download stats
- Update notice: “Update Now” appears when a newer version is available
- Bilingual UI support

## How to Use

### ZIP Extension Import Tip (Chrome)

To import a ZIP-format Chrome extension:
1. Unzip the plugin package to a fixed folder
2. Open `chrome://extensions`
3. Enable **Developer mode**
4. Click **Load unpacked**
5. Select the unzipped extension folder

### 1. Open the Extension Panel
Click the WebDown icon in your browser toolbar.

### 2. Select a Mode
- Save Current Page: archive only the current page
- Site Crawl: recursively crawl from a start URL

### 3. Configure Crawl Parameters
Common parameters:
- `Start URL`: crawl entry address
- `Depth`: recursive link depth for site mode
- `Page Scope`: same-origin / same-site / any-domain
- `Allow External Resources`: include cross-domain static resources
- `Download Third-party Scripts`: include script files
- `Download Media Files`: include audio/video files
- `Wait for Rendering`: recommended for dynamic pages
- `Render Wait (ms)`: render wait duration
- `Sequential Mode`: stable but slower
- `Concurrent Downloads`: higher = faster, but more load
- `ZIP Filename`: custom output file name
- `ZIP Root Folder`: optional root folder name inside ZIP

### 4. Start Archiving
Click `Start` and watch real-time status and stats.

### 5. Pause and Resume
- Click `Pause` to stop further processing
- Click `Resume` to continue from existing progress (already downloaded content is kept)

### 6. Download the Result
When finished, the extension generates and downloads a ZIP file. Unzip it for offline browsing.

## Usage Tips

- Static sites: increase concurrency for better speed
- Dynamic sites: enable render wait and increase timeout if needed
- Large sites: start with lower depth, then increase gradually
- Unstable network: pause first and resume later
