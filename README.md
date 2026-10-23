# Duly Qualified - Lead Engine Operations

This is the master operating manual and directory guide for the Duly Qualified infrastructure. 

## Directory Structure

* `engine/`: The core lead pipeline scripts (Overture data extraction, website audits, shortlist builders).
* `data/`: Raw geographical and industry data (e.g., Overture places for Nelson Mandela Bay).
* `profiles/`: Client configuration files (e.g., `covenant.yaml`, `covenant_overrides.yaml`).
* `runs/`: Output folders for specific client generation batches (e.g., `runs/covenant-2026-10-20/`).
* `Sites/`: Live client reports and Cloudflare Pages projects. Contains its own deployment `README.md`.
* `duly-qualified-hero.html`: The master template for the main public facing website.

## Environment Variables

Never hardcode secrets into the files or chat. Ensure these are set in your Windows user variables:
* `CLOUDFLARE_API_TOKEN`: Required for deploying client reports and the main site via Cloudflare Pages.
* `PAGESPEED_API_KEY`: Used by the website audit engine to evaluate target client websites.

## Client Delivery Workflow

**1. Onboarding**
* Receive payment and intake form (CSD number, target area, ideal profile).
* Create `profiles/[client_name].yaml`.

**2. Data Generation (Starter & Growth)**
* Run the pipeline from `engine/` to pull Overture data.
* Filter 15 to 20 highly qualified targets based on the client profile.
* Output results to `runs/[client_name]-[date]/`.

**3. Report Deployment**
* Compile the custom client report in `Sites/`.
* Test locally at 390x844 (mobile) and 1440x900 (desktop) to ensure UI quality.
* Deploy to Cloudflare Pages (refer to `Sites\README.md` for CLI commands).

**4. Tender Preparation (Growth Tier Only)**
* Scan local government portals (Nelson Mandela Bay Municipality, eTenders).
* Download relevant PDFs and extract mandatory MBD/SBD forms.
* Draft technical methodologies, health and safety plans, and compliance documents.
* Pass the drafted bid to the internal government contact for review and correction.
* Save review notes to the client profile to optimize future bid accuracy.

## Maintenance Notes

* Close all heavy background applications before running the `engine/` scripts to prevent memory bottlenecks.
* Always verify POPIA compliance before initiating first contact. No consent, no pitch.
