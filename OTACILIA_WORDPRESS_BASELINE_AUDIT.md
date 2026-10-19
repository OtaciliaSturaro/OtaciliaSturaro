# Otacilia Sturaro — WordPress Baseline Audit

| Field | Value |
|---|---|
| Site | otaciliasturaro.com (WordPress.com site ID `231107304`) |
| Audit type | Read-only technical baseline |
| Audit date | 2026-10-19 |
| Method | Authenticated WordPress.com MCP connection (read operations only), plus anonymous HTTP requests to the public site |
| Changes made to WordPress | **None.** All write operations are disabled in the MCP connection settings, and none were attempted. |
| Purpose | Baseline to compare with the separate historical website design audit before the master architecture is approved |

### How to read this document

- Sections 1–5 hold **verified findings** (prefix `F-`). Each one came straight from a WordPress.com API response or a live HTTP request made during the audit.
- Section 6 holds **recommendations** (prefix `R-`). They are proposals and have not been implemented.
- Section 7 holds **owner decisions** (prefix `Q-`).
- Wherever something could not be verified, the document says so as a **Limitation** (prefix `L-`).
- The IDs exist so this baseline can be cross-referenced item by item with the historical design audit.

---

## 1. Verified WordPress configuration and site identity

### 1.1 Account and access

| ID | Finding |
|---|---|
| F-01 | Authenticated as WordPress.com user `otaciliasturaro` (display name "Otacilia Sturaro", user ID 246990623). |
| F-02 | That user is the site's **only** user, with the role Administrator. Registered 2024-02-21. |
| F-03 | The account has two sites: **otaciliasturaro.com** (audited here) and **hightechhighquality.com** ("HTHQ FINANÇAS FREEDOM"). |
| F-04 | hightechhighquality.com is a self-hosted Jetpack site marked **disconnected**, so MCP tools cannot reach it. See L-01. |
| F-05 | In the MCP connection, every create, update and delete operation is **disabled** for content, site editing and settings. Only read operations are available. |

### 1.2 Site identity

| Setting | Verified value |
|---|---|
| Site title (`blogname`) | `OTACILIA STURARO` |
| Tagline (`blogdescription`) | `Owner First. Advisor Second.` (set 2026-10-18) |
| Home / Site URL | `https://otaciliasturaro.com` |
| Primary domain | `otaciliasturaro.com`, flagged as a custom domain |
| Hosting platform | WordPress.com "atomic", the hosting tier with SSH/SFTP access |
| Site created | 2024-03-21 |
| WordPress / PHP version | WordPress 7.1.3 / PHP 8.4.26 (from the backup metadata) |
| Language | `en_US` |
| Timezone | `America/New_York` (GMT−4 at audit time) |
| Date / time format | `F j, Y` / `g:i a` |
| Week starts on | Sunday (0) |
| Admin email | `ADMIN@OTACILIASTURARO.COM` |
| Site logo | **Not set** (`site_logo: 0`) |
| Site icon (favicon) | **Not set** (`site_icon: 0`) |
| User registration | Disabled; default role `subscriber` |

### 1.3 Reading, writing and discussion settings

| Setting | Verified value |
|---|---|
| Front page displays | **Latest posts** (`show_on_front: posts`) |
| Static front page / posts page | None (`page_on_front: 0`, `page_for_posts: 0`) |
| Posts per page / RSS | 10 / 10, full text in feeds |
| Permalink structure | `/%year%/%monthnum%/%day%/%postname%/` |
| Category / tag base | Default (empty) |
| Default comment status | **Open** |
| Pingbacks / trackbacks | **Open** |
| Comment moderation | Off; previously approved commenters are auto-approved |
| Close comments on old posts | Off |
| XML-RPC | Enabled |
| Default post category | Uncategorized (ID 1) |
| Privacy policy page | Not set (`wp_page_for_privacy_policy: 0`) |

### 1.4 Recent activity log (verified)

All of these events occurred on 2026-10-18 local time (2026-10-18 23:24 → 2026-10-19 00:14 UTC).

