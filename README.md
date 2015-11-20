# [get-scala.org](http://get-scala.org)

This repository holds the content of [get-scala.org](get-scala.org), including all documentation and the language specification.

It's a static site generated by [Jekyll 3](https://github.com/jekyll/jekyll), and uses a whole host of open-source tools including a touch of Twitter's Bootstrap.

## Dependencies ##

<<<<<<< b7d3768c12ac157563b35806b9fcc3f36b8d3606
This site uses a Jekyll, a Ruby framework. The required Jekyll version is 3.1.6.
=======
This site uses a Jekyll, a Ruby framework. You'll need Ruby and Bundler installed; see [Jekyll installation instructions](http://jekyllrb.com/docs/installation/) for the details.
>>>>>>> Content migration, version upgrades

## Building & Viewing ##

`cd` into the directory where you cloned this repository, then install the required gems with `bundle install`. This will automatically put the gems into `./vendor/bundle`.

Start the server in the context of the bundle:

    bundle exec jekyll serve -i

The generated site is available at `http://localhost:4000`

Jekyll will automatically watch for changes on the filesystem, and regenerate the site. It can take a few minutes for your changes to appear. Watch the output from `jekyll serve`. When you start up you'll see this:

     $ bundle exec jekyll serve -i
     Configuration file: /Users/ben/src/scala.github.com/_config.yml
                 Source: /Users/ben/src/scala.github.com
            Destination: /Users/ben/src/scala.github.com/_site
      Incremental build: enabled
           Generating...
                         done in 1.04 seconds.
      Auto-regeneration: enabled for '/Users/ben/src/scala-lang'

When you change a file, this output will tell you that jekyll is regenerating. It's not done until it says `done.`

       Server running... press ctrl-c to stop.
           Regenerating: 1 file(s) at 2014-11-29 09:19:04 ...done in 0.9704294 seconds.
           Regenerating: 3 file(s) at 2014-11-29 09:21:39 ...done in 1.9161814 seconds.
           Regenerating: 2 file(s) at 2014-11-29 09:25:10 ...done in 1.2371298 seconds.
           Regenerating: 2 file(s) at 2014-11-29 09:27:49

### Windows and UTF-8

If you get `incompatible encoding` errors when generating the site under Windows, then ensure that the
console in which you are running jekyll can work with UTF-8 characters. As described in the blog
[Solving UTF problem with Jekyll on Windows](http://joseoncode.com/2011/11/27/solving-utf-problem-with-jekyll-on-windows/)
you have to execute `chcp 65001`. This command is best added to the `jekyll.bat`-script.

## Writing and Formatting

### YAML Front Matter

The "YAML Front Matter" is nothing more than the header on each page that you intend for Jekyll to parse. It contains information such as the name of the HTML template (layout) chosen for the specific document, and the title of the document. An example YAML front matter might look like:

    ---
    layout: page
    title: My page title
    ---

You can use these fields in the YAML front matter later in your document. For example, to make a header with the title of the document, in markdown you would write:

    ---
    layout: page
    title: My page title
    ---

    # {{ page.title }}

    Body text here...

`# {{ page.title }}` would be rendered in HTML as, `<h1>My page title</h1>`.

### Linking to internal pages

The least error-prone way to link between documents, to link to local images, or anything else: `[link text]({{ site.baseurl }}/path/to/page/page.html)`

Here, `{{ site.baseurl }}` is a site-wide variable that represents the root directory of the static site. So, to display the Scala logo image, located in `img/scala-logo.png`, one must simply write: `![Img alt text]({{ site.baseurl }}/resources/img/scala-logo.png)`.

### Resources and Workflow

GitHub Pages rebuilds the site on every commit to the `gh-pages` branch of the `soc/scala-lang` repository.
