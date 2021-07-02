# Using the site

---
* Install hugo in your system. [Click here for steps](#installing-in-windows)
* Clone the repository
* Run `cd movie_cards`
* Start the hugo server. [Click here for steps](#start-the-hugo-server)





# Getting started with Hugo Framework

---
Checkout https://gohugo.io/getting-started/quick-start/ for getting started.
- [Installing in windows](#installing-in-windows)
- [Installing in other OS](#installing-in-other-os)
- [Creating a new site](#creating-a-new-site)
- [Adding  a theme](#adding-a-theme)
- [Adding some content](#adding-some-content)
- [Start the Hugo server](#start-the-hugo-server)
- [Getting example site from the theme](#getting-example-site-from-the-theme)  
- [Creating a new theme](#creating-a-new-theme)
- [Variables](#variables)
- [Front Matter](#front-matter)
- [Archetypes](#archetypes)
- [Shortcodes](#shortcodes)
- [Creating custom shortcodes](#creating-custom-shortcodes)
- [Data files](#data-files)
## Installing in windows
* Goto https://github.com/gohugoio/hugo/releases.
* Find the release for windows in the bottom of the page and download the zip file.
* Create a new directory `Hugo/bin` and extract the files in zip folder in to the new directory.
* Add to `PATH` the new path created for `bin`.
* Run `hugo version` in command prompt to see whether hugo is installed.

## Installing in other OS
* Check https://gohugo.io/getting-started/installing/
## Creating a new site
* Run `hugo new site site-name` in the command prompt and a new folder named site-name will be created.

## Adding a theme
* First, download the theme from GitHub and add it to your site’s themes directory:
* Sample code\
`cd site-name`\
`git init`\
`git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke`
* Then, add the theme to the site configuration: In `config.toml` add `theme = "ananke"`.

## Adding some content
* Run `hugo new posts/my-first-post.md`.
* This will create `content/posts/my-first-post.md`.
* Change `draft: true` to `draft: false`.
## Start the Hugo server
* Run `hugo server -D`.
* Navigate to your new site at http://localhost:1313/

## Getting example site from the theme
* Copy the content of `themes/ananke/exampleSite` to `site-name`.
* Ensure that `theme` in `config.toml` matches the file name in `themes` directory.
* Start the hugo server and navigate to site.
* Customize files in `content/` to edit the example site.

## Creating a new theme
Refer https://retrolog.io/blog/creating-a-hugo-theme-from-scratch/ \
OR
https://levelup.gitconnected.com/a-quick-tutorial-on-hugo-templates-creating-your-theme-a4102b42a85f
OR
https://www.zeolearn.com/magazine/develop-a-theme-for-hugo
## Variables
* Variables can only be used inside templates and layouts, not inside content.
* The basic syntax of go html template looks like this `{{ args }}`
* Example of variable:\
  `{{ .Title }}` is used for accessing the title for this page.
* Variables $ : Hugo also lets you create your own custom variables. Here you can store values to use in your layouts. To create a custom variable use the following notation:\
`{{ $myVar := value }}` : assigns value to $myVar\
`{{ $myVar }}` : prints $myVar
## Front Matter
* Example:
  
      ---
      title: "My First Post"
      date: 2021-06-22T15:15:38+05:30
      tags: ["foo", "bar"]
      ---
* This is found in the starting of each md file.
* It is just key:value pairs containing the details about that file.
* Custom variables can be added here. Eg: `tags` is a variable.
* Default language for front matter is YAML.

## Archetypes
* Control the default front matter created on creating md files.

## Shortcodes
* Shortcodes are simple snippets inside your content files calling built-in or custom templates.
* Shortcodes are used to avoid writing raw html code in md files.
* Syntax of shortcodes in md files: `{{< shortcode-name param1 >}}` .
  Here `param1` is a parameter passed to the shortcode. 
  These are single tag shortcodes.
* We can also use two tags for calling shortcodes. 
  
      {{< shortcode-name >}} 
      Some text
      {{< /shortcode-name>}}
* To send markdown text using two tags, use:
  
      {{% shortcode-name %}}
      Stuff to `process` in the *center*.
      {{% /shortcode-name %}}
* A default shortcode available is for adding youtube videos to our site.
  This can be done by `{{< youtube paramter >}}` where the parameter is a youtube video id,
  for eg: `2xkNJL4gJ9E`
* Visit https://gohugo.io/content-management/shortcodes/ for more details.  
## Creating custom shortcodes
* Create a new folder `shortcodes` in `layouts` folder.
* Create an html file inside `shortcodes`. The name of file will be used
  for calling the shortcode.
* Create the needed template in the html file just created.
* Call the shortcode in content file using `{{< shortcode-name >}}`
* Variables can be passed to shortcode. 
  They can be accessed using `{{.Get "var-name" }}` in the shortcode html file.
* Parameters can also be accessed according to their position.
  `{{ .Get 0 }}` can be used to access the first parameter passed.
* To access the text written inside the shortcode tags, we can use `{{.Inner}}`.

## Data files
* Relevant read: https://discourse.gohugo.io/t/solved-how-to-pass-name-of-data-file-or-table-to-a-shortcode/4961
* Hugo supports loading data from YAML, JSON, and TOML files located in the data directory in the root of your Hugo project.
* The data will be accessible as a `map` in the `.Site.Data` variable.
* For eg: `data/jazz/bass/jacopastorius.toml` can be accessed using `.Site.Data.jazz.bass.jacopastorius`

## Content Organization
* Read https://gohugo.io/content-management/organization/
## Notes
* All the templates are placed inside the layout.
* 2 types of content - List and Single
* List - lists all the pages(md files)
* Single - shows single page
* Hugo creates list pages only for those directories in the root folder of content
* To get a list page for particular directories, create a file `_index.md` in that directory



