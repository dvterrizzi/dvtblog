# www.dvt.life
My place on the web

## Build
The website is built using Jekyll with `jekyll [build|serve]`
This will take the HTML files, SCSS files, Markdown posts and YML data files to generate a static website. The resulting output will be stored under the `_site` subfolder, which is excluded from the repository by the Jekyll template `.gitignore` file.

## Deploy
GitHub Actions is uesd to build the repo and deploy the generated static site to GitHub Pages, which is linked to the `www.dvt.life` domain.