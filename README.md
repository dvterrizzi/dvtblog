# Introduction<a name="intro"></a>
Repository for my personal website at https://www.dvt.life

# Table of contents
- [Introduction](#introduction)
- [Table of contents](#table-of-contents)
- [Build](#build)
  - [Gemfile](#gemfile)
  - [SCSS](#scss)
  - [TODO](#todo)
- [Deploy](#deploy)

# Build<a name="build"></a>
The website is built using Jekyll with `jekyll [build|serve]`
This will take the HTML files, SCSS files, Markdown posts and YML data files to generate a static website. 

The resulting output will be stored under the `_site` subfolder, which is excluded from the repository by the Jekyll template `.gitignore` file.

## Gemfile<a name="gemfile">
Apparently there is a `github-pages` gem which wraps the `jekyll` gem with a couple of extra features, like checking the GitHub Pages DNS challenge from the CLI. I've ran into multiple issues using it (building, deprecated Sass compiler), so I've decided to not use it.

The only way to get GitHub Actions to build the repo when using the (now unused) `github-pages` gem, is by removing the `Gemfile.lock` file from the repo and adding it to `.gitignore`. This file is created when running `bundle` from the CLI to install the gems.

I managed to get GitHub Actions to build using the `jekyll` gem while leaving the `Gemfile.lock` file in the repo by deleting the file and re-creating it using the following commands.

1. `bundle` 
2. `bundle lock --add-platform x86_64-linus`
3. `bundle lock --normalize-platforms`

## SCSS<a name="scss"></a>
Using `@import "partial"` has been deprecated and partials should instead be imported using `@use` where they are assigned a namespace to prevent conflicting variable names. The global namespace `*` can also be used, but is not advised. 

```scss
@use "colors" as colors;

#myElement { font: colors.$main; }
```

As stated above, only the `jekyll` gem contains the modern DartSass compiler that supports this.

## TODO<a name="todo-build"></a>
- Get the repo building on my Mac.

# Deploy<a name="deploy"></a>
GitHub Actions is uesd to build the repo and deploy the generated static site to GitHub Pages, which is linked to the `www.dvt.life` domain.