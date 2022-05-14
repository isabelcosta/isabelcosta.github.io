# My Etch

Started this project with:
- https://gohugo.io/getting-started/quick-start/
- https://github.com/LukasJoswiak/etch/wiki/Getting-started
- https://github.com/peaceiris/actions-gh-pages#%EF%B8%8F-create-ssh-deploy-key
- git submodules: https://git-scm.com/book/en/v2/Git-Tools-Submodules
- https://gohugo.io/hosting-and-deployment/hosting-on-github/

## Run

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



## Setup of GH Pages

Generating and set ssh keys for actions deploy key:
```
~/.ssh > ssh-keygen -t rsa -b 4096 -C "$(git config user.email)" -f
~/.ssh > pbcopy < ~/.ssh/gh-pages 
~/.ssh > pbcopy < ~/.ssh/gh-pages.pub
```