| ID | Event |
|---|---|
| F-06 | An initial full Jetpack backup recorded the site URL as `otaciliasturaro.wpcomstaging.com`. A second full backup minutes later recorded `otaciliasturaro.com`. Default options (thumbnail sizes, time format, comment threading, `show_on_front`, `site_icon`, privacy page) were written by the system at the same moment. This pattern suggests the site was **recently transferred or re-provisioned** onto its current hosting. |
| F-07 | The owner logged in and **turned off** the Jetpack Search module. |
| F-08 | The owner set the tagline to "Owner First. Advisor Second." A term named `footer` was created at the same time. |
| F-09 | The owner uploaded one portrait photo (media ID 22). |
| F-10 | The owner updated the HOME draft (page ID 25). |
| F-11 | The server installed the "WordPress Agent" plugin (v7.9.22). |
| F-12 | Backups ran with no errors and no scan findings. |

### 1.5 Traffic and audience

| ID | Finding |
|---|---|
| F-13 | 2 views and 2 visitors from 2026-07-21 to 2026-10-18. |
| F-14 | 0 subscribers. 0 comments on record. |
| F-15 | Site health is "warning", with the reason "No posts published in over a year". |

---

## 2. Complete inventory

### 2.1 Pages (all statuses, including drafts, private and trash)

| ID | Title | Slug | Status | Last modified | Template | Content |
|---|---|---|---|---|---|---|
| 1 | About | `about` | Published | 2024-03-21 | Default | **WordPress sample text** ("This is an example of a page…"), including a link into the WordPress.com dashboard (`wordpress.com/page/231107304/new/`) |
| 25 | HOME | `home` | **Draft** | 2026-10-18 | Default | **Empty.** No body, excerpt, featured image or SEO fields. Preview URL `?page_id=25` |

Total: 2 pages (1 published, 1 draft). Nothing is in trash, pending or scheduled.

### 2.2 Posts (all statuses)

| ID | Title | Slug | Status | Date | Category | Content |
|---|---|---|---|---|---|---|
| 2 | Hello World! | `hello-world` | Published | 2024-03-21 | Uncategorized | **WordPress sample post** ("Welcome to WordPress! This is your first post…"). Comments open. |

Total: 1 post.

### 2.3 Taxonomies

| Type | Items |
|---|---|
| Categories | Uncategorized (ID 1, 1 post) |
| Tags | None |
| Synced (reusable) patterns | Not enumerated. See L-06. |

### 2.4 Theme

| Field | Value |
|---|---|
| Active theme | **Twenty Twenty-Two** (`twentytwentytwo`), a block (full-site-editing) theme |
| Installed themes | Twenty Twenty-Two only |
| Global Styles customizations (user layer, ID 3) | **None**: `settings: []`, `styles: []` |
| Theme palette (defaults) | Foreground `#000000`, Background `#ffffff`, Primary `#1a4548`, Secondary `#ffe2c7`, Tertiary `#F6F6F6` |
| Theme fonts (defaults) | System Font stack; Source Serif Pro (variable 200–900, roman and italic) |
| Theme font sizes | small 1rem, medium 1.125rem, large 1.75rem, x-large clamp(1.75rem, 3vw, 2.25rem) |
| Layout widths | Content 650px, wide 1000px |

### 2.5 Templates

| Template ID | Title | Source | Notes |
|---|---|---|---|
| `twentytwentytwo//blank` | Blank | **custom (modified)** | Post content only, medium font size |
| `twentytwentytwo//404` | Page: 404 | theme | Default |
| `twentytwentytwo//page-no-separators` | Page (No Separators) | theme | Default |
| `twentytwentytwo//archive` | All Archives | theme | Default |
| `twentytwentytwo//page` | Pages | theme | Default. Includes a comments block. |
| `twentytwentytwo//single` | Single Posts | theme | Default. Includes a comments block. |
| `twentytwentytwo//search` | Search Results | theme | Default |
| `twentytwentytwo//home` | Blog Home | theme | **Renders the current homepage**, using the `header-small-dark` part |
| `twentytwentytwo//single-no-separators` | Single Post (No Separators) | theme | Default |
| `twentytwentytwo//index` | Index | theme | Fallback |
| `twentytwentytwo//page-large-header` | Page (Large Header) | theme | Uses the `header-large-dark` part, which holds demo content (F-17) |

