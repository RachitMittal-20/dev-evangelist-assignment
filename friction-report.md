# SleekCMS Onboarding Friction Report

**Submitted by:** Rachit Mittal  
**Date:** June 19, 2026  
**Live site:** https://rachit-mittal-portfo-mqkmena2.sleekcms.site  
**GitHub:** https://github.com/RachitMittal-20/dev-evangelist-assignment  

---

## 1. Timeline

| Phase | Time | Notes |
|---|---|---|
| Homepage & signup | ~8 min | Found signup buried under a login-first flow |
| Dashboard first look | ~5 min | No onboarding — landed cold on Models screen |
| Content modeling (fields) | ~20 min | Smooth once understood, but no guidance on what fields to add |
| Figuring out content entry | ~15 min | Biggest time sink — could not find where to fill content |
| Collection → Reference detour | ~20 min | Collection field had no sub-fields, had to rebuild with Entry + Reference |
| Template writing (EJS) | ~15 min | Straightforward for a developer |
| Styling with Tailwind/DaisyUI | ~10 min | Mostly smooth, one live vs preview discrepancy |
| Deploy | ~5 min | One click, very clean |
| **Total** | **~98 min** | Within the 2–3 hour budget |

The biggest unexpected time cost was not the build — it was navigating between Models, Content, and Builder to understand which screen does what. The mental model of how these three sections relate took significant trial and error to form.

---

## 2. Top Friction Points

### #1 — Content entry is completely undiscoverable from the Models screen

After defining fields in Models → Pages, there is no visible path to filling in content. The Home row has three icons: a code editor, a pencil (page settings), and a collapse toggle. None of these open a content form. The actual content editor lives under a separate "Content" section in the left sidebar — with no indication of this from the Models screen. I spent ~15 minutes clicking every icon on the Home row, checking the Entries tab, and opening the three-dot menu before accidentally finding it.

**Reproduction:** Create a blank site → define fields on a Page model → try to fill in content. There is no "Edit content" button, tooltip, or empty state hint pointing to the Content section.

**Impact:** High. Every new user who builds a page model will hit this wall. It breaks the mental flow of "define structure → add content."

---

### #2 — Collection field creates empty rows with no sub-fields

The Collection field type (described as "repeatable group of fields") does not allow defining what fields each item contains. Adding a Collection field and then opening the Content editor shows an expandable row that is completely blank inside. There is no UI to add sub-fields to a Collection, no error message, and no documentation link. The correct pattern — creating an Entry model and referencing it — is nowhere suggested in the UI.

**Reproduction:** Add a Collection field to any Page → go to Content → expand a collection row. It is empty with no way to add fields.

**Impact:** High. Any user building a portfolio, blog, or product listing (the most common use cases) will add a Collection and hit a dead end. Required significant reverse-engineering to discover the Entry + Reference pattern.

---

### #3 — "Get Started" CTA leads to a login page, not signup

The homepage's primary call to action is a button labeled "Get Started." Clicking it opens a page titled "Sign in to your account" with a signup link buried at the bottom as small secondary text: "DON'T HAVE AN ACCOUNT? SIGN UP." A first-time user coming from the homepage does not have an account — sending them to a login screen first creates immediate friction and confusion about whether free signup is even available.

**Reproduction:** Visit sleekcms.com as a new user → click "Get Started" → observe you land on a login screen.

**Impact:** Medium-high. This is the very first interaction. It signals to new users that the product is not expecting them.

---

### #4 — Preview does not auto-update after content changes

After saving content in the Content section, the Preview pane still shows the old (blank) state. There is a REBUILD button, but no indication that it needs to be clicked after content changes — only after template changes. I assumed the preview was broken for several minutes before trying REBUILD.

**Reproduction:** Fill in content → save → open Preview. Content does not appear. Must click REBUILD manually.

**Impact:** Medium. Adds confusion during the iterative content-filling phase. A simple "Content changed — rebuild to see updates" banner would fix this entirely.

---

### #5 — Live site renders differently from the in-app Preview

