# README

## Download submodule theme

```text
# https://git-scm.com/book/en/v2/Git-Tools-Submodules#_cloning_submodules
git submodule init && \
  git submodule update
```

## Writing

```text
hugo server \
  --buildDrafts -D \  # Also render content set to draft:true
  --buildFuture -F \  # Also render content with a date (or publishDate) set in the future
  --logLevel info  \  # Display information, warning, and error messages
  --watch             # Watch the filesystem for changes
```

Also see [hugo server](https://gohugo.io/commands/hugo_server/).

## Publishing

See [Deploy with Cloudflare Pages](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/#deploy-with-cloudflare-pages).
