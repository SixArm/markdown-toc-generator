# Markdown TOC generator

Update a markdown file by autogenerating a table of contents
based on the markdown headlines; currently we just do H2.

Syntax:

    markdown-toc-generator <file>

Example:

    markdown-toc-generator example.md


## How it works

The command parses the Markdown file using GitHub's HTML pipeline.

Example Markdown headline:

    ## Hello World

The pipeline generates a headline anchor href string:

    hello-world

The command creates a markdown list item:

    * [Hello World](#hello-world)

The command searches the text for the abbreviation "TOC:"
that starts a line, and is on the line by itself.

    TOC:

The command replaces successive non-blank lines with the markdown list items:

    TOC:
    * [Hello World](#hello-world)


## Demo

Demonstration Markdown file text, before the generator:

    # Demo

    TOC:
      
    ## Alpha

    Lorem ipsum...

    ## Bravo
    
    Lorem ipsum...

    ## Charlie

    Lorem ipsum...

Example Markdown file text, after the generator:

    # Demo

    TOC:
    * [Alpha](#alpha)
    * [Bravo](#bravo)
    * [Charlie](#charlie)
      
    ## Alpha

    Lorem ipsum...

    ## Bravo
    
    Lorem ipsum...

    ## Charlie

    Lorem ipsum...

Example of how GitHub renders the file, approximately:

    <h1>Demo</h1>

    TOC:
    <ul>
    <li><a href="#alpha">Alpha</a></li>
    <li><a href="#bravo">Bravo</a></li>
    <li><a href="#charlie">Charlie</a></li>
    </ul>
 
    <h2><a class="anchor" href="#alpha" id="user-content-alpha">Alpha</a></h2>

    Lorem ipsum...

    <h2><a class="anchor" href="#bravo" id="user-content-bravo">Bravo</a></h2>
    
    Lorem ipsum...

    <h2><a class="anchor" href="#charlie" id="user-content-bravo">Charlie</a></h2>

    Lorem ipsum...


The GitHub automatic rendering typically adds more information, 
such as an SVG anchor image that shows/hides during hover.


## Tracking

* Command: markdown-toc-generator
* Version: 1.5.0
* Created: 2018-02-04
* Updated: 2018-02-06
* License: GPL
* Contact: Joel Parker Henderson (joel@joelparkerhenderson.com)

