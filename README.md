# Planet Lia Bounce Evasion Docs
[![Netlify Status](https://api.netlify.com/api/v1/badges/a2e33de5-8739-4386-b738-06c863449a3c/deploy-status)](https://app.netlify.com/sites/bounce-evasion-docs-planetlia/deploys)

The official Planet Lia Bounce Evasion documentation website.

The website is available on: [https://bounce-evasion.docs.planetlia.com](https://bounce-evasion.docs.planetlia.com).

To view the source code of the Planet Lia CLI or game, head on to our monorepo [planet-lia/planet-lia](https://github.com/planet-lia/planet-lia).

## Development
The website is created using [Hugo](https://gohugo.io) and the 
[Material Docs theme](https://github.com/digitalcraftsman/hugo-material-docs).

Unless you have a good reason, **do not** change the `hugo-material-docs` theme. 
The theme has been forked and many changes have been made. If you need to add/change
something, there exists a pretty good chance it is possible in the project and
not the forked theme. Consult with the project maintainers (open an issue) to
make sure.

### A Note on Static Files
Anything in the folder `static` will be treated as the root path of the final build, eg. 
in source: `static/static/images/logo.png` will become in the build:
`http(s)://<BASE_WEBSITE_ROOT>/static/images/logo.png`.
Hopefully this explains the duplicate static folder.

# License
All files are released under the Apache License version 2.0.
