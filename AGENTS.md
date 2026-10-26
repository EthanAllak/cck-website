# AGENTS.md

## Project

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
