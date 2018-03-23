Invoke-Documentation
====================
Started out from [Damien Sorel](https://github.com/mistic100)'s [jekyll-bootstrap-doc](https://github.com/mistic100/jekyll-bootstrap-doc)

The aim is to centralise all (technical) documentation for all projects of Invoke-Automation using this site.

Running the site localy
-----------------------
### Checking out a repo with submodules
for Git 2.13 and later you can clone everything using
```bash
git clone --recurse-submodules https://github.com/Invoke-Automation/Invoke-Documentation.git
```

If you already cloned and forgot or if you are using older versions of Git
```bash
git clone https://github.com/Invoke-Automation/Invoke-Documentation.git
cd Invoke-Automation
git submodule update --init --recursive
```

### Install Jekyll

Use the [Jekyll documentation](https://jekyllrb.com/docs/quickstart/)

TL;DR for Windows:

```Powershell
choco install ruby -y
gem install jekyll
gem install bundler
```

### Run the site

```bash
bundle exec jekyll serve
```

Adding a project
----------------

To Add a project to this site the following steps need to be taken:

 1. Add the project to the `\_data\projects.yml`
  ```YAML
  - name: ProjectName
    description: ProjectDescription
    github: ProjectGitHubURL
    index: ProjectIndex
    path: /projects/ProjectName
  ```
 2. Add the Project repo as submodule to this repo
  ```bash
  git submodule add ProjectGitURL.git projects/ProjectName
  ```
To make the README file visible on the site the README.md file needs to start with the following yml header:
```YAML
---
URL: URLToTheREADMEFile
index: 0
---
```

Updating a project
------------------

To update a projects documentation the documentation first needs to be available in the master branch of that project.
If the master branch of a project is updated these changes should be pulled into this repo:

```bash
git submodule foreach git pull origin master
```