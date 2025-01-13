We can use markdown inside astro using the `.md` extention.

## YAML
YAML are the values that we put inside the 3 slashes up top:

```markdown
title: 'My First Blog Post'
pubDate: 2022-07-01
description: 'This is the first post of my new Astro blog.'
author: 'Astro Learner'
```

They are not included in the markdown file, but we can use them using our
layouts.

## creating layout for our markdown

We should create layout for our markdown so that we can use the 
YAML values 

We simply create a layout file with which we get the `frontmatter` value
from `Astro.props`:

```Astro
---
const { frontmatter } = Astro.props;
---
<h1>{frontmatter.title}</h1>
<p>Written by {frontmatter.author}</p>
<slot />
```

the frontmatter would use the YAML values.

We need the layout option in YAML in order to use the layout

```Markdown
layout: ../../layouts/MarkdownPostLayout.astro
title: 'My First Blog Post'...
```