### 2.6 Template parts

| Part ID | Area | Source | Content |
|---|---|---|---|
| `twentytwentytwo//header-small-dark` | header | **custom (modified)** | Black background. Contains an empty site-logo block (no logo is set), the logo image (media 5, 234px), the "chrome" wordmark image (media 13, 654px), and the navigation block (automatic page list). Used by Blog Home, the current homepage. |
| `twentytwentytwo//header` | header | theme | Site logo, italic site title, navigation (automatic page list) |
| `twentytwentytwo//header-large-dark` | header | theme | **Theme demo content** (F-17) |
| `twentytwentytwo//footer` | footer | **custom (modified)** | Site title plus **two empty paragraphs**. The "Proudly powered by" credit has been removed. No contact, legal or social links. |

| ID | Finding |
|---|---|
| F-17 | `header-large-dark` still contains the Twenty Twenty-Two demo heading *"The Hatchery: a blog about my adventures in bird watching"* and the theme's bird illustration (`flight-path-on-transparent-c.png`). It is used by the Page (Large Header) template. No page currently uses that template. |

### 2.7 Navigation and menus

| ID | Type | Title | Content | Rendered output |
|---|---|---|---|---|
| 4 | Block navigation (`wp_navigation`) | Navigation | `<!-- wp:page-list /-->` (automatic list of published pages) | One link: **About** → `/about/` |

- There are no hand-built links. The menu shows whatever pages are published.
- Classic menus and widget areas were not enumerated. They don't apply to this block theme.

### 2.8 Plugins

| Plugin | Version | Status | Notes |
|---|---|---|---|
| Jetpack | 16.4-a.1 | Active | Can't be deactivated (platform-managed). Provides backups, the activity log and per-page SEO fields. |
| Akismet Anti-spam | 5.7.2 | Active | Platform-managed |
| Gutenberg | 24.2.0 | Active | Development version of the block editor |
| Page Optimize | 0.6.3 | Active | Combines and optimizes CSS/JS files |
| Gravatar Enhanced | 0.14.0 | Active | |
| WordPress Agent (`big-sky`) | 7.9.22 | Active | Installed by the server on 2026-10-18 |
| Classic Editor | 1.7.0 | Inactive | |
| Crowdsignal Dashboard | 3.1.8 | Inactive | |
| Crowdsignal Forms | 1.8.3 | Inactive | |
| Layout Grid | 1.8.5 | Inactive | |

Totals: 10 installed, 6 active, 0 updates pending. **No dedicated SEO, forms, analytics or caching plugin is installed.**

### 2.9 Media library (13 items)

