
# Okta Developer Site

Okta developer site (developer.okta.com) is a custom Jekyll site deployed on [GitHub pages](https://pages.github.com/)

All API documentation submissions are welcome. To submit a change, fork this repo, commit your changes, and send us a [pull request](http://help.github.com/send-pull-requests/)


## Setup

http://jekyllrb.com/

1. Clone repository
2. `~ $ gem install github-pages` or `bundle install`'` if you use bundler
3. `~ $ cd okta.github.io`
4. `~ $ jekyll serve -w -t`
5. Change CNAME with the right subdomain
6. Visit `http://localhost:4000` in your browser

## Authoring Guide

### Pages

Pages are single purpose html or markdown files

1. Create a folder with `index.html` file. (e.g. *pricing/index.html*)
2. Author front matter as follows:

 ```
---
layout: page
title: YOUR_TITLE
css: CSS_FILENAME.css (optional page specific css file)
---
```
3. Put html or css content under front matter
4. Expose link to page in header or elsewhere. URL will be the folder
   name, `index.html` is not necessary (e.g. */pricing*)

### Docs

1.  Create `PAGE_NAME.md` in `docs/FOLDER_NAME` (e.g. *docs/api/rest/users.md*)
2.  Filenames are underscore seperated and all lowercase. (e.g. *my_cool_doc_page.md*)
3.  Author front matter

 ```
---
layout: docs_page
title: Title Case Name of Page
---
```
4.  The content under the front matter should not have any `h1`s -
    this will be set by the `title` property
5.  All `h2`s in the content will be rendered as a link in the table
    of contents
6.  Create placement entry in manifest at `_data/docs.yml` in
    appropriate `pages` section.
7.  The `pages` name must match the filename without extension. (e.g. `users.md` => `users`)
8.  To create a new section in the manifest

 ```
section: NAME_OF_FOLDER
title: TITLE_CASE_NAME_OF_SECTION
```
9.  The sections structure should follow the folder names
10. The ordering of sections and pages in the manifest determines the order in
    which they appear in the leftnav

### Customers

1.  Create an `index.md` folder in `customers/CUSTOMER_NAME` (e.g. *customers/box/index.md*)
2.  Create the images:

```
`index_image`:     220px x 165px @144dpi  // image used on index page
`header_image`:   1080px x 220px @144dpi  // title bar image on story page
`diagram_image`:   694px x <n>px @144dpi  // information graphic at bottom of story page
```
3.  Author front matter

 ```
`index_blurb` will be clipped over three lines of text
`sidebar_copy` will be markdownified. Newlines sohuld be doubled.
```

### Authors

1.  Create an entry in _source/_data/authors.yml
2.  Put avatar image in _source/assets/img. Make sure aspect ratio of image is square.

### Posts

1. Clone repository
    * root folder './' are the files served by github.
    * '_source' folder contains the source files.
    * '_site' is still ignored
2. Make changes under '_source'
3. Compile the site locally.
4. Preview using locahost:4000
5. rsync files from '_site' to root folder './'
    ```rsync -r _site/ ./```
6. Commit/push to github. Github won't compile the site

**Specific Questions**
Q: Why do we need 2 branches 
A: We don't. Everything is now under one branch, "master".

Q: Why can’t we just checkin _site on master branch with the compiled site.  
A:  Github will not serve a specific folder, in this case the compiled version under '_site'.
