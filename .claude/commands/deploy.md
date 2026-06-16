# Deploy Website Changes

Commit current changes, merge to `main`, push to GitHub Pages, then wait for the build and verify the site is live.

## Instructions

1. Run `git status` and `git diff --stat` to review. Stage only relevant files. **Never stage `.DS_Store`** or local-only files (e.g. `repo_session_*.md`).
2. Write a concise commit message summarizing the change. If on a feature branch, commit there, then `git checkout main` and `git merge --no-ff <branch>`.
3. **Push as the repo owner.** This repo is `lazo-flores/lazo-flores.github.io`. If `git push` returns `403 ... denied to enablemate-dev`, run `gh auth switch --user lazo-flores` and push again. The `enablemate-dev` account is usually the active gh account and lacks write access here. (See the `reference_gh_push_account` memory.)
4. **Wait for the GitHub Pages build, then verify live:**
   - Poll `gh api repos/lazo-flores/lazo-flores.github.io/pages/builds/latest --jq '.status + " " + .commit'` until `status` is `built` on the commit you just pushed (usually 1 to 3 minutes; poll roughly every 60 to 120s).
   - Check routes return 200 (cache-bust with a `?cb=<timestamp>` query): `/`, `/consulting.html`, and each `/blog/<slug>/`.
   - Confirm no em-dashes shipped on the changed pages: fetch each and run `perl -ne 'print if /\x{2014}/ or /&mdash;/'` (must print nothing).
5. Report the live URL(s) back to Jose. If a blog post was published, share its `/blog/<slug>/` URL explicitly.

## Notes

- GitHub Pages is static: there are no server-side redirects. Preserve `/blog/...` paths by not moving the post files. (See the `project_blog_rolling_release` memory.)
- `index.html` uses CRLF line endings, which can break the Edit tool's exact-match. Use byte-aware edits there. (See the `reference_index_crlf` memory.)
- Default branch is `main`; pushing to it triggers the Pages deploy automatically.
