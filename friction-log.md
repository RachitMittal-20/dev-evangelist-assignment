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

[13:33] [FRICTION] Entries tab is empty with no connection to the Home page 
model just built — no indication that "NEW ENTRY" here will let you fill 
in the Home page fields. Relationship between Models and Entries is unclear 
to a new user.

[13:33] [FRICTION] clicking "+ NEW ENTRY" opens "New content model" — not 
a content entry form. Expected to fill in my homepage content, instead 
being asked to create another model. Entries tab does not connect to the 
Home page model already built. Completely confusing — two separate concepts 
with no explanation of the difference.

[13:36] [FRICTION] clicking the Home row collapses/expands fields — not 
obvious that the pencil icon is needed to edit page settings. No "fill 
content" button visible anywhere on this screen. New user cannot find 
where to actually enter content for the homepage.

[13:38] [FRICTION] "PREVIEW" button does not show a visual preview — it 
stays on the same screen. The actual site builder is accessed via a code 
icon (</>) next to the pencil icon on the Home row, not via PREVIEW. 
Completely non-obvious. New user would never find this.

[13:38] [FRICTION] clicking the code editor opens an EJS template file 
"/views/pages/_index.ejs" with just one line: <h1><%= item.title %></h1>. 
This is a code editor, not a visual builder. SleekCMS requires writing 
EJS templates to build pages — this is NOT a no-code tool despite the 
homepage implying otherwise.

[13:42] [DELIGHT] code editor has syntax highlighting, line numbers, and 
clean EJS rendering — comfortable for a developer to work in.

[13:43] [DELIGHT] Context tab shows a live data preview of all fields — 
can see title, hero_heading, bio, bio_short, avatar, github_url, 
linkedin_url, projects all showing "null" — confirms fields are connected 
to the template correctly but content not yet filled in.

[13:44] [FRICTION] no way to fill in page content from the Models view — 
clicking the Home row only collapses/expands fields. Pencil opens page 
settings. Code icon opens template editor. Curly braces collapses fields. 
Zero path to actual content entry from this screen.

[13:45] [FRICTION] three dots menu on Home row shows only "JSON to fields" 
and "Delete model" — no "Edit content" or "Fill in content" option anywhere 
in the Models view. Content entry path is completely hidden from this screen.

[13:48] [FRICTION] content entry form is under "Content" in the left 
sidebar — completely separate from Models, Builder, and Integrate sections. 
Took significant exploration to find. No indication from the Models screen 
that "Content" is where you fill in page data. New user would waste 
significant time searching.

[13:48] [DELIGHT] once found, Content screen shows a clean form with all 
8 fields correctly labeled and ready to fill — Title, Hero Heading, Bio, 
Bio Short, Avatar, GitHub URL, LinkedIn URL, Projects. Exactly what was 
needed.

[13:52] [DELIGHT] content save shows a clean "updated" popup confirmation — 
simple and clear.

[13:53] [FRICTION] preview still blank after filling in content and saving — 
shows "13 minutes" next to DEPLOY button suggesting last build was 13 minutes 
ago. Content changes don't auto-rebuild the preview. No indication that 
REBUILD is required after content changes.

[13:55] [DELIGHT] content renders correctly after REBUILD — all fields 
showing: hero heading, bio short, about section, bio, projects section. 
EJS template is working correctly.

[13:55] [FRICTION] text is completely unstyled — no CSS applied, all 
content runs together with no visual hierarchy. No default styles provided 
for a blank site. Developer must write all CSS from scratch.

[13:55] [FRICTION] "Full-Stack Developer & AI Builder" hero heading is 
overlapping with the bio text — layout broken because there is no CSS. 
Confusing for new users who expect at least minimal default styling.

[13:57] [DELIGHT] CSS file is pre-configured with Tailwind CSS, typography 
plugin, forms plugin, and DaisyUI — powerful setup out of the box. No 
manual Tailwind configuration needed.

[13:58] [DELIGHT] Tailwind + DaisyUI classes render correctly in preview — 
hero section, buttons, about section, and project card all styled properly 
with zero custom CSS written. Powerful out of the box.

[13:58] [FRICTION] Projects section shows a card with only "View Project" 
button and no title or description — because project sub-fields (title, 
description, link) were never defined inside the Collection field. No 
guidance on how to add sub-fields to a Collection.

[14:00] [FRICTION] clicking + on Projects collection adds a new "Projects" 
row but it's completely empty — no sub-fields to fill in (no title, 
description, link). Collection field has no defined schema for its items. 
New user has no idea how to add fields to a collection item.

[14:01] [FRICTION] Collection items have no sub-fields — expanding a 
Projects row shows nothing. Collection field type creates repeatable 
rows but provides no way to define what fields each row contains. 
This is a significant docs gap — no explanation of how to structure 
collection items anywhere in the UI.

[14:04] [FRICTION] editing a Collection field only shows Label, Handle, 
and "Multiple values?" toggle — no way to add sub-fields to the collection 
from here. Collection sub-fields cannot be defined through the field editor. 
Completely undiscoverable.

[14:05] [FRICTION] Reference field requires selecting an existing "entries 
schema record" from a dropdown — but no entries schema exists yet. Must 
first create an Entry model before a Reference field can be added. 
Circular dependency with no guidance on correct order of operations.

[14:07] [DELIGHT] empty Entry model shows a helpful empty state with 
"Your fields will be shown here" and a "MODEL BUILDER" option — 
better onboarding than the blank Pages model screen.

[14:16] [DELIGHT] Reference field auto-shows all created project entries 
as selectable options — all 3 projects already linked with checkmarks. 
No manual wiring needed.

[14:18] [DELIGHT] project cards render perfectly in 3-column grid with 
DaisyUI card styling — ContentIQ, Sentiment Analyser AI, and NoirBrew 
all showing correct content pulled from Reference entries.

[14:20] [DELIGHT] deploy modal clearly explains the choice — free subdomain 
vs custom domain, with a pre-filled subdomain. Clean and simple. No server 
configuration needed.

[14:22] [DELIGHT] "Your site is live!" confirmation modal with green 
checkmark and direct URL — clean, satisfying deploy experience. 
One click from preview to public URL.

---

## Day 2 — Finishing Build & Publish

[HH:MM] [TAG]

---

## Scratch / things to double check later

