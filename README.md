# Website Fachschaft
This repo contains the code of the [website of "Fachschaft Computerlinguistik" at LMU](https://fachschaft.cis.lmu.de/index.html).
Our [repository of the website](https://gitlab2.cip.ifi.lmu.de/altinger/website-fscl) is located in gitlab.


# Run Locally
_Note: In order to run the server you need to install the `hugo` CLI. Inform yourself on how to install it on your system._

To start the server run the following command (in this folder):
```
hugo server
```
alternatively your can run this command in order for the server to recompile during development:
```
hugo server --buildDrafts --disableFastRender
```
If the website does not open automatically in your browser, visit `localhost:1313` to see the website inside your browser.


## Create new content
There are four kinds of content you can add to the website, by creating a markdown file. This creation can be done by manuallt adding the resepectively required yaml frontmatter to the new file (look at `/archetypes` to see the existing templates). Alternatively it is recommended to just create a new file using the existing templates.

```
hugo new content --kind <content_kind> <file_path>.md
```
Possible `content_kind`s are `docfile`, `event`, `post` and `default`. Due to hugo's internal structure you have to keep in mind, that docs, posts, events, etc have to be placed into their respective folders, allowing for the following possibilities to create new markdown files

```
hugo new content --kind blog content/blog/<file_name>.md
hugo new content --kind docfile content/docs/<file_name>.md
hugo new content --kind event content/events/<file_name>.md
```
After creating your file adjust the frontmatter accordingly and start filling in the content itself.


## Update Website on Server (has to get updated)
1. Log into server `fachschaft.cis.uni-muenchen.de` via ssh to do so replace `<user>` and `<key>` with your respective credentials
2. Naigate to the `www` folder which contains the `html subfolder`
3. pull the current version from the github repo to update here
    - you need to know your user name and password (on the server) to have sudo rights
    - know your user name and password (from gitlab) to fetch / pull from the repo
```
1. ssh <user>@fachschaft.cis.uni-muenchen.de -i <key>
2. cd /var/www/
3. sudo git pull 
```

_Note: You need access to this repo and to the server mentioned. If you have no access to the website, contact Thomas Schaefer from CIS. 
If you have no access to the repo, you need to contact members of the fachschaft who have._
