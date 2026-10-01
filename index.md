---
title: Home
layout: home
---

This is a starter template to create a [Jekyll] site that uses **Just the Games** — an interactive tabletop RPG reference built on the [Just the Docs] theme. You can easily set the created site to be published on [GitHub Pages] – the [README] file explains how to do that, along with other details.

If [Jekyll] is installed on your computer, you can also build and preview the created site *locally*. This lets you test changes before committing them, and avoids waiting for GitHub Pages.[^1] And you will be able to deploy your local build to a different platform than GitHub Pages.

More specifically, the created site:

- uses a gem-based approach, i.e. uses a `Gemfile` and loads the `just-the-docs` gem plus Just the Games plugins
- includes dice rolling, hover previews, clickable maps, TOC navigation, and RPG callouts
- uses the [GitHub Pages / Actions workflow] to build and publish the site on GitHub Pages

See a live example at [games.puzzledungeon.com](https://games.puzzledungeon.com/), or browse the [Make Your Own](https://games.puzzledungeon.com/docs/make-your-own) guides in this template to learn how to write adventures and rules in Markdown.

To get started with creating a site, simply:

1. click "[use this template]" to create a GitHub repository
2. go to Settings > Pages > Build and deployment > Source, and select GitHub Actions

If you want to maintain your docs in the `docs` directory of an existing project repo, see [Hosting your docs from an existing project repo](https://github.com/sunflowermans/just-the-games-template/blob/main/README.md#hosting-your-docs-from-an-existing-project-repo) in the template README.

----

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Just the Docs]: https://just-the-docs.github.io/just-the-docs/
[GitHub Pages]: https://docs.github.com/en/pages
[README]: https://github.com/sunflowermans/just-the-games-template/blob/main/README.md
[Jekyll]: https://jekyllrb.com
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/
[use this template]: https://github.com/sunflowermans/just-the-games-template/generate
