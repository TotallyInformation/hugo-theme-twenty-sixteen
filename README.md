# hugo-theme-twenty-sixteen
A blog and information management theme for Hugo roughly based on the Wordpress Twenty Sixteen theme.

**WARNING**: This template is NOT YET READY.

## Features

* Simple, clean layout based loosely on the WordPress 2016 default theme
* Mix of posts and pages as needed
* Front page, categories and tags listing pages include ALL pages and posts
* Drop-down Site menus with configurable separators
* Safe list of "follow me" social icons (no cookies, GDPR safe)
* Automatically incorporates `description` frontmatter field in page output
* Pages show frontmatter metadata including `date`, `Lastmod`, `title`, `description`, `categories`, `tags`
* Automatic generation of sitemap and RSS feeds
* RSS feeds show full article not summary (be kind to your readers)
* Bulma CSS framework, provides basic responsiveness for mobile
* Fontawsome
* SEO, Google Search, Facebook, Twitter metadata optimisations included (NOT YET COMPLETE)
* Disqus commenting & Google Analytics available

## Usage

To use this for yourself, install as a git submodule as per the instructions on the Hugo website.
See below for more specific instructions.

If you want to make modifications, clone the GitHub project first. You can choose whether to keep 
your copy updated with any upstream changes.

## File Layout

```
content
|
+---pages     | Anything you want to be a site information page goes in here. No index page.
+---posts     | Blog posts go here. No index page
+---kb        | Knowledgebase information pages go here
    |
    +---_index.kb
    ++--A folder for each kb subject area
        |
        +--index.md    | for each folder. 

static
|
+---images    | Site images such as the page header
+---uploads   | This is where blog related files go such as images and other downloadable content
+---css       | Style overrides. a `2016.css` file is located in the template static folder
+---js        | Javascript overrides. a `2016.js` file is located in the template static folder

config.toml   | The main Hugo configuration file

layouts       | Hugo structural definitions. You don't normally need much, if anything in here.
archetypes    | Hugo templates for the `hugo new xxxx` command. Only useful from the command line.
```

## Site Configuration Variables

The following parameters and variables are set in the site `config.toml` file.

```toml
baseURL = "https://it.knightnet.org.uk"
languageCode = "en-gb"
title = "Much Ado About IT"
theme = "twenty-sixteen"

enableRobotsTXT = true
sectionPagesMenu = "main"
paginate = 5 # Number of posts to show before paginating

[permalinks]
  # Configures post URLs
  posts = "/:year/:month/:slug"
  post = "/:year/:month/:slug"
  page = "/:slug"
  pages = "/:slug"
  #kb = "/kb/:slug"
  kbs = "/kb/:slug"
  #category = "/topics/:slug"
  categories = "/topics/:slug"

[author]
  # Site author(s)
  name = "Site Author"
  homepage = ""

# Code Highlighting (uses Chroma but shares old config names for compatibility)
pygmentsCodefences = true
pygmentsUseClasses = true
PygmentsStyle = "monokai"

# Disqus shortcode
# Disable comments for any individual post by adding "comments: false" in its frontmatter
#disqusShortname = ""

[[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
[[menu.main]]
    name = "Topics"
    url = "/categories/"
    identifier = "topics"
    weight = 1
[[menu.main]]
    name = "Tags"
    url = "/tags/"
    parent = "topics"
    identifier = "topics-tags"

[params]
    # Site description
    description = "Ramblings and rantings from IT Consultant, Julian Knight"

    # If false, all of blog post will appear on front page (and in pagination)
    truncate = true

    # Default page editor's name (appears in meta tags and under posts)
    author = "Page Editor"

    # Google analytics code - remove if you do not have/want Google Analytics - needs JavaScript
    #googleAnalytics = ""

    # --- TwentySixteen Theme Parameters --- #
    # What elements to exclude from the navigation menu?
    menuExclude = ["Posts", "Pages"]

    # Sidebar: /layouts/partials/site-sidebar.html
    sidebarSide = "right" # left/right or comment out to disable sidebar
    #sidebarWidth = 3      # Width as # of logical columns (n/12 ths), default = 3

    # Do we want social sharing icons showing?
    sharingicons = true

    # Twitter User - if set will show Twitter timeline in sidebar
    twitterUser = "TwitterHandle"
    # Number of recent posts to show (defaults to 5, max 20)
    twitterPosts = 5
    # Width & height in pixels (defaults to the width of the sidebar, expands to height of tweet list)
    # twitterWidth = 220
    # twitterHeight = 600
    # Twitter widget theme (See https://dev.twitter.com/web/embedded-timelines )
    # twitterTheme = "light" # dark/light/transparent, default dark
    # twitterChrome = "" # default "nofooter noborders"
```

## Page Parameters

The following custom page parameters are used.

* `extraStyle` (URL list): Will load the url as a style sheet in the HTML `head`. Useful for special pages such as one containing a Bulma timeline.
* `extraScript` (URL list): Will load the url as a style sheet in the HTML `head`.

  Example:
  ```yaml
  ---
  extraStyle: 
  - https://unpkg.com/bulma-timeline@2.0.1/dist/bulma-timeline.min.css
  ---
  ```

## Git Submodule handling


## License

This repo is licensed under the Apache 2.0 license. Please see the LICENSE file for details.