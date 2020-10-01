# ACN syllabus

This is a Hugo based web site.

This repo aims to contain all the info needed to run the African Coding Network's official courses. This is very much a work in progress, and if you feel that you can improve this syllabus in any way, please feel free to make a pull request.

## To clone this repo

There is a submodule in here so clone recursively:

```
git clone --recursive git@github.com:Umuzi-org/ACN-syllabus.git
```

## running locally

This is a Hugo based application.

**PLEASE NOTE** We are using hugo version 0.51. We have run into some annoying problems when upgrading hugo in the past so please just use this version.
If you are tempted to give us a PR that upgrades this to the latest version of hugo, it will be a waste of time. The plan is to upgrade this all to use Eleventy in the near future.

### To get yourself set up on a Debian based machine (linux ubuntu/mint)

```
sudo apt install golang
./install_hugo.sh
```

### MAC

Add this in your bash file e.g .zshrc

```
# Go development
export GOPATH="${HOME}/.go"
export GOROOT="$(brew --prefix golang)/libexec"
export PATH="$PATH:${GOPATH}/bin:${GOROOT}/bin"
```

Run these installs in your terminal using Homebrew

```
brew install go
brew install hugo -> look for version 0.51
```

### To run the development server, once it is installed

```
hugo serve -b "http://localhost:1313/"
```

## syllabus docs

look inside /content. The documentation is composed of a bunch of markdown files with a lil metadata.

## Contributing

Please make sure that your contributions actually works and look good. If you edit some stuff then run the hugo server locally. Look at your changes in the browser.

You can contribute in a few different ways:

### You can add or edit course materials

All our course materials live inside the `content` directory.

Please DO NOT put large binary files into this repo. For example PDFs and Presentations and word documents aren't cool.

#### Adding new materials

Let's say you want to add a self-study introduction to Python Flask. You would do something like this:

1. make a directory. This path would make sense: `content/topics/intro-to-flask`
2. make a markdown file inside your new directory called `_index.md`
3. start your markdown file with the following:

```
---
topic: Introduction to Flask
ready: true
---
```

The `ready:true` part tells hugo that this is not a draft, it is ready for human consumption.

If you add anything inside the `content/projects` directory then it will automatically get rendered with a link to a submission form at the top of the page. If you want to suppress this behavior then use the frontmatter:

```
submission_type: nosubmit
```

Take a look at http://localhost:1313/projects/nodejs/ to see this in action

### you can upgrade the look and feel of this site

For the most part the best place to do this is in the layouts directory.

DO NOT EVER make changes directly in the public directory. If you do this your changes will be destroyed. Everything in public gets generated auto-magically so your stuff will just get over-written.

### Lint

To set up your environment:

```
mkvirtualenv -p $(which python3.7) umuzi-tech-dept
pip install -r requirements.txt
```

Run `python lint.py` to make sure all your markdown frontmatter is ok.