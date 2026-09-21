# Profile artwork

The README uses native GitHub Markdown, `picture`, `img`, and nested `details`.
The illustrations are self-contained SVGs: no JavaScript, fonts, tracking,
third-party image services or external resources. Bit is an animated replay;
the expandable debugging puzzle supplies the interaction.

## Daily refresh

`.github/workflows/contributions.yml` runs at 09:23 UTC (06:23 in Brasilia),
on relevant pushes to `main`, or via **Actions → Bit's daily patrol → Run workflow**.
No personal access token or custom secret is needed. The built-in `GITHUB_TOKEN`
reads the contribution calendar through GitHub GraphQL and commits updated SVGs.
Only `contents: write` is granted, at job scope. Checkout is the sole external
Action and is pinned to the verified v6.0.2 commit.

The graph covers the current UTC week and the preceding 15 weeks, with Sunday
at the top of each column. Counts and intensity levels come from GitHub;
future days are omitted. This is a rolling window, not an annual statistic.
Both themes share the same dates and route. CSS honors reduced motion, and
the artwork stays meaningful in renderers that do not play SVG animation.

The script validates the entire response before writing images. API errors
fail the job and leave the last committed artwork available. A concurrency
group serializes updates, unchanged output produces no commit, and artwork
commits do not trigger another refresh. Branch rules that block bot pushes
will also block publishing; failures appear in Actions rather than being hidden.
GitHub schedules can be delayed or disabled after 60 days of public-repository
inactivity. Re-enable the workflow in Actions if GitHub disables it.

For local development with Node 22 or later:

```sh
node --test scripts/arcade.test.mjs
# Optional regeneration: provide a GitHub token as GH_TOKEN in your environment.
node scripts/arcade.mjs
```

## Content decisions

Reviewed the public profile and the 16 public repository entries on 2026-09-21.
Inspected manifests, READMEs and source files in the non-empty original projects.
The three featured pairs offer the clearest examples beyond framework tutorials:

- `lytex-back` / `lytex-front`: NestJS, Mongoose, JWT, invoice integration,
  Angular routes and charge management.
- `front-end` / `back-end`: Nuxt, Vue, Pinia, localStorage cart, Laravel product
  filters and validation. Laravel's local default is SQLite; no MySQL claim.
- `vr-api` / `vr-web`: NestJS, PostgreSQL/TypeORM, product pagination,
  store associations and the Angular product/pricing interface.

Professional experience since 2022 and the domains come from the existing
profile README; they are not inferred from commit history. The LinkedIn URL
matches both the public profile and the original README. Docker, MySQL and Go
were omitted from the compact stack because the featured source does not
justify prioritizing them. No unverified performance or production claims,
language percentage cards, streak rankings or badge walls were added.

References: [GitHub image syntax](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-advanced-formatting-syntax),
[collapsed sections](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-collapsed-sections),
[workflow syntax and permissions](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax),
[scheduled events](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule).
