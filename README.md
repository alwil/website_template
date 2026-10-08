# Coding Cafe website template

This repository contains a template website for setting up your own Coding Cafe website. View the appearance of the website [here](https://code-cafes-nl.github.io/website_template/).

The website uses [Quarto](https://quarto.org), an open source publishing system that generates HTML websites from markdown documents. A GitHub Actions workflow renders the site automatically, so to update the website you only need to edit text files and push them.

## Prerequisites

To use the template you need:

- A [GitHub account](https://github.com/signup) (free).
- A basic way to edit text files. You can do this entirely in the GitHub web interface (the pencil icon on any file), or locally with an editor such as VSCodium, VS Code or RStudio.
- *Only if you want to preview the site on your computer:*
  - [Quarto](https://quarto.org/docs/get-started/) (free, one installer)
  - [Git](https://git-scm.com/downloads) to clone the repository (or use GitHub Desktop)

No programming knowledge is needed. Files ending in `.qmd` are markdown with a small header, and Quarto turns them into web pages.
The website uses Quarto, which is an open source publishing system that makes it possible to generate html websites from markdown documents. This repository comes with a GitHub actions workflow to automate the rendering of markdown to html, so to update the website you only need to edit markdown files.

## Setup instructions

1. In the top right, click **Use this template**.
2. Create a repository from this template under your organization or your own user account.
3. Open the repository **Settings → Pages**. Under *Build and deployment*, set **Source** to **GitHub Actions**.
4. Go to the **Actions** tab and check that the workflow has run (green tick). Your site will be at `https://<user-or-org>.github.io/<repository-name>/`.
5. Start customising your website (see below).

## What is where?

| File / folder | Purpose |
|---|---|
| `_quarto.yml` | Site configuration: title, navigation bar, logo, theme |
| `index.qmd` | Home page, including the "Next event" section |
| `about.qmd` | About page |
| `meetups/` | One file per event, plus the overview page |
| `assets/` | Images (`assets/img`) and calendar files (`assets/ics`) |
| `code-cafe.scss` | Colours and styling |
| `.github/workflows/` | Automatic build and deployment |

## Make it your own

1. Replace `[Insert name of programming cafe]` in `_quarto.yml`, `index.qmd` and `about.qmd` with your cafe's name.
2. Replace the logo in `assets/img/logo.png` (keep the same file name, or update the path in `_quarto.yml`).
3. Edit the text in `index.qmd` and `about.qmd`. Update the GitHub link in the navigation bar in `_quarto.yml`.

## Adding a new event

⚠️ *Verify file names and fields against the `meetups/` folder.*

1. Copy an existing event file in `meetups/` and give it a new name, e.g. `meetups/2025-03-12-intro-python.qmd`.
2. Edit the header (the part between the `---` lines) with the event details:

```yaml
   ---
   title: "Intro to Python"
   description: "A beginner-friendly walkthrough."
   date: 2025-03-12
   time: "16:00-17:00"
   location: "Room 1.23, Main Building"
   presenter: "Jane Doe"
   ---
```
3. Optional: add a calendar file (`.ics`) to `assets/ics/` so visitors can use "Add to calendar".
4. Commit and push. The event appears in the table on the **meetups** page, sorted by date. The "Next event" block on the home page shows the upcoming event.
   ⚠️ *State here whether the home page picks the next event automatically or must be edited by hand.*

## Changing the look of the website

- **Theme and colours:** `_quarto.yml` lists the base theme and `code-cafe.scss`. Change the colour variables at the top of `code-cafe.scss`, such as the primary colour and background.
- **Navigation bar:** edit the `navbar` section in `_quarto.yml` to add, remove or rename pages.
- **Adding a page:** create a new `.qmd` file and add it to the navbar in `_quarto.yml`.

Useful Quarto guides:

- [Website basics](https://quarto.org/docs/websites/)
- [Navigation](https://quarto.org/docs/websites/website-navigation.html)
- [HTML themes and Sass variables](https://quarto.org/docs/output-formats/html-themes.html)
- [Listings (the events table)](https://quarto.org/docs/websites/website-listings.html)

## Previewing and deploying

### Automatic deployment (default)

Every push to the `main` branch triggers the GitHub Actions workflow, which renders the site and publishes it. Progress is visible in the **Actions** tab. It usually takes a few minutes. If the run fails (red cross), open it to read the error message.

### Preview on your own computer

1. Install [Quarto](https://quarto.org/docs/get-started/) and Git.
2. Clone your repository:
```bash
   git clone https://github.com/<user-or-org>/<repository-name>.git
   cd <repository-name>
```
3. Start the live preview:
```bash
   quarto preview
```
   A browser tab opens and refreshes whenever you save a file.
4. To build the full site without previewing, run `quarto render`. The output goes to `_site/`, which is not committed.

When you are happy, commit and push your changes, and the site updates automatically.
- In the top right, click 'Use this template'
- Create a repository from this template under your organization or your own user account
- Change the setting for GitHub Pages: Open the repository 'settings', click 'Pages'. For the 'Build and deployment' source select 'GitHub Actions'.
- Now start working on your website!

> [!TIP]
> RStudio, VS Code and VSCodium have a "Preview" / "Render" button for Quarto files, so you don't have to use the command line.
## Troubleshooting

- **Site shows a 404:** check that Pages source is set to *GitHub Actions* and that the workflow has completed.
- **Changes not visible:** check the Actions tab for a failed run, then do a hard refresh (Ctrl/Cmd + Shift + R).
- **New event missing:** check the header formatting (indentation, quotes, a `---` line above and below) and the date format.

## Acknowledgements
> Clone the repository to your PC and edit files using your favorite code editor, VSCodium, Rstudio, etc. They typically have a 'preview' button that will open the website in a browser to see how your changes will look like.
This template is developed as part of the [CAFE (Code Along Feel Empowered) method](https://tdcc.nl/nes/projects/the-cafe-code-along-feel-empowered-method/) project, funded by the [NWO](https://www.nwo.nl/en) and [TDCC-NES](https://tdcc.nl/nes/) (Thematic Digital Competence Centre for Natural and Engineering Sciences).
