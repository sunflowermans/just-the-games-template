# just-the-games-template
iiii
This is a starter template to create a [Jekyll](https://jekyllrb.com) site that:

- uses **Just the Games** — interactive tabletop RPG references built on the [Just the Docs](https://just-the-docs.github.io/just-the-docs/) theme;
- can be built and published on [GitHub Pages](https://docs.github.com/en/pages);
- can be built and previewed locally, and published on other platforms.

More specifically, the created site:

- uses a gem-based approach, i.e. uses a `Gemfile` and loads the `just-the-docs` gem plus Just the Games plugins;
- includes dice rolling, hover previews, clickable maps, TOC navigation, and RPG callouts;
- uses the [GitHub Pages / Actions workflow](https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/) to build and publish the site on GitHub Pages.

See a live example at [games.puzzledungeon.com](https://games.puzzledungeon.com/).

To get started with creating a site, simply:

1. click "[use this template](https://github.com/sunflowermans/just-the-games-template/generate)" to create a GitHub repository
2. go to Settings > Pages > Build and deployment > Source, and select GitHub Actions

If you want to maintain your docs in the `docs` directory of an existing project repo, see [Hosting your docs from an existing project repo](#hosting-your-docs-from-an-existing-project-repo).

After completing the creation of your new site on GitHub, update it as needed:

## Replace the content of the template pages

Update the following files to your own content:

- `index.md` (your new home page)
- `README.md` (information for those who access your site repo on GitHub)
- `docs/` (replace the sample adventure and plugin guides with your own rules and adventures)



## Changing the version of the theme and/or Jekyll

Simply edit the relevant line(s) in the `Gemfile`.

## Adding a plugin

The Just the Docs theme automatically includes the `jekyll-seo-tag` plugin. This template also ships with Just the Games plugins in the `Gemfile` and `_config.yml`:

- `jekyll-dice-tray` — clickable dice notation and random tables
- `jekyll-hover-popup` — preview windows for internal links
- `jekyll-image-links` — clickable regions on maps and diagrams
- `jekyll-jtd-toc-nav` — document headings in the sidebar
- `rpg-callouts` — additional callout styles for RPG content
- `dark-dungeons-theme` — dark visual overlay for Just the Docs

To add an extra plugin, you need to add it in the `Gemfile` *and* in `_config.yml`.

Note: If you are using a Jekyll version less than 3.5.0, use the `gems` key instead of `plugins`.

## Publishing your site on GitHub Pages

1. If your created site is `YOUR-USERNAME/YOUR-SITE-NAME`, update `_config.yml` to:
  ```yaml
    title: YOUR TITLE
    description: YOUR DESCRIPTION
    theme: just-the-docs

    url: https://YOUR-USERNAME.github.io/YOUR-SITE-NAME

    aux_links: # remove if you don't want this link to appear on your pages
      Template Repository: https://github.com/YOUR-USERNAME/YOUR-SITE-NAME
  ```
2. Push your updated `_config.yml` to your site on GitHub.
3. In your newly created repo on GitHub:
  - go to the `Settings` tab -> `Pages` -> `Build and deployment`, then select `Source`: `GitHub Actions`.
    - if there were any failed Actions, go to the `Actions` tab and click on `Re-run jobs`.



## Building and previewing your site locally

Assuming [Jekyll](https://jekyllrb.com) and [Bundler](https://bundler.io) are installed on your computer:

1. Change your working directory to the root directory of your site.
2. Run `bundle install`.
3. Run `bundle exec jekyll serve` to build your site and preview it at `localhost:4000`.
  The built site is stored in the directory `_site`.



## Publishing your built site on a different platform

Just upload all the files in the directory `_site`.

## Customization

You're free to customize sites that you create with this template, however you like!

[Browse the Just the Docs documentation](https://just-the-docs.github.io/just-the-docs/) to learn more about the base theme, and see this template's [Make Your Own](https://github.com/sunflowermans/just-the-games-template/tree/main/docs) guides for adventure authoring and plugin features.

## Hosting your docs from an existing project repo

You might want to maintain your docs in an existing project repo. Instead of creating a new repo using the [just-the-games template](https://github.com/sunflowermans/just-the-games-template), you can copy the template files into your existing repo and configure the template's Github Actions workflow to build from a `docs` directory. You can clone the template to your local machine or download the `.zip` file to access the files.

### Copy the template files

1. Create a `.github/workflows` directory at your project root if your repo doesn't already have one. Copy the `pages.yml` file into this directory. GitHub Actions searches this directory for workflow files.
2. Create a `docs` directory at your project root and copy all remaining template files into this directory.



### Modify the GitHub Actions workflow

The GitHub Actions workflow that builds and deploys your site to Github Pages is defined by the `pages.yml` file. You'll need to edit this file to that so that your build and deploy steps look to your `docs` directory, rather than the project root.

1. Set the default `working-directory` param for the build job.
  ```yaml
    build:
      runs-on: ubuntu-latest
      defaults:
        run:
          working-directory: docs
  ```
2. Set the `working-directory` param for the Setup Ruby step.
  ```yaml
    - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.3'
          bundler-cache: true
          cache-version: 0
          working-directory: '${{ github.workspace }}/docs'
  ```
3. Set the path param for the Upload artifact step:
  ```yaml
    - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: docs/_site/
  ```
4. Modify the trigger so that only changes within the `docs` directory start the workflow. Otherwise, every change to your project (even those that don't affect the docs) would trigger a new site build and deploy.
  ```yaml
    on:
      push:
        branches:
          - "main"
        paths:
          - "docs/**"
  ```



## Licensing and Attribution

This repository is licensed under the [MIT License](https://en.wikipedia.org/wiki/MIT_License). You are generally free to reuse or extend upon this code as you see fit; just include the original copy of the license (which is preserved when you "make a template"). While it's not necessary, we'd love to hear from you if you do use this template, and how we can improve it for future use!

The deployment GitHub Actions workflow is heavily based on GitHub's mixed-party [starter workflows](https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml). A copy of their MIT License is available in [actions/starter-workflows](https://github.com/actions/starter-workflows/blob/main/LICENSE).

This template is adapted from [just-the-docs-template](https://github.com/just-the-docs/just-the-docs-template).

---

[^1]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).
