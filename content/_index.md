---
title: "Hugo Quickstart"
---

_This not the official docs.
I'm just distilling stuff to help myself and colleagues to create new sites in
the future._

# Getting started with Hugo

## What is Hugo

Hugo is a static site generator or static CMS based on Markdown.
You write Markdown and it generates HTML.
It is very handy for creating technical documentation and programming blogs
since embedding nice highlighted code is really easy.

### Example sites

Here are some pages I've made with Hugo.

- [Fluttered (book)](https://fluttered-book.github.io/)
- [Sikkerhed på spil](https://easv-it-sikkerhed.github.io/sikkerhed-paa-spil/)

## Install

### macOS / Linux

```sh
brew install hugo
```

### Windows

🤷

Do [this](https://wiki.archlinux.org/title/Installation_guide) then see above.

## Setup site

```sh
hugo new site <name>
cd <name>
git init
git add -A
git commit -m 'New hugo site'
```

Where `<name>` is what you want to call your site.

Find a theme you like on [Hugo Themes](https://themes.gohugo.io/).
Then install it.
Installing a theme generally just means adding it as a git submodule and
setting `theme` in `hugo.toml`.

Example: Say you want to use the [book theme](https://themes.gohugo.io/themes/hugo-book/), then you can install it like this:

```sh
git submodule add https://github.com/alex-shpak/hugo-book themes/hugo-book
echo "theme = 'hugo-book'" >> hugo.toml
```

_**NOTE**: some themes can require additional setup.
Please check the documentation for the theme._

## Workflow

Start a local web server with:

```sh
hugo server
```

Open the URL that gets printed to the terminal.

Add your content by creating `.md` files in the content directory.
Hugo will in most cases automatically refresh the page when you change files.

Try it out by adding a couple of pages.

```bash
cat > content/_index.md << EOF
# Index

[Another page](another/page)
EOF

mkdir content/another
cat > content/another/page.md << EOF
---
title: Another Page
weight: 1
---

# Another page
EOF
```

Notice your browser reloaded the page by itself.

You can also the hugo command to scaffold new pages.
Example: `hugo new content/page.md`

## How it works

Hugo watches the `content/` folder for changes.
A bit of JS (livereload.js) is injected into the page.
It creates a WebSocket that the Hugo server can use to instruct it to reload.

Hugo uses [Goldmark](https://github.com/yuin/goldmark/) to parse markdown.

You can add metadata to your content using Front Matter.
It is the stuff between the `---` at the top of your files.
For example:

- `title` sets the page title, displayed on browser tabs
- `weight` is used to set the order of pages.

See [Hugo front matter docs](https://gohugo.io/content-management/front-matter/) for more.

## Deployment

You can deploy pages build with Hugo however you like since it just generates static HTML.
Run `hugo build` and copy `public/` to your hosting of choice.

Personally, I like to just use GitHub Pages.
To automatically deploy on new commits, see [Host on GitHub
Pages](https://gohugo.io/host-and-deploy/host-on-github-pages/).

## Links

- [Markdown syntax](https://www.markdownguide.org/basic-syntax/)
- [Hugo documentation](https://gohugo.io/documentation/)
- [Hugo themes](https://themes.gohugo.io/)
