# WebDown Project Overview (English)

## Purpose

WebDown is a browser extension + license service stack for offline web archiving. Its core goals are:
- Capture web content and package it into distributable offline ZIP archives
- Support both single-page and full-site crawl modes
- Control extension availability through trial/license logic
- Deliver update notices and upgrade links to users

## Functional Modules

### 1) Page Archive
Used to save the current page and its dependencies as an offline package.

Features:
- Capture current page HTML
- Parse and download resources (CSS, JS, images, fonts, media)
- Rewrite resource references for offline usability
- Export ZIP output

### 2) Site Crawl
Used to recursively crawl pages from a start URL and package them together.

Features:
- Breadth-first traversal from start URL
- Crawl expansion controlled by depth
- Domain boundary control via page scope
- Unified mapping, deduplication, and packaging of pages/resources

### 3) Task Control
Used to control long-running archive tasks.

Features:
- Start task
- Pause task (keep already downloaded progress)
- Resume task (continue from paused progress)
- Real-time status and stats updates

### 4) Licensing & Trial
Used to manage extension access.

Features:
- Activation-code based licensing
- License status query and refresh
- Trial creation and expiration checks
- Configurable default trial days in admin backend
- Trial reset by device

### 5) Update Announcement
Used to notify users about new versions.

Features:
- Configure latest version and announcement text in admin backend
- Configure update redirect URL
- Extension compares local version and shows update banner

## Core Parameters

### A. Archive Parameters (Extension Side)

- `mode`
  - Purpose: archive mode selector
  - Values: `page` (current page), `site` (full-site crawl)

- `startUrl`
  - Purpose: crawl start URL
  - Notes: site entry for `site` mode; target page for `page` mode

- `archiveName`
  - Purpose: output ZIP filename
  - Notes: auto-generated when empty

- `zipRootFolder`
  - Purpose: root folder name inside ZIP
  - Notes: used for archive organization

- `depth`
  - Purpose: site crawl depth
  - Range: `0-20`

- `pageScope`
  - Purpose: link-follow domain scope
  - Values:
    - `same-origin`
    - `same-site`
    - `any-domain`

- `allowExternalResources`
  - Purpose: allow downloading cross-domain resources
  - Type: `boolean`

- `includeScripts`
  - Purpose: include script resources
  - Type: `boolean`

- `includeMedia`
  - Purpose: include media resources
  - Type: `boolean`

- `render`
  - Purpose: wait for rendering before capture
  - Type: `boolean`

- `renderTimeoutMs`
  - Purpose: render wait time in milliseconds
  - Range: `0-45000`

- `sequential`
  - Purpose: sequential download mode
  - Type: `boolean`

- `maxConcurrency`
  - Purpose: concurrent download count
  - Range: `1-20`

- `quiet`
  - Purpose: quiet mode switch
  - Type: `boolean`

- `proxyUrl`
  - Purpose: proxy input parameter slot
  - Notes: currently reserved; real proxy routing is not enabled

- `uiLanguage`
  - Purpose: UI language
  - Values: `auto`, `zh-CN`, `en-US`

### B. License Parameters (Extension / Server)

- `activationCode`
  - Purpose: activation code
  - Format: `WD1-XXXX-XXXX-XXXX-XXXX`

- `licenseId`
  - Purpose: unique license record identifier

- `deviceId`
  - Purpose: unique device identifier for trial/activation binding

- `plan`
  - Purpose: plan identifier (for example `pro`, `trial`)

- `maxActivations`
  - Purpose: max device bindings per activation code

- `expiresAt`
  - Purpose: license expiration timestamp (milliseconds)

- `trialDaysDefault`
  - Purpose: default trial duration in days
  - Notes: applies only when a new trial record is created

### C. Announcement Parameters (Admin Side)

- `latestVersion`
  - Purpose: latest release version
  - Notes: compared with extension local version

- `title`
  - Purpose: announcement title

- `notes`
  - Purpose: announcement body text

- `url`
  - Purpose: update target URL (opened by “Update Now”)

- `publishedAt`
  - Purpose: announcement publish timestamp (milliseconds)

## Admin Capability Parameters

### Activation Code Generation Parameters
- `plan`: plan identifier
- `maxActivations`: device limit
- `expiresAt`: expiration time (timestamp / relative days / date format)

### Trial Reset Parameter
- `deviceId`: target device ID

### Key Fields in Code List
- `licenseId`: license identifier
- `key` (activation code): plain activation code (available for newly generated records)
- `status`: license status
- `plan`: plan name
- `max_activations`: device limit
- `expires_at`: expiration timestamp
- `created_at`: creation timestamp
