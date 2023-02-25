---
layout: post
title: Setting up a Blog with GitHub Pages
---
# Introduction

GitHub Pages is a free service from GitHub that lets you start a blog quickly and easily. It's primarily **targeted at developers** since they are already familiar with using GitHub, version control systems and writing documents using the markdown syntax. Other people can try but there are simpler systems out there targeted at non developers such as WordPress.

GitHub Pages uses Jekyll in the background to process your blog entries into something more presentable and SEO friendly. Each time you modify your GitHub Pages Jekyll will notice the changes and run in the background to transform them into presentable html and css (and perhaps some javscript). This process may take a minute or two to complete but can be tracked under the **"Actions" tab for your repo on the GitHub website**.

# Installation

Create a GitHub account if you don't already have one.

Create a repository named `<your github username>.github.io`

Create a file `index.md`:

```yml
---
layout: home
---
```

Create a file `_config.yml`:

```yml
title: Jonathan's Tech Blog
first_name: Jonathan
last_name: Pugh
email: jdspugh@gmail.com
description: Tech Blog
baseurl: "/"
url: "https://jdspugh.github.io"
twitter_username: jdspugh
github_username:  jdspugh
theme: minima
```

That's it! Simple! Now we will add some content:

# Creating Posts

Create a folder `_posts`. Inside this folder you will create your blog posts. Name them with the date followed by a name e.g.:

```
2023-02-23-jp-watch-c.md
2023-02-25-github-pages-jekyll-setup.md
```

The content of each blog post will be of the form:

```yml
---
layout: post
title: <blog entry's title>
---
<blog entry's content in markdown format>
```

GitHug Pages uses markdown syntax for blog entries. For me I mainly use these features:

Titles:
```md
# Title 1
## Title 2
```

Code blocks:
~~~html
```html
<p>This is html code</p>
```
~~~

~~~js
```js
console.log('Hi!')
```
~~~

GitHub Pages uses the "GitHub Flavored Markdown Spec" that you can browse if you want details on everything that can be done in this markdown flavour: <https://github.github.com/gfm/>

# Custom CSS

Create a file `assets/main.scss`. You can place any custom CSS at the bottom of this file e.g.:

```css
---
---
@import "{{site.theme}}";

/* START numbered headings */
article {
  counter-reset: a;
}

article h2:before {
  content: counter(a)" ";
}

article h2 {
  counter-increment: a;
  counter-reset: b;
}

article h3:before {
  content: counter(a)"."counter(b)" ";
}

article h3 {
  counter-increment: b;
}
/* END numbered headings */
```

# User Comments

If you want users to be able to comment and discuss your posts you can easily add this feature by adding [Disqus][1] to your posts if you are using the `minima` theme. Add your [Disqus][1] shortname to the `_config.yml`:

```yml
theme: minima
disqus:
  shortname: tech-blog-jdspugh
```

# Summary

The final directory structure of your repo will look like this:

```
index.md
_config.yml
_posts
  2023-02-23-jp-watch-c.md
  2023-02-25-github-pages-jekyll-setup.md
assets
  main.scss
```

I hope you found this tutorial helpful to get started with blogging using GitHub Pages. Feel free to leave any comments, and happy blogging!

[1]: https://disqus.com