# Writing

```text
hugo server \
  --buildDrafts -D \  # Also render content set to draft:true
  --buildFuture -F \  # Also render content with a date (or publishDate) set in the future
  --verbose \         # Verbose output
  --watch             # Watch the filesystem for changes
```

Also see [hugo server](https://gohugo.io/commands/hugo_server/).

# Publishing

See [Deploy with Cloudflare Pages](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/#deploy-with-cloudflare-pages).