| ID | Uploaded | Title / filename | Type | Dimensions | Size | Alt text |
|---|---|---|---|---|---|---|
| 22 | 2026-10-18 | `9EB6BE8E-E7BD-440F-BCE2-42AF05EBEA37.jpeg` (portrait) | JPEG | 1424×1898 | 0.8 MB | **None** |
| 19 | 2024-09-16 | `image.jpeg` | JPEG | 975×1300 | 0.17 MB | **None** |
| 18 | 2024-09-16 | `foto-nova.jpg` ("FOTO NOVA") | JPEG | 3525×3467 | 1.19 MB | **None** |
| 17 | 2024-09-15 | `screenshot-2024-09-01-at-1.12.16…pm.png` | PNG | 2866×1438 | **4.61 MB** | **None** |
| 13 | 2024-06-27 | `otacilia-sturaro-chrome-1.png` (wordmark, wide crop) | PNG | 3956×494 | 0.76 MB | **None** |
| 12 | 2024-06-27 | `otacilia-sturaro-chrome-edited.png` | PNG | 4078×2718 | 0.83 MB | "Otacilia Sturaro" |
| 11 | 2024-06-27 | `unknown.webp` ("Unknown") | WebP | 768×768 | 0.54 MB | **None** |
| 10 | 2024-06-27 | `luxury_miami_mansion_with_beachfront_43550824.webp` | WebP | 1016×576 | 0.51 MB | **None** |
| 9 | 2024-06-27 | `luxury_miami_beachfront_real_estate_4094010455.webp` | WebP | 1016×576 | 0.37 MB | **None** |
| 8 | 2024-06-27 | `os-side-headshot_hd.png` | PNG | 1024×1419 | 0.90 MB | **None** |
| 7 | 2024-06-27 | `os-body-shot-hd.png` | PNG | 1024×1216 | 0.60 MB | **None** |
| 6 | 2024-06-27 | `otacilia-sturaro-chrome.png` (wordmark, original) | PNG | 4200×2800 | 1.45 MB | "Otacilia Sturaro" |
| 5 | 2024-06-27 | `os-sahire-glow.png` ("Otacilia Sturaro logo") | PNG | 4200×2800 | 2.06 MB | "Otacilia Sturaro logo" |

| ID | Media summary |
|---|---|
| F-16 | 3 of 13 items have alt text. Only media 22 has generated resized versions; the 2024 uploads report none. |
| — | None of the media is attached to a post or page. Media 5 and 13 are used in the custom `header-small-dark` part. |

---

## 3. Current privacy and SEO limitations

### 3.1 Verified

| ID | Finding |
|---|---|
| F-18 | **The site is private.** `blog_public` is `-1`. An anonymous request to `https://otaciliasturaro.com/` returns HTTP 200 with the page title **"Private Site"** and the WordPress.com login form. |
| F-19 | `robots.txt` is served as `User-agent: *` / `Disallow: /`, which blocks all crawling. |
| F-20 | `sitemap.xml` returns the private-site login page instead of a sitemap. |
| F-21 | **Conflicting signals about privacy.** The account's site list reports `is_private: false`, launched, not coming-soon. The site's settings report `is_private: true`, and the live response confirms the site is private. |
| F-22 | The public favicon is the generic WordPress.com icon (`s0.wp.com/i/webclip.png`), because no site icon is set. |
| F-23 | **SEO fields on HOME (page 25) are empty.** Jetpack's per-page fields exist but are blank: `advanced_seo_description`, `jetpack_seo_html_title`, `jetpack_seo_schema_type`. `jetpack_seo_noindex` is `false`. |
| F-24 | Permalinks are date-based, so post URLs include `/YYYY/MM/DD/`. |
| F-25 | No dedicated SEO plugin is installed, and no structured data is configured beyond whatever Jetpack outputs by default. |
| F-26 | Jetpack Search was turned off on 2026-10-18 (F-07). |
| F-27 | Only one category (Uncategorized) exists, and there's no topic structure. |

### 3.2 Limitations (not verifiable through the available tools)

| ID | Limitation |
|---|---|
| L-01 | hightechhighquality.com could not be audited because its Jetpack connection is disconnected. |
| L-02 | Jetpack's site-wide SEO settings (front-page meta description, title formats) and Search Console / Bing / Pinterest verification codes are not exposed by the MCP tools. |
| L-03 | Social-sharing tags (Open Graph, Twitter cards) and the homepage's real HTML output could not be checked, because the private-site screen replaces every public page. |
| L-04 | `www.otaciliasturaro.com` could not be tested. The audit sandbox's network proxy refused the connection, so this says nothing about the domain itself. |
| L-05 | Domain registration, DNS records, SSL details and email (MX) configuration were **intentionally not inspected**, per the audit rules. |
| L-06 | Synced patterns, the "Coming Soon" / launch status operations, monitoring, scanning, newsletter settings and account-protection status are disabled in the MCP settings, so they couldn't be read. |
| L-07 | The WordPress.com plan name and renewal date were not retrieved. The "atomic" hosting implies a Business-tier (or higher) plan, but this is **not verified**. |
| L-08 | Form submissions, analytics beyond WordPress.com Stats, and any third-party integrations (CRM, email marketing, scheduling) were not visible. |

