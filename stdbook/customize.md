---
layout: default
title: {{ site.name }}
---

# <a name="how" class="anchor">Style</a>
 
## <a name="jekyll" class="anchor">Jekyll</a>

[Jekyll](https://jekyllrb.com/) is a [Ruby](https://www.ruby-lang.org/) gem that transforms plain text into static websites and blogs. Here, we will briefly cover overriding Jekyll's style files to make your documentation as beautiful as you would like it (or at the least tolerable). You can learn more about customizing Jekyll [here](https://jekyllrb.com/).

## <a name="sass" class="anchor">SASS</a>

The Jekyll gem depends on SASS for styling. The [Jekyll Cayman Theme](https://github.com/pages-themes/cayman) is our base style and we have overriden some styles in the ./_assets/css/style.scss file. You can add any of your modifications there. These files are detected by Jekyll, converted to css, and added to the generated web content under _sites/assets/css/style.css. You can learn more about SASS, or "css with superpowers" [here](http://sass-lang.com/).

## <a name="images" class="anchor">Images and Other Assets</a>

All images can be placed in the root images directory under a logical organizational structure, as needed. If you have videos or other assets, you can create separate directories for those and they should be detected by Jekyll and added to the generated web content under _sites/. You can learn how to reference images and other assets in your *.md files via the [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

