# Portfolio site — structure & how to extend it

## Files
```
index.html                      → homepage (about, skills, project grid)
style.css                        → shared styles, used by the homepage
projects/
  style.css                      → same stylesheet, duplicated here so project pages
                                    don't rely on ../ path traversal
  project-template.html          → BLANK format — duplicate this for every new project
  loan-approval.html             → filled example (Loan Approval Case Study)
  retail-sales-db.html           → in-progress example (Retail Sales Database Design)
```

Two copies of `style.css` exist on purpose — one at the root for `index.html`, one inside
`projects/` for the project pages. If you change the design, edit both (or replace with a
single shared file and update the `<link>` paths — either works fine on GitHub Pages).

## Adding a new project
1. Copy `projects/project-template.html` into `projects/your-project-name.html`.
2. Fill in every `[bracketed placeholder]` — problem, data, approach, results, key takeaway, links.
3. Delete the `.stat-strip` block if the project has no headline numbers.
4. Open `index.html`, find the `<!-- Project card -->` section, and duplicate one `<a class="project-card">` block:
   ```html
   <a class="project-card" href="projects/your-project-name.html">
     <span class="status done">complete</span>  <!-- or class="status progress" -->
     <h3>Your Project Name</h3>
     <p>One-line description.</p>
     <span class="go">view case study →</span>
   </a>
   ```
5. Done — no build step, no npm. It's plain HTML/CSS.

## Deploying to GitHub Pages
1. Push this folder to a GitHub repo (e.g. `yourusername.github.io` for a root domain, or any repo name for a project page).
2. In the repo: **Settings → Pages → Source → Deploy from branch → main → / (root)**.
3. Your site goes live at `https://yourusername.github.io/` (or `.../repo-name/`).

## Before you publish
- Replace the placeholder email/GitHub/LinkedIn links in `index.html`'s Contact section.
- Fill in the `[N]` stat placeholders and `.placeholder` text blocks in the two example project pages.
