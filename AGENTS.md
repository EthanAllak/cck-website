# AGENTS.md

## Project

<<<<<<< HEAD
- This is the website for Creative Code Kortrijk (CCK), a creative coding club in Kortrijk, Belgium.
- The audience is artists, designers, programmers and anyone curious about creative coding, from
  beginners to experienced makers.
- The site presents the club's workshops, its foundations (core values), its team and its news.
- The pages are home (`/`), about (`/about`) and news (`/news`), plus a detail page for each
  workshop, foundation and team member.
- The content is placeholder copy. `src/pages/about.md` says so itself ("This is all fake.").
- The visual design is in Figma (link in `readme 4.md`), based on the Positivus community landing
  page. The illustrations come from pixels.market (Doodledo).
- The repository is a team exercise ("Git Party") built by three students who use GitHub Flow, with
  one feature branch per task.

## Stack & constraints

- Astro 7 (`astro@^7.4.0`) is the only framework dependency. There is no UI framework (React, Vue,
  ...) and no integrations in `astro.config.mjs`.
- No CSS framework is used. Styling is plain CSS in `src/styles/` (`reset.css`, `global.css`,
  `markdown.css`) plus scoped `<style>` blocks in `.astro` files.
- `global.css` defines custom properties for colors (`--color-primary: #B9FF66`, ...), a fluid type
  scale (`--fs-*`) and fluid spacing (`--sp-*`), all built with `clamp()`.
- The font is Space Grotesk Variable, loaded through `@fontsource-variable/space-grotesk` in
  `src/layouts/Base.astro`.
- The content lives in Astro content collections defined in `src/content.config.ts`. Each one uses
  the `glob` loader on `src/content/<name>/**/*.md`, and schemas are written with `astro/zod`:
  - `workshops`: `title` (string), `image` (image)
  - `foundations`: `title` (string), `description` (string)
  - `team`: `name`, `function`, `bio` (strings), `pic` (image)
- A missing or invalid frontmatter field fails the build.
- Images referenced from frontmatter sit next to the content in `img/` folders and go through
  Astro's `image()` helper.
- A `news` collection is planned but not defined yet. Its source items are in `resources/news/`.
- Starter files for the detail pages are in `resources/{workshops,foundations,team}/detailpage`.
  Each detail page uses the entry id as its dynamic route parameter.
- The code still contains placeholders of the form `##WHAT-SHOULD-BE-HERE##` in components, pages
  and content files.
- Layouts: `Base.astro` (header, main slot, footer) and `Markdown.astro` (for `.md` pages).
- TypeScript extends `astro/tsconfigs/base` with `strictNullChecks` on.
- Scripts: `npm run dev` (`astro dev --host`), `npm run build`, `npm run preview`.
=======
- Website for Creative Code Kortrijk (CCK), a new creative coding club in Kortrijk, Belgium.
- Audience: artists, designers, programmers and curious beginners of all skill levels who want
  to explore the intersection of art and code.
- The site presents the club's workshops, foundations (core values), team members and news, plus
  an About page and a `/code` page where visitors enter a 4-digit code hidden across the site.
- Built as a team assignment (Web 3 "Git Party") by three students, each working on their own
  feature branch with their own agent, merged into `main` via GitHub Flow pull requests.
- Design source: Figma (CCK file, based on the "Positivus" community landing page); illustrations
  from pixels.market "doodledo".

## Stack & constraints

- Astro 7 (`astro` ^7.4.0), static site, ES modules (`"type": "module"`).
- TypeScript config extends `astro/tsconfigs/base` with `strictNullChecks` on.
- Content lives in Astro content collections defined in `src/content.config.ts`, loaded with the
  `glob` loader from `src/content/<collection>/*.md` and validated with Zod schemas:
  - `workshops`: `title`, `image`
  - `foundations`: `title`, `description`
  - `team`: `name`, `function`, `bio`, `pic`
  - `news`: not yet defined; sample items are in `resources/news/`.
- A missing frontmatter field in a markdown file makes the build fail.
- Images referenced from frontmatter live next to the content in `src/content/<collection>/img/`
  and use the schema `image()` helper.
- Pages in `src/pages/` (`index.astro`, `news.astro`, `about.md`); layouts in `src/layouts/`
  (`Base.astro`, `Markdown.astro`); components in `src/components/`.
- Detail page starters for each collection are in `resources/<collection>/detailpage`; detail
  pages use the entry id as a dynamic route parameter.
- Starter code contains placeholders of the form `##WHAT-SHOULD-BE-HERE##`.
- No CSS framework: plain CSS in `src/styles/` (`reset.css`, `global.css`, `markdown.css`) plus
  scoped `<style>` blocks in components. Design tokens are CSS custom properties (`--color-*`,
  fluid `--fs-*` type scale, `--sp-*` spacing scale).
- Font: Space Grotesk via `@fontsource-variable/space-grotesk` (the only other dependency).
- Scripts: `npm run dev` (with `--host`), `npm run build`, `npm run preview`.
- Deployment target: GitHub Pages via the Astro GitHub Actions workflow, deployed on changes to
  `main`.
>>>>>>> origin/main
