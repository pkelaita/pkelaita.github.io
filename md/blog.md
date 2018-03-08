# Grip for Github Flavored-Markdown
***Pierce Kelaita*** <br>
***3-8-2018***

Often times when hosting a project on Github, we want others to be able to understand, use, and contribute to our software with as little difficulty as possible. Github makes this process quite easy by supporting its own flavor of the Markdown language to write comprehensive README files. However, due to the many nuances of Github-flavored markdown, users unknowingly may commit a README that is poorly formatted, or has syntax errors. This is where Grip comes in.

Grip uses the [Github Markdown API](http://developer.github.com/v3/markdown) to allow writers of .md files to view their Markdown files locally, before commiting to remote. Grip's creator cites [README-Driven Development](http://tom.preston-werner.com/2010/08/23/readme-driven-development.html) as the motivation for creating this tool. Indeed, creating a well-formatted README document allows developers to have a better idea of the big-picture of their software, write more effective documentation, and collaborate more efficiently with teams. 

There are many Markdown-HTML conversion tools availible to the public, but what sets Grip apart from the rest is its ease of usability. Instead of clumsy navigating between text editors and external applications, Grip allows users to perform every type of preview or conversion directly from the command line.

To render a file:
```console
$ grip filename.md
 * Running on http://localhost:6419/
```

To specify a hostname or port:
```console
$ grip filename.md 80
 * Running on http://localhost:80/
```

```console
$ grip filename.md 0.0.0.0:80
 * Running on http://0.0.0.0:80/
```

Additionally, running the command `grip` will automatically search the current directory for a `README.md` and render the file, if found. Grip also supports the `-b` flag to automatically open the rendered file in your browser, a feature that I am greatly thankful for.

Howebver, I find Grip's most powerful feature to be its ability to seamlessly export Markdown files to HTML:

```console
$ grip filename.md --export
Exporting to filename.html
```

Control the output name with the second argument:

```console
$ grip filename.md --export index.html
Exporting to index.html
```

Unfortunately, this program does not come without its fair share of [bugs](https://github.com/joeyespo/grip/issues). Most recently, I ran into an issue last week when Github turned off the TLS1.0, requiring openSSL and Python updates in order to allow Grip to run. This was a version of Python not yet supported by the latest version of Homebrew, so I had to manually reinstall Grip, Python, and openSSL before Grip could run. Others have documented similar HTTP connection errors produced by Grip.

Despite its bugs, Grip is probably the single most useful command-line tool I use, and many of my coworkers make regular use of it. I highly reccommend it to anyone developing software for the public.

Install and read more about Grip on [Joeyespo's Github](https://github.com/joeyespo/grip).