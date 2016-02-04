---
title: A draft post
layout: post
---
Drafts are posts without a date. They're posts you're still working on and don't want to publish yet. To get up and running with drafts, create a `_drafts` folder in your site's root.

```
|-- _drafts/
|   |-- a-draft-post.md
```

## Front matter

The front matter is where Jekyll starts to get really cool. Any file that contains a YAML front matter block will be processed by Jekyll as a special file. The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines.

### Posts

```
---
title: Some catchy title
layout: post
date: 2016-02-03 21:18:21 +0100
tags: [csharp, web]
---
```

- `title` The post title, no magic here.
- `layout` This should always be "post".
- `date` Current danish date, time and timezone. Jekyll will take care of the rest.
- `tags` List of keywords, used to find related posts.

### Pages

```
---
title: This is awesome!
layout: page
summary: This text is bigger then the rest.
---
```

- `title` The page title, still no magic here.
- `layout` This should always be "page".
- `summary` Short text about the page. This is bigger.

## Publish a post

When the post is ready to be published, update the `date` front matter with the current timestamp and timezone.

Rename the file to include the publish date `YYYY-MM-DD-title.md`, and move it to the `_posts` folder. Your post should no be published.
