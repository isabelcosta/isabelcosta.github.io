# My Etch

This is my new website made with [Hugo](https://gohugo.io/). It uses [LukasJoswiak/etch](https://github.com/LukasJoswiak/etch) template. I chose this template because it is focused on the content.

## Setup & Run

Get submodule code:
```
git clone <url>
git submodule update --init
```

or

```
git clone --recurse-submodules <url>
```

Serve
```
hugo server -t etch
```

Open http://localhost:1313/

Original example: https://lukasjoswiak.github.io/etch/

### Setup of GH Pages

Generating and set ssh keys for actions deploy key:
```
~/.ssh > ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f
~/.ssh > pbcopy < ~/.ssh/gh-pages 
~/.ssh > pbcopy < ~/.ssh/gh-pages.pub
```

Links:
- https://gohugo.io/hosting-and-deployment/hosting-on-github/
- https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-create-ssh-deploy-key

### Branches

- `main` has the source code of the website
- `gh-pages` has the files that result from building the website and that will be used by GitHub Pages

### Posts configuration

I added a couple additional options to the posts frontmatter. Here's some:

- `override_url`: if set to a value, this will serve as the link to the post when listed
- `crossposts`: will contain the external links to the posts in blogging platforms. So far the code will only render when given url for `medium` and `devto`.


## Other links

- https://gohugo.io/getting-started/quick-start/
- https://github.com/LukasJoswiak/etch/wiki/Getting-started
- git submodules: https://git-scm.com/book/en/v2/Git-Tools-Submodules