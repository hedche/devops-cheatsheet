Taken from the Hextra Starter Template

[![Deploy Hugo site to Pages](https://github.com/hedche/devops-cheatsheet/actions/workflows/pages.yaml/badge.svg)](https://github.com/imfing/hextra-starter-template/actions/workflows/pages.yaml)

## Local Development

Pre-requisites: [Hugo](https://gohugo.io/getting-started/installing/), [Go](https://golang.org/doc/install) and [Git](https://git-scm.com)

```shell
# Clone the repo
git clone https://github.com/imfing/hextra-starter-template.git

# Change directory
cd hextra-starter-template

# Start the server
hugo mod tidy
hugo server --logLevel debug --disableFastRender -p 1313
```
