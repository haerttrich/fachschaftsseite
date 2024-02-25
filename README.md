# Website Fachschaft
Currently a new website for the [Fachschaft Computerlinguistik at LMU](https://fachschaft.cis.lmu.de/index.html) is being constructed. This repository contains the current status of the reconstruction process.
The current version can be seen under [https://fachschaft.haerttrich.dev](https://fachschaft.haerttrich.dev).

## Run Locally
1. Download this Repository with `git clone https://github.com/haerttrich/fachschaftsseite`
2. [Install HUGO](https://gohugo.io/installation/)
3. Start the server locally with `hugo server --buildDrafts --disableFastRender -F`
4. Visit `loaclhost:1313`

## Add changes
1. Create a new faeature branch
2. Commit all your changes on the branch
3. Test functionality locally
4. Solve possible conflicts to main on your branch
5. Create a Pull Request for the main branch
6. Once your PR is accepted the changes are online

### New Content
There are four kinds of content you can add to the website, by creating a markdown file. This creation can be done by manually adding the resepectively required yaml frontmatter to the new file (look at `/archetypes` to see the existing templates). Alternatively it is recommended to just create a new file using the existing templates.
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

## References
[HUGO docs](https://gohugo.io/documentation/), [Go-lang docs](https://go.dev/doc/), [Hextra Theme](https://imfing.github.io/hextra/).
