---
title: "Configuration"
tags:
- setup
---

## Configuration
Quartz is designed to be extremely configurable. You can find the bulk of the configuration scattered throughout the repository depending on how in-depth you'd like to get.

The majority of configuration can be be found under `data/config.yaml`. An annotated example configuration is shown below.

```yaml
name: Your name here! # Shows in the footer
enableToc: true # Whether to show a Table of Contents
enableLinkPreview: true # whether to render card previews for links
description: Page description to show to search engines
page_title: Quartz Example Page # Default Page Title

links: # Links to show in footer
  - link_name: Twitter
    link: https://twitter.com/_jzhao
  - link_name: Github
    link: https://github.com/jackyzha0
```

### HTML Favicons

A Favicon is most commonly seen as the **image preceding the URL in a browser**. 
Some other examples include (but are not limited to) bookmarks, search history, 
and app icons (i.e. "save page to home screen" on mobile devices).
[File format support](https://en.wikipedia.org/wiki/Favicon#File_format_support)
and the [use of favicons](https://en.wikipedia.org/wiki/Favicon#Use_of_favicon) 
differ across the combination of platforms and browsers.

If you would like to customize the favicons of your quartz-based website, you 
can add them to the `data/config.yaml` file. The **default** without any set 
`favicon` key is:

```html
<link rel="shortcut icon" href="icon.png" type="image/png">
```

The default can be overridden by defining a value to the `favicon` key in your 
`data/config.yaml` file. Here is a `List[Dictionary]` example format, which is
equivalent to the default:

```yaml
favicon:
  - { rel: "shortcut icon", href: "icon.png", type: "image/png" }
#  - { ... } # Repeat for each additional favicon you want to add
```

In this format, the following keys are available:
- `rel`: The `rel` attribute of the `<link>` tag.
- `type`: The `type` attribute of the `<link>` tag.
- `href` (optional): The `href` attribute of the `<link>` tag.
- `sizes` (optional): The `sizes` attribute of the `<link>` tag.

If you plan to add multiple favicons generated by a website (see list below), it
may be easier to define it as HTML. Here is an example which appends the 
**Apple touch icon** to quartz's default favicon:

```yaml
favicon: |
  <link rel="shortcut icon" href="icon.png" type="image/png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```

This second favicon will now be used as a web page icon when someone adds your 
webpage to the home screen of their Apple device. If you are interested in more 
information about the current, and past, standards of favicons, you can read 
[this article](https://www.emergeinteractive.com/insights/detail/the-essentials-of-favicons/).

Some websites that **generate favicons** for you (ordered alphabetically) include:
- [`favicon.io`](https://favicon.io/)
- [`realfavicongenerator.net`](https://realfavicongenerator.net/)
- [`www.favicon.cc`](https://www.favicon.cc/)

These sites will take a base image and generate a set of favicons for you, 
one of which will be, for example, the `apple-touch-icon` favicon. These sites
will often **also provide the HTML** for the favicon, which can be simply 
added to the `data/config.yaml` using the HTML format of the `favicon` 
argument. 

**Note** that all generated favicon paths, defined by the `href` 
attribute, are relative to the `static/` directory.

### Graph View
To customize the Interactive Graph view, you can poke around `data/graphConfig.yaml`.

```yaml
enableLegend: false # automatically generate a legend
enableDrag: true # allow dragging nodes in the graph
enableZoom: true # allow zooming and panning the graph
depth: -1 # how many neighbours of the current node to show (-1 is all nodes)
paths: # colour specific nodes path off of their path
  - /moc: "#4388cc"
```


## Styling
Want to go even more in-depth? You can add custom CSS styling and change existing colours through editing `assets/styles/custom.scss`. If you'd like to target specific parts of the site, you can add ids and classes to the HTML partials in `/layouts/partials`. 

### Partials
Partials are what dictate what actually gets rendered to the page. Want to change how pages are styled and structured? You can edit the appropriate layout in `/layouts`.

For example, the structure of the home page can be edited through `/layouts/index.html`. To customize the footer, you can edit `/layouts/partials/footer.html`

More info about partials on [Hugo's website.](https://gohugo.io/templates/partials/)

Still having problems? Checkout our [FAQ and Troubleshooting guide](troubleshooting.md).

## Multilingual
[CJK + Latex Support (??????)](CJK%20+%20Latex%20Support%20(??????).md) comes out of the box with Quartz.

Want to support languages that read from right-to-left (like Arabic)? Hugo (and by proxy, Quartz) supports this natively.

Follow the steps [Hugo provides here](https://gohugo.io/content-management/multilingual/#configure-languages) and modify your `config.toml`

For example:

```toml
defaultContentLanguage = 'ar'
[languages]
  [languages.ar]
    languagedirection = 'rtl'
    title = '????????????'
    weight = 1
```
