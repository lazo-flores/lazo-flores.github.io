# Update Website Content

Make content updates to the website following the branch-review-merge workflow.

## Instructions

1. Ask the user what content they want to update. Common updates include:
   - Section text (About Me, Experience, Contact, etc.)
   - CV/Resume PDF in `documents/`
   - Profile or project images in `images/`
   - External links (demo URLs, GitHub repos, platform URLs)
   - Navigation bar entries
   - Technology tags on project/platform cards

2. Create a new feature branch from `main`: `feature/update-<short-description>`

3. Make the requested changes in `index.html`. Key reference points:
   - Header tagline: search for `id="header"`
   - About Me: search for `id="about"`
   - Experience: search for `id="experience"`
   - Platforms: search for `id="platforms"`
   - Projects: search for `id="projects"`
   - Contact: search for `id="contact"`
   - Navigation: search for `id="nav"`
   - Custom styles: inline `<style>` block at the top of the file

4. Start the dev server (`python3 -m http.server 8000`) and ask the user to review.

5. After approval, commit, merge to `main`, and push.
