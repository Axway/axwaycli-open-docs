# Axway-CLI-Open-Docs

Axway-CLI-Open-Docs is a docs-as-code implementation for Axway documentation. It is built using [Hugo](https://gohugo.io/) static site generator with the [Google Docsy](https://github.com/google/docsy) theme. The site is deployed on Netlify at <https://axwaycli-open-docs.netlify.app/>

This repository contains all files for building and deploying the site. The Markdown files for the documentation are stored at `/content/en/docs`. The image files for the documentation are stored at `/static/Images`.

## Contribute

We welcome your contributions! To get started, go to <https://axway-open-docs.netlify.app/> and click **Documentation** in the top menu. Browse the documentation and use the options in the right navigation to edit any page using GitHub or Netlify CMS.

Before you start contributing, please read the [contribution guidelines](https://axwaycli-open-docs.netlify.app/docs/contribution_guidelines/).

## Safe Use of HTML in Markdown

Markdown supports inline HTML, however only the following HTML is permitted:

| Description    | HTML                                                    |
| -------------- | ------------------------------------------------------- |
| Line break     | `<br>`                                                  |
| Link w/ target | `<a href="https://axway.com/" target="_blank">Axway</a>` |
