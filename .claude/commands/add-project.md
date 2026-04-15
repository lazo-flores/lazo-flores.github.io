# Add a New Project Card

Add a new project card to the AI Agent Projects section in `index.html`.

## Instructions

1. Ask the user for the following details:
   - Project name
   - Description (1-2 paragraphs)
   - Technologies used (for tech tags)
   - Image filename (to be placed in `images/`)
   - Live Demo URL (or "Coming Soon" if not ready)
   - View Code / GitHub URL (optional)

2. Create a new feature branch from `main`: `feature/add-project-<name>`

3. Add the project card to the Projects section (`id="projects"`) in `index.html`, following the existing card HTML structure:
   - Use the `col-6 col-12-narrow` grid pattern
   - Include `project-image` class on the `<img>` tag
   - Use `tech-tags` / `tech-tag` classes for technologies
   - Use the `button disabled` class for "Coming Soon" demos
   - Place the card in an existing row if there's only one card in the last row, otherwise create a new row

4. If adding a card that would be alone in its row, center it with `justify-content: center` on the row div.

5. Start the dev server (`python3 -m http.server 8000`) and ask the user to review.

6. After approval, commit, merge to `main`, and push.
