# Data Dispatches

[Data Dispatches](https://jhu-data-services.github.io/data-dispatches/)

## Installation

This blog is built in [Quarto](https://quarto.org/). Quarto is a
language-agnostic scientific and technical publishing system built on
Pandoc.

To install `Quarto`, visit [Quarto Get
Started](https://quarto.org/docs/get-started/) and select the Quarto
command line interface (CLI) appropriate to your operating system.

Ensure that you have the appropriate languages installed for the
documents you would like to render. For example, if you are rendering
both `*.Rmd` and `*.ipynb` files, make sure you have `R` and `Python`
installed.

## Usage

Begin by cloning the Data Dispatches repository to a directory of your preference:

`git clone git@github.com:jhu-data-services/data-dispatches.git`

To compile the project:

`cd data-dispatches`

`quarto render`

The rendered website will be added to `/docs`. 

## Configuration

Configuration of the Data Dispatches website is accomplished by setting parameters within the `_quarto.yml` project file.

To understand the structure of the `_quarto.yml` details are provided for each of the `_quarto.yml` sections.

### Project

Do not change project settings. The type, `website`, renders the
multiple notebooks as a unified page, and the specified output
directory `docs` allows Github Pages to render the website content generated by Quarto.

``` yaml
project:
  type: website
  output-dir: docs
```

### Website

``` yaml
website:
  title: "Data Dispatches - JHU Data Services"
  reader-mode: false
  page-navigation: true
  search:
    location: sidebar
```

#### Navbar

The navbar controls the navigation bar at the top of the page. The position of the bar can be `left`, `middle`, or `right`. The icons use the [Font Awesome](https://fontawesome.com/) library of icons, so any FA icons should work.

``` yaml
  navbar: 
    logo: logos/data-dispatches-white.png
    background: primary
    right: 
    - icon: github
      href: https://github.com/jhu-data-services
    - icon: globe 
      href: https://dataservices.library.jhu.edu/
    - text: "Help"
      menu:
        - text: "Report an Issue"
          icon: "bug"
          href: "https://github.com/jhu-data-services/data-dispatches/issues"
        - text: "Get Help"
          icon: "chat-right-text"
          href: "https://v2.libanswers.com/chati.php?hash=8b19eda5bc7bc7b80e623cad56abdd12"
```

#### Sidebar

The sidebar section is important, this is where you will add new content that you are adding to Data Dispatches.

``` yaml
  sidebar: 
    - id: dispatches
      title: "Data Tutorials"
      style: "floating"
      search: true
      collapse-level: 2
      contents:
        - index.qmd
        - section: "Data Visualization"
          contents:
            - dispatches/data-visualization/custom-ggplot2-theme.qmd

```

If you are adding content (`.Rmd`, `.ipynb`, `.qmd`) for a new topic (ex. Data Cleaning) you will need to:

  * Create an appropriately named folder in the `dispatches` directory, for example: `mkdir ./dispatches/data-cleaning`
  * Add a section to the contents of the sidebar section. For example,
    to add an `example-data-cleaning-lesson.qmd` to the sidebar
    contents above:

``` yaml
      contents:
        - index.qmd
        - section: "Data Visualization"
          contents:
            - dispatches/data-visualization/custom-ggplot2-theme.qmd
        - section: "Data Cleaning"
          contents:
            - dispatches/data-cleaning/example-data-cleaning-lesson.qmd
```

#### Page Footer

Add information to the page footer. Positioning of footer information can be `left`, `center`, or `right`

``` yaml
  page-footer: 
    background: primary
    left: "Copyright 2022, JHU Data Services." 
    right: "This site was built with [Quarto](https://quarto.org/)."
```

### Format

The theme can be set in the `format` section, and any custom css can be added to `styles.css`.

``` yaml
format:
  html:
    theme: litera 
    css: styles.css
    toc: true
```

### Editor

This is an RStudio specific setting that sets the default view for Quarto documents in RStudio. `editor: visual` will show the rendered `.qmd` pages by default.

``` yaml
editor: visual
```

## Contributing

Submit a pull-request to add new content to the Data Dispatches site.
