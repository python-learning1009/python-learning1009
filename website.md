# DATA1009 Website Maintenance Guide

This file records how the course website is organized and how to update it consistently.

## Live site and publishing

- Live website: https://python-learning1009.github.io/python-learning1009/
- GitHub repository: https://github.com/python-learning1009/python-learning1009
- Publishing source: `main` branch, repository root (`/`)
- The site is plain static HTML, CSS, and JavaScript. No build step is required.

After an update, publish the changed files to the `main` branch and wait for GitHub Pages to finish. Confirm the live page contains the new content before considering the update complete.

## Main files

- `index.html`: page content, sections, links, and downloadable materials
- `styles.css`: typography, colors, layout, responsive rules, and component styling
- `script.js`: mobile navigation behavior
- `.nojekyll`: keeps GitHub Pages from applying Jekyll processing
- Course documents: stored in the repository root and linked with relative URLs
- Large slide decks: stored as assets in the `course-slides-2026` GitHub Release

## Topic slide mapping

| Topic | Slide file | Release asset URL ending |
| --- | --- | --- |
| 01 — Introduction to Programming | `Pythonlearn-01-Intro.pptx` | `/Pythonlearn-01-Intro.pptx` |
| 02 — Data Types | `Pythonlearn-02-Data Types.pptx` | `/Pythonlearn-02-Data.Types.pptx` |
| 03 — Expressions and Statements | `Pythonlearn-03-Expressions.pptx` | `/Pythonlearn-03-Expressions.pptx` |
| 04 — Conditional Execution | `Pythonlearn-04-Conditional.pptx` | `/Pythonlearn-04-Conditional.pptx` |

Topic resources appear inside the matching `<li>` in `.topic-list` as an anchor with class `topic-slide`. The full URL pattern is:

`https://github.com/python-learning1009/python-learning1009/releases/download/course-slides-2026/<encoded-filename>`

The Release is used because `Pythonlearn-01-Intro.pptx` is larger than GitHub's 25 MB browser-upload limit for repository files. Keep all course slide decks together in this Release and upload the original files without recompressing them. GitHub normalizes the space in `Pythonlearn-02-Data Types.pptx` to a period in the published asset name, so its link must end in `Pythonlearn-02-Data.Types.pptx`.

## Typography hierarchy

Section and card headings should remain visually distinct from explanation text, while the main section headings stay compact.

- Page title: `.hero h1`
- Section number labels: `.section-number`, set to `1.1rem` so the `01 / Overview` through `05 / Materials` series stays prominent
- Main section titles: `.section-heading h2` and `.project-header h2`, using the half-size responsive value `clamp(1.4rem, 2.9vw, 2.6rem)`
- Topic titles: `.topic-list h3`
- Card and subsection titles: `.person-card h3`, `.outcomes h3`, `.project-steps h3`, `.deliverables h3`, and `.file-card h3`
- Explanations remain regular body text (`p`) and should not visually compete with headings

Use the existing responsive `clamp(...)` values when changing large headings. Keep body text at least `1rem` when it is essential course information.

The Overview section intentionally has only the `01 / Overview` label and no `h2`. Current section copy includes `Eleven sessions.` for Topics and `Build something interesting together` for the group project. Assessment remains `How your work is evaluated`, and Materials remains `Course files and learning resources`.

## Adding or changing content

1. Put the new document or slide file in the website folder.
2. For a normal document, add or update its relative link in `index.html`. For a slide deck, upload it as an asset in the `course-slides-2026` Release and use the Release asset URL.
3. Reuse an existing CSS class before creating a new one.
4. Check desktop and mobile layouts; topic rows collapse to two columns below `680px`.
5. Start a local preview from this folder with `python3 -m http.server 4173` and open `http://127.0.0.1:4173/`.
6. Test every new download link and confirm the linked file exists and is not empty.
7. Publish the changed source and assets to `main`, then verify the live GitHub Pages URL.

## Style conventions

- Preserve the navy/cyan course palette defined in `:root`.
- Keep section numbering (`01 / Overview`, `02 / Topics`, etc.) in monospace uppercase labels.
- Use semantic headings in order: one `h1`, section `h2` headings, and card/topic `h3` headings.
- Keep descriptive text concise and visually smaller than its heading.
- Maintain accessible link text such as `Download slides`; do not use an icon alone.
- Preserve keyboard navigation, the skip link, responsive navigation, and reduced-motion support.

## Current project notes

- Group presentations are scheduled for October 26 and 28; presentation order is determined by random draw.
- Existing course documents and recommended external resources should remain available when other sections are edited.
