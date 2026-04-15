# Add a New Platform Card

Add a new platform card to the AI Platforms & Ventures section in `index.html`.

## Instructions

1. Ask the user for the following details:
   - Platform name
   - User's role (Founder, Co-Founder & CTO, Creator, etc.)
   - Description (1-2 paragraphs about what the platform does)
   - Technologies used (for tech tags)
   - Image filename (to be placed in `images/`)
   - Platform URL (or "Coming Soon" if not live)
   - Whether to also add a Professional Experience entry for this platform (and if so, the start date and role description)

2. If the platform URL is provided, scrape the website to supplement the description with accurate details about features and value proposition.

3. Create a new feature branch from `main`: `feature/add-platform-<name>`

4. Add the platform card to the Platforms section (`id="platforms"`) in `index.html`, following the existing card HTML structure. If a card would sit alone in a row, center it with `justify-content: center` and `margin-top: 2em` on the row div.

5. If a Professional Experience entry is requested, add it at the top of the Experience section (`id="experience"`), before existing entries, with the role title, date range, and description.

6. Start the dev server (`python3 -m http.server 8000`) and ask the user to review.

7. After approval, commit, merge to `main`, and push.
