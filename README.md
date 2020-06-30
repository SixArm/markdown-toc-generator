# Markdown TOC generator

Update a markdown file by autogenerating a table of contents
based on the markdown headlines.

Syntax:

```terminal
markdown-toc-generator <file>
```

Example:

```terminal
markdown-toc-generator example.md
```

Limits:

* This does H2 headlines and lesser; this does not do H1 headlines.
* This needs each headline anchor href to be unique; this does not auto-number them.

## Install

This command uses Ruby.

Verify you have Ruby version 2.2 or better:


```terminal
ruby -v
```

Copy this command to somewhere on your path such as:

```terminal
curl https://raw.githubusercontent.com/SixArm/markdown-toc-generator/master/markdown-toc-generator --output /usr/local/bin/markdown-toc-generator
```

TODO: transition this to a gem, then to Rust.

## How it works

The command parses the Markdown file using GitHub's HTML pipeline.

Example Markdown headline:

```markdown
## Hello World
```

The pipeline generates a headline anchor href string:

```text
hello-world
```

The command creates a markdown list item:

```markdown
* [Hello World](#hello-world)
```

The command searches the text for the abbreviation "TOC:"
that starts a line, and is on the line by itself.

```markdown
TOC:
```

The command replaces successive non-blank lines with the markdown list items:

```markdown
TOC:
* [Hello World](#hello-world)
```

## Demo

Demonstration Markdown file text, before the generator:

```markdown
# Demo

TOC:
      
## Alpha

Lorem ipsum...

## Bravo
    
Lorem ipsum...

## Charlie

Lorem ipsum...
```

Example Markdown file text, after the generator:

```markdown
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
```

Example of how GitHub renders the file, approximately:

```html
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
```

The GitHub automatic rendering typically adds more information, 
such as an SVG anchor image that shows/hides during hover.

## Tracking

* Command: markdown-toc-generator
* Version: 1.6.0
* Created: 2018-02-04
* Updated: 2018-02-06
* License: Open source as described in the file LICENSE.md
* Contact: Joel Parker Henderson (joel@joelparkerhenderson.com)
