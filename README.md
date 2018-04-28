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
* Schema.org extensions for blog (built in), person (put ld+json in `/data/siteauthorld.json` file) and organisation (put ld+json in `/data/siteauthorld.json` file).

## Usage

To use this for yourself, install as a git submodule as per the instructions on the Hugo website.
See below for more specific instructions.

If you want to make modifications, clone the GitHub project first. You can choose whether to keep 
your copy updated with any upstream changes.

## Content Structure

I use a content structure that is quite opinionated. I can't guarantee that you will like it but please do give it a go
to see if you can live with it.

Like many site structures, I assume that you have 2 basic types of actual content: `posts` and `pages`. 

### Content sections

This theme assumes the use of 6 content sections. You will need to create the matching folders under
the `/content` folder. Each will have an `_index.md` file.

1. **posts** - These are your standard blog posts. Use as expected. I use a permalink structure that 
   puts posts under a URL of `/blog/:slug`.
2. **categories** - You probably wont have anything other than an `_index.md` file in this folder.
   The actual list of categories is generated automatically by Hugo. However, by including the folder
   and an index file, you can provide both a menu (though you could do this via `config.toml` if preferred)
   and some explanatory header text along with an SEO description.
3. **tags** - as for categories.
4. **about** - A (generally small) collection of pages such as ones about the site, about the site owner/author,
   about the design. More importantly, you are likely to want to keep privacy, copyright and other legal statements here.
   Keep anything you would like to see under an `about` menu here. Don't forget to add menu frontmatter options.
5. **kb** - Knowledgebase - This section is for pages that are less volatile and less likely to age than your standard blog posts.
   There is no hard and fast rule as to whether to use posts or the knowledgebase. You may wish to create sub-sections
   in `kb` as I do, each covering different specialist areas.
6. **projects** - This is a portfolio section. Use this for keeping track of projects you've worked on. It is entirely optional.

Really, all of these sections are arbitrary and optional. However, you may occasionally find things in the theme that don't quite
work as expected if you don't at least have `posts`, `about` and `kb`.

You may have more sections as you wish. Simply add a new folder under the `/content` folder and include a `_index.md` file containing the appropriate menu
entry and any fixed content you want appearing before the list of pages. The list of pages in the section is generated automatically.

If you have any fixed content above the list, I recommend that you add a level 3 heading at the end of the index file (so it appears as the
heading for the list of pages).

### Other data types

While `posts` and `pages` are the 2 default page (content) types, you can, of course, add others and also use the `/data` folder
to create data-driven content. These are standard Hugo features and there is no special support built into this theme.

## File Layout

You should use the following file layout when using this theme

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
+---data
    |
    +---siteauthorld.json | ld+json format person data (schema.org), optional
    +---siteorgld.json    | ld+json format organisation data (schema.org), optional

static
|
+---images    | Site images such as the page header
+---uploads   | This is where blog related files go such as images and other downloadable content
+---css       | Style overrides. a `2016.css` file is located in the template static folder
+---js        | Javascript overrides. a `2016.js` file is located in the template static folder
+---favicon.ico

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