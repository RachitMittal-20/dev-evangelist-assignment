# Friction Log — Raw Notes (SleekCMS Cold Build)

> Rules for using this file:
> 1. Log the MOMENT something happens — confusion, delight, surprise, dead end.
>    Don't wait, don't polish. One line is fine.
> 2. Use a timestamp + tag so it's easy to sort later: [HH:MM] [TAG] note
>    Tags: FRICTION / DELIGHT / DOCS-GAP / QUESTION / IDEA
> 3. If you had to open docs to figure something out, note WHAT you searched
>    and HOW LONG it took to find (or if you never found it).
> 4. Don't filter for "is this worth reporting" right now — that happens later.
>    Capture everything, prune in the report-writing phase.

---

## Day 1 — Signup & First Build

-[13:03] [FRICTION] homepage hero has a "Describe your website" prompt box as 
the primary CTA — no explanation of what SleekCMS actually is before asking 
you to act. New user has to scroll down to understand the product.

[13:03] [FRICTION] preset buttons show Bakery, Pizzeria, Café, Family winery, 
Personal trainer, Plant shop, Yoga studio — all business/local categories, 
no developer or portfolio option visible. Unclear if this is an AI site 
builder or a CMS.

[13:03] [QUESTION] tagline says "A real CMS, not vibe-code" — implies 
developer positioning but the UI looks like an AI website generator. 
Confusing mixed signal on first load.

[13:06] [FRICTION] "Get Started" button lands on a "Sign in to your account" 
page — not a signup page. New user has to hunt for "DON'T HAVE AN ACCOUNT? 
SIGN UP" link at the bottom. Primary CTA misleads new users.

[13:06] [DELIGHT] right panel clearly explains what SleekCMS is in 3 steps — 
headless CMS + static site builder, content modeling, API access. This is 
the clearest product explanation I've seen so far, but it's buried on the 
login page, not the homepage.

[13:08] [DELIGHT] after signup, dashboard immediately shows a "Skip the blank 
canvas" screen with templates and an AI builder option — no empty void, 
reduces new user paralysis.

[13:08] [FRICTION] no onboarding tour, checklist, or "here's what to do first" 
guidance — jumps straight to site creation. First-time user has no context 
about what SleekCMS concepts like "entries", "pages", "blocks" mean yet.

[13:08] [FRICTION] scroll down to check — no portfolio or developer template 
visible in first row. Templates seem content/blog focused (fashion, fitness, 
travel, literary). Developer building a portfolio has no obvious starting point.

[13:10] [FRICTION] scrolled through all templates — no portfolio template 
exists. Closest option is "tech-&-programming" which is a blog format, 
not a portfolio. Developer use case not represented in templates.

[13:11] [FRICTION] "Create Blank Site" modal asks for a "Clone Token" with no 
explanation of what it is or where to get one. New user has no idea if this 
is required or what it does. Tooltip says "optional" but no docs link.

[13:11] [FRICTION] blank site created and lands on "Models > Pages" tab — 
no welcome screen, no "start here" guidance, no explanation of what 
Models/Pages/Entries/Blocks/Options mean or how they relate to each other. 
Complete silence for a new user.

[13:11] [FRICTION] there is a "Home" page auto-created with "1 field" but 
no indication of what that field is, what to do with it, or what the 
difference between Pages/Entries/Blocks/Options tabs is. No tooltips visible.

[13:13] [FRICTION] clicking Home page shows a "fields" table with #, Type, 
Handle, Label columns — this is a content schema editor, not a page editor. 
No explanation that you're defining a data model, not writing content. 
New user expects to type content, not define fields.

[13:13] [FRICTION] only 1 auto-created field: "title" (type Abc = text). 
No guidance on what other fields to add for a homepage — bio, hero text, 
projects — completely blank slate with no suggestions.

[13:14] [DELIGHT] field type selector is comprehensive and well-labeled — 
Text, Rich Text, Markdown, Image, Collection, Reference, Code, Stack etc. 
Descriptions under each are clear. Good UX here.

[13:14] [FRICTION] no recommended fields or starter suggestions for common 
page types — new user has to know in advance what fields they need. 
No "for a portfolio homepage, try adding..." guidance.

[13:16] [FRICTION] Handle field does NOT auto-populate from the Label — 
user has to manually type both Field Label and Handle separately. 
Easy to make inconsistent naming mistakes, no auto-suggest.

[13:16] [DELIGHT] Handle field DOES auto-populate from Field Label with 
correct snake_case formatting — missed this on first field because I filled 
both manually. Small but solid UX detail.

[13:23] [DELIGHT] auto-fill handle handled "GitHub URL" correctly — 
generated "github_url" not "git_hub_url". Smarter than expected.

[13:25] [FRICTION] Collection field config has no way to define sub-fields 
inline — just Label, Handle, and "Multiple values?" toggle. No indication 
of how to define what each project item contains (title, description, link, 
stack). New user has no idea what to do next.



---

## Day 2 — Finishing Build & Publish

[HH:MM] [TAG]

---

## Scratch / things to double check later