---

## 4. Technical risks and dependencies

These are based on the verified findings above. Severity is the auditor's assessment.

| ID | Risk / dependency | Severity | Basis |
|---|---|---|---|
| T-01 | **Site isn't visible to visitors or search engines.** Launch needs privacy changed, and robots.txt and the sitemap must be checked afterward. | High | F-18, F-19, F-20 |
| T-02 | **The two sources disagree about privacy** (site list says public, settings say private). The reported launch status can't be relied on, so it needs to be confirmed in the dashboard before launch. | Medium | F-21 |
| T-03 | **Default WordPress content is the only published content.** If privacy were lifted today, visitors would see "Hello World!" as the homepage and sample text on the About page. | High | §2.1, §2.2, §1.3 |
| T-04 | **Demo content in the theme.** "The Hatchery… bird watching" would show on any page assigned the Page (Large Header) template. | Medium | F-17 |
| T-05 | **The automatic menu is fragile.** It lists every published page, so any new page appears in navigation unplanned. | Medium | §2.7 |
| T-06 | **Header duplicates the brand and leaves a gap.** The header shows an empty site-logo slot next to two hard-coded logo images, at 234px and 654px wide. Mobile layout is likely to suffer. | Medium | §2.6, F-22 |
| T-07 | **Heavy images.** One file is 4.6 MB and PNGs reach 4200px. The 2024 uploads have no smaller versions, which slows page loads. | Medium | §2.9 |
| T-08 | **Accessibility.** 10 of 13 images lack alt text. | Medium | F-16 |
| T-09 | **Spam exposure.** Comments and pingbacks are open site-wide with moderation off, and XML-RPC is enabled. | Low–Medium | §1.3 |
| T-10 | **Date-based permalinks.** Changing them after launch requires redirects. It is cheapest to settle now, while nothing is indexed. | Low (now) | F-24 |
| T-11 | **Ageing theme.** Twenty Twenty-Two dates from 2022, and redesign work may favor a newer block theme. Switching themes affects the 3 customized items (Blank template, header-small-dark, footer). | Low–Medium | §2.4–2.6 |
| T-12 | **Plugin overlap.** Gutenberg (a development plugin) and Page Optimize run on top of the platform's own editor and optimization. They could conflict with new layouts and need checking at build time. | Low | §2.8 |
| T-13 | **Recent re-provisioning.** The 2026-10-18 activity suggests a transfer or rebuild, so earlier settings may have been reset. | Low | F-06 |
| T-14 | **Single administrator.** One user account holds full control with no backup admin. | Low | F-02 |
| T-15 | **Write access depends on MCP settings.** Any implementation through this connection requires the owner to enable specific write operations. | Dependency | F-05 |
| T-16 | **HTHQ™ site disconnected.** Any cross-site architecture involving hightechhighquality.com requires reconnecting Jetpack first. | Dependency | F-04, L-01 |
| T-17 | **Missing legal pages.** There's no privacy policy, terms or investment disclaimer page, which an investment/advisory brand needs before launch. | High (pre-launch) | §1.3, §2.1 |
| T-18 | **No lead capture.** There's no contact page, form plugin or form block in use. | Medium | §2.1, §2.8 |

---

## 5. Existing assets that should be preserved