DaisyUI badge classes that rendered correctly in the SleekCMS Preview pane failed silently on the live deployed URL — skill badges collapsed into unstyled inline text. There was no warning, no build error, and no indication that certain Tailwind utility classes might not compile in production. Discovered only after opening the live URL in a separate browser tab.

**Reproduction:** Use DaisyUI badge classes (`badge`, `badge-lg`, `badge-outline`) in a template → preview looks correct → deploy → open live URL → classes are not applied.

**Impact:** Medium. For a developer this is debuggable, but it erodes trust in the Preview as a reliable representation of the live site.

---

## 3. Delights

**Deploy experience is exceptional.** One click from the Preview pane → "Your site is live!" with a working public URL. No server configuration, no DNS setup, no CI/CD pipeline to wire up. This is genuinely better than most platforms I've used. The build history panel with rollback capability was an unexpected bonus.

**Tailwind + DaisyUI pre-configured out of the box.** A blank site comes with Tailwind, the typography plugin, the forms plugin, and DaisyUI already wired in the CSS file. For a developer this removes significant boilerplate. I had a styled hero section working within minutes of finding the template editor.

**The field type selector is well-designed.** The "Select field type" modal has clear icons, short descriptions under each type, and a search box. Text, Rich Text, Markdown, Image, Collection, Reference, Code, Location — all immediately understandable without needing docs.

**Handle auto-fill is smart.** Typing a Field Label automatically populates the Handle in correct snake_case. It handled edge cases like "GitHub URL" → `github_url` correctly without mangling.

**The Context tab in the code editor is genuinely useful.** Clicking Context while in the template editor shows a live JSON preview of all field values, confirming the data structure in real time. This is the kind of developer tool that shows the team thinks about DX seriously.

---

## 4. Docs Gaps

**No explanation of the Models → Content → Builder relationship.** The three core sections of the product (Models for schema, Content for data, Builder for templates) are never explained together. There is no "How SleekCMS works" overview page. A new user has to reverse-engineer the mental model entirely through trial and error.

**Collection field has no documentation on sub-fields.** The field type is described as "repeatable group of fields" but there is no guide on how to actually make it repeatable with typed sub-fields. The correct pattern (Entry model + Reference field) is not surfaced anywhere near the Collection field UI.

**No quickstart for a portfolio or developer use case.** Every template in the gallery is a business or content site (café, bakery, fashion blog). There is no "developer portfolio" or "personal site" starter, and no quickstart guide targeting this use case. The product's tagline "A real CMS, not vibe-code" signals developer positioning, but the getting-started experience does not follow through on that.

**Preview vs live discrepancy is undocumented.** There is no documentation warning that certain Tailwind classes may not compile in production builds, or guidance on how to verify that template styles will render correctly on the live URL.

---

## 5. Top 3 Fixes

### Fix 1 — Add a "Edit Content" button directly on the Page model row

**Change:** On the Models → Pages screen, add a clearly labeled "Edit Content" button or link next to each page row that navigates directly to that page's content form in the Content section.

**Why first:** This is the single highest-friction moment in the entire onboarding. Every new user who creates a page model will stall here. It requires no architectural change — just a navigation shortcut. The fix is one afternoon of work and would eliminate the most common support question a new user would generate.

---

### Fix 2 — Show an inline guide when a Collection field is added with no sub-fields

**Change:** When a user opens the Content editor and expands a Collection row that has no sub-fields, show an inline callout: "This collection has no fields yet. To add fields to each item, create an Entry model and use a Reference field instead." Link to a docs page with a 3-step example.

**Why second:** The Collection → Reference pattern is the correct SleekCMS way to handle repeatable structured content, but it is completely non-obvious. The current experience is a silent dead end. This fix teaches the right pattern at exactly the moment the user needs it, without requiring them to find documentation.

---

### Fix 3 — Rename "Get Started" to "Sign Up Free" and route it to signup

**Change:** On the homepage, change the primary CTA button label from "Get Started" to "Sign Up Free" and route it directly to the signup form rather than the login page.

**Why third:** This is the very first interaction a prospective user has with the product. It signals whether the product is welcoming new users or treating them as an afterthought. The fix is a single label change and a route update — minimal effort, maximum first-impression impact.