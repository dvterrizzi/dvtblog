# www.dvt.life
Repository for my personal website.

## Build
The website is built using Jekyll with `jekyll [build|serve]`
This will take the HTML files, SCSS files, Markdown posts and YML data files to generate a static website. 

The resulting output will be stored under the `_site` subfolder, which is excluded from the repository by the Jekyll template `.gitignore` file.

### Gemfile
Apparently there is a `github-pages` gem which wraps the `jekyll` gem with a couple of extra features, like checking the GitHub Pages DNS challenge from the CLI. I've ran into multiple issues using it (building, deprecated Sass compiler), so I've decided to not use it.

The only way to get GitHub Actions to build the repo when using the (now unused) `github-pages` gem, is by removing the `Gemfile.lock` file from the repo and adding it to `.gitignore`. This file is created when running `bundle` from the CLI to install the gems.

TODO: Get the repo building on my Mac.

### SCSS
Using `@import "partial"` has been deprecated and partials should instead be imported using `@use` where they are assigned a namespace to prevent conflicting variable names. The global namespace `*` can also be used, but is not advised. 

```scss
@use "colors" as colors;

#myElement { font: colors.$main; }
```

As stated above, only the `jekyll` gem contains the modern DartSass compiler that supports this.

## Deploy
GitHub Actions is uesd to build the repo and deploy the generated static site to GitHub Pages, which is linked to the `www.dvt.life` domain.