| ID | Asset | Location | Why keep it |
|---|---|---|---|
| A-01 | Domain `otaciliasturaro.com` and its current hosting (with SSH/SFTP access) | Site 231107304 | Primary brand domain, already mapped and active. **No DNS or email changes are proposed.** |
| A-02 | Tagline "Owner First. Advisor Second." | Settings | Current positioning statement, set by the owner on 2026-10-18 |
| A-03 | Logo `os-sahire-glow.png` | Media 5 | Primary logo file, with alt text |
| A-04 | Wordmark `otacilia-sturaro-chrome.png` and its edited/cropped versions | Media 6, 12, 13 | Brand wordmark variants |
| A-05 | Portrait photography: `os-side-headshot_hd.png`, `os-body-shot-hd.png`, `foto-nova.jpg`, the 2026 portrait | Media 8, 7, 18, 22 | Personal brand imagery. Media 22 is the newest upload. |
| A-06 | Other uploads: `image.jpeg`, `unknown.webp`, the 2024 screenshot | Media 19, 11, 17 | Content unknown from metadata alone. Keep until the owner reviews them. |
| A-07 | Beachfront real estate images | Media 9, 10 | Keep for reference. The filenames suggest stock or generated imagery (see Q-09). |
| A-08 | Customized `header-small-dark` and `footer` template parts | Site editor | They record the owner's earlier layout intent (dark header, logo + wordmark, no "powered by" credit). |
| A-09 | HOME draft (page 25), slug `home` | Pages | Reserved slug for the future front page. Empty, but owner-created. |
| A-10 | Jetpack backups and activity log | Platform | Backups have been confirmed working. They provide a rollback point before any implementation. |
| A-11 | hightechhighquality.com ("HTHQ FINANÇAS FREEDOM") | Separate site | Existing HTHQ™ web presence. Its status needs confirming (Q-03). |

---

## 6. Recommendations (not verified findings — not implemented)

> Everything in this section is a **proposal**. Nothing has been changed on WordPress.
> Each item needs owner approval (Section 7) and the relevant MCP write operations enabled before it can be carried out.

### 6.1 Pre-build hygiene

| ID | Recommendation | Addresses |
|---|---|---|
| R-01 | Keep the site private until content, legal pages and SEO are ready. Then launch deliberately and check robots.txt and the sitemap afterward. | T-01, T-02 |
| R-02 | Unpublish or replace "Hello World!" (post 2) and the sample About text (page 1). | T-03 |
| R-03 | Set a static front page (HOME, page 25) and a dedicated posts page (for example "Insights"). | T-03, §1.3 |
| R-04 | Change permalinks to `/%postname%/` before launch, while nothing is indexed. | T-10 |
| R-05 | Close comments and pingbacks site-wide unless the owner wants comments on Insights. Consider disabling XML-RPC if nothing uses it. | T-09 |
| R-06 | Replace the automatic page-list menu with a hand-built navigation menu. | T-05 |
| R-07 | Set the site logo and site icon properly, then remove the duplicate hard-coded logo images from the header. | T-06, F-22 |
| R-08 | Remove or replace the demo "Hatchery" header part, or avoid the Page (Large Header) template. | T-04 |

### 6.2 Design system

| ID | Recommendation | Addresses |
|---|---|---|
| R-09 | Decide whether to keep Twenty Twenty-Two or move to a newer block theme before building pages. If switching, migrate the 3 customized items first. | T-11 |
| R-10 | Define a brand palette and font pairing in Global Styles, which are currently empty, instead of relying on theme defaults. Align it with whatever the historical design audit established. | §2.4 |
| R-11 | Check whether the Gutenberg and Page Optimize plugins are still needed. Retire unused inactive plugins (Classic Editor, Crowdsignal, Layout Grid). | T-12 |

### 6.3 Media

| ID | Recommendation | Addresses |
|---|---|---|
| R-12 | Re-export brand images at web sizes (≤2000px, WebP or JPEG, under 300–500 KB) and give them descriptive filenames. | T-07 |
| R-13 | Add alt text to every image that is kept. | T-08 |
| R-14 | Replace generic or generated property imagery with real portfolio photography wherever possible. | A-07 |

### 6.4 SEO and compliance

