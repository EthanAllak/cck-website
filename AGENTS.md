# AGENTS.md

## Project

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
