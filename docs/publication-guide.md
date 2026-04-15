# HyperJIS: publication checklist

Step-by-step for getting HyperJIS published across GitHub, the Karabiner community repo, and simone.org.

---

## 1. GitHub repo (smnrg/HyperJIS)

You already have the repo at github.com/smnrg/HyperJIS. Current state: README and LICENSE only, no config files, no releases.

**Steps:**

a. Clone your repo locally:
```bash
git clone git@github.com:smnrg/HyperJIS.git
cd HyperJIS
```

b. Delete the old README.md (we're replacing it):
```bash
rm README.md
```

c. Copy in all the new files from the download. Your repo should look like:
```
HyperJIS/
├── json/
│   ├── hyperjis-core.json
│   ├── hyperjis-accents-romance.json
│   ├── hyperjis-accents-french.json
│   ├── hyperjis-accents-spanish.json
│   └── hyperjis-accents-german.json
├── docs/
│   ├── hyperjis-diagram.svg
│   ├── ke-submission-notes.md
│   ├── blog-post.md
│   └── publication-guide.md
├── README.md
└── LICENSE
```

d. Commit and push:
```bash
git add -A
git commit -m "v1.0: core layout + modular accent system for 5 languages"
git push origin main
```

e. Create a GitHub release:
   - Go to github.com/smnrg/HyperJIS/releases/new
   - Tag: `v1.0`
   - Title: `HyperJIS v1.0`
   - Description: paste the first two paragraphs of the README
   - Publish release

f. Add repo metadata on GitHub:
   - Description: "Karabiner-Elements config: US layout + Vim + Hyper + multilingual accents on Apple JIS keyboards"
   - Website: https://simone.org (or your blog post URL once published)
   - Topics: `karabiner`, `karabiner-elements`, `keyboard-layout`, `jis`, `vim`, `macos`, `hyper-key`, `apple-keyboard`

---

## 2. Karabiner community repo (KE-complex_modifications)

This gets your rules listed on ke-complex-modifications.pqrs.org where Karabiner users browse for configs.

**Steps:**

a. Fork github.com/pqrs-org/KE-complex_modifications

b. Clone your fork:
```bash
git clone git@github.com:smnrg/KE-complex_modifications.git
cd KE-complex_modifications
```

c. Copy your JSON files into `public/json/`:
```bash
cp ~/HyperJIS/json/hyperjis-core.json public/json/
cp ~/HyperJIS/json/hyperjis-accents-romance.json public/json/
```
(Start with core + romance. Add the language extensions in a follow-up PR if the first ones get accepted.)

d. Remove `"comment"` fields from the JSON. These are non-standard and might get flagged:
```bash
# Check for comment fields
grep -n '"comment"' public/json/hyperjis-*.json
# Remove them manually or with sed
```

e. Edit `public/groups.json` and add entries. Find the "International" group (or the best-fitting one) and add:
```json
{ "path": "json/hyperjis-core.json" },
{ "path": "json/hyperjis-accents-romance.json" }
```

f. Build and test:
```bash
make
make server
# Open http://localhost:8000 and verify your rules appear
```

g. Commit (do NOT commit `public/build/dist.json`):
```bash
git add public/json/hyperjis-core.json public/json/hyperjis-accents-romance.json public/groups.json
git commit -m "Add HyperJIS core layout and Romance accent layer"
git push origin main
```

h. Open a PR against `pqrs-org/KE-complex_modifications`. Use the PR descriptions from `docs/ke-submission-notes.md`.

---

## 3. Blog post on simone.org

The blog post in `docs/blog-post.md` is ready to publish. It's written in Markdown.

**Steps:**

a. Copy the content from `docs/blog-post.md` into your CMS or static site generator

b. Add the keyboard diagram image. Either:
   - Upload `docs/hyperjis-diagram.svg` to your site's media
   - Or hotlink from GitHub: `https://raw.githubusercontent.com/smnrg/HyperJIS/main/docs/hyperjis-diagram.svg`

c. Add the diagram somewhere between "What it actually does" and the modifier cascade code block. The SVG works in both light and dark mode.

d. Check that the karabiner:// import links work. They should fire Karabiner-Elements directly. On mobile or non-Mac browsers, they'll be dead links, which is fine (your audience is on Macs).

e. Publish. Suggested URL: `simone.org/hyperjis` or `simone.org/blog/hyperjis`

---

## 4. Sharing and discoverability

After everything is live:

**Reddit:**
Post to r/mac, r/vim, r/MechanicalKeyboards, or r/Karabiner. Keep the post short: one paragraph about the problem, one about the solution, link to the blog post. Reddit hates self-promotion that looks like self-promotion, so frame it as "I built this for myself, figured others might use it."

**Hacker News:**
Submit the blog post URL. Title: "HyperJIS: US layout + Vim + multilingual accents on Apple JIS keyboards." HN likes opinionated tools with clear technical writing.

**Karabiner community:**
The KE-complex_modifications PR itself is distribution. Once merged, anyone browsing the Karabiner rules site can find and install your rules directly.

**Twitter/X:**
Short thread: screenshot of the keyboard diagram, one-line description, link. The diagram is the hook.

**simone.org:**
Add a link to HyperJIS in your site's projects section or footer. It's a good portfolio piece that shows how you think about systems.

---

## File inventory

| File | Purpose | Destination |
|---|---|---|
| `README.md` | GitHub repo landing page | repo root |
| `json/hyperjis-core.json` | Core layout rules (14 rules) | repo + KE PR |
| `json/hyperjis-accents-romance.json` | Base accent layer | repo + KE PR |
| `json/hyperjis-accents-french.json` | French extension | repo (+ KE later) |
| `json/hyperjis-accents-spanish.json` | Spanish extension | repo (+ KE later) |
| `json/hyperjis-accents-german.json` | German extension | repo (+ KE later) |
| `docs/hyperjis-diagram.svg` | Keyboard diagram | repo + blog post |
| `docs/blog-post.md` | Blog post for simone.org | your blog |
| `docs/ke-submission-notes.md` | KE PR reference | your reference |
| `docs/publication-guide.md` | This file | your reference |