| ID | Recommendation | Addresses |
|---|---|---|
| R-15 | Write a unique SEO title and meta description for every page. Use the Jetpack SEO fields, or approve an SEO plugin. | F-23, F-25 |
| R-16 | Add Person structured data for Otacilia Sturaro, and Organization data for HTHQ™ / ME VS ME™ if they are legal entities. | F-25 |
| R-17 | Set up a category structure for Insights (for example Investing, Global Markets, HTHQ™, ME VS ME™). | F-27 |
| R-18 | Create Privacy Policy, Terms and Investment / Not-Financial-Advice Disclaimer pages, with wording reviewed by the owner's counsel. Assign the privacy policy page in settings. | T-17 |
| R-19 | At launch, verify Google Search Console and submit the sitemap. | L-02 |
| R-20 | Add a contact or inquiry form with a spam filter. | T-18 |
| R-21 | Add a second administrator or recovery path for the account. | T-14 |

### 6.5 Proposed information architecture (draft for comparison)

This draft is to be reconciled with the historical design audit before the master architecture is approved.

```
Home
├─ About Otacilia            story, credentials, "Owner First. Advisor Second." philosophy
├─ Real Estate Investing     own portfolio / track record, approach, markets
├─ Advisory                  global advisory services, ideal client, process, engagement CTA
├─ HTHQ™                     overview page → hightechhighquality.com (or folded in; see Q-03)
├─ ME VS ME™                 program / philosophy, offer, waitlist or lead capture
├─ Insights                  posts page with the categories from R-17
├─ Media & Speaking          press, podcasts, speaking requests, media kit
└─ Contact                   inquiry form (investors / advisory clients / press), scheduling link
Footer: Privacy Policy · Terms · Disclaimer · social links · ©
```

Proposed homepage flow:
1. Hero with portrait and tagline
2. Three paths: Invest · Advise · Programs
3. Proof (track record, markets, credentials)
4. HTHQ™ and ME VS ME™ teasers
5. Latest Insights
6. Contact call to action

---

## 7. Questions requiring owner approval

| ID | Question | Related |
|---|---|---|
| Q-01 | Which MCP write operations may be enabled, and when? (For example: pages and posts as drafts only; navigation; global styles; template parts; settings.) | T-15 |
| Q-02 | What is the target launch date, and should the site stay private until then? | R-01, T-01 |
| Q-03 | Should **HTHQ™** live inside otaciliasturaro.com, stay on hightechhighquality.com, or both? If it stays separate, will you reconnect Jetpack on that site so it can be audited? | T-16, L-01, A-11 |
| Q-04 | Does **ME VS ME™** have its own domain, offer, pricing or sign-up flow that the site must integrate with? | §6.5 |
| Q-05 | Should Twenty Twenty-Two be kept, or may a newer block theme be evaluated? | R-09, T-11 |
| Q-06 | Are there approved brand colors, fonts and logo files beyond what is in the media library? Which logo and wordmark versions are canonical? | R-10, A-03, A-04 |
| Q-07 | May the "Hello World!" post and the sample About page be unpublished or replaced? | R-02 |
| Q-08 | May permalinks change to `/%postname%/`? | R-04 |
| Q-09 | Are the beachfront images (media 9, 10) real properties or stock/generated? May they be used publicly? | A-07, R-14 |
| Q-10 | What are media 11 (`unknown.webp`), 17 (2024 screenshot) and 19 (`image.jpeg`)? Keep, replace or retire? | A-06 |
| Q-11 | Should comments be enabled anywhere, such as on Insights posts? | R-05 |
| Q-12 | Is an SEO plugin acceptable, or should SEO stay within Jetpack's built-in fields? | R-15 |
| Q-13 | Who will supply and approve the legal wording (privacy policy, terms, investment disclaimer)? | R-18 |
| Q-14 | Which contact and lead-capture tools are in use or preferred (form, scheduling link, CRM, email list)? | R-20, L-08 |
| Q-15 | Which languages are in scope? The HTHQ™ site name is in Portuguese ("Finanças"). | §6.5 |
| Q-16 | Can you confirm the WordPress.com plan, and that the 2026-10-18 changes (F-06 to F-11) were intended? | L-07, T-13 |
| Q-17 | Should a second administrator be added? | R-21 |

---

*End of baseline audit. No changes were made to WordPress, DNS, domains or email while preparing this document.*
