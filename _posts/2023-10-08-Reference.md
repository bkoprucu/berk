---
author: "Berk Koprucu"
title: "Variable reference"
subtitle: "List of front matter variables"
excerpt_text: "Front matter reference" # Custom excerpt text
description: "Seo description"
#seo_enabled: true # Force seo for hidden page
#excerpt_image: /assets/images/test/diagram_1.png
#banner: /assets/images/test/berk_logo_funny.png
#excerpt_image_on_page: true # false: Don't show except image on the pag, only on listing
#excerpt_image_page_style: 'max-height: 150px'
categories: [Other]
tags: []
hide: [related, navigator] # Can be header, tags, navigator, related, comments. Implementation in post.html
hidden: true # Hide from listing
published: false
permalink: "/reference.html"  # Custom url
sidebar: [article-menu] # about-box, article-menu, category-list, tag-list, archive-list
---

## Reference

Front matter reference

```
author: "Berk Koprucu"
title: "Parameter reference"
subtitle: "List of front matter variables"
seo_enabled: true # Force seo for a hidden page
excerpt_text: "Front matter reference" # Custom excerpt text
excerpt_size: 100 # Custom excerpt size
excerpt_image: /assets/images/test/berk_logo_funny_2.png
excerpt_image_copyright: 'Image by Blabla'
excerpt_image_on_page: false # Don't show except image on post page, only on listing
excerpt_image_page_style: 'max-height: 150px' # Apply CSS to excerpt image
banner: /assets/images/test/berk_logo_funny.png
banner_credit: 'Photo by Casey Horner' 
categories: [Test]
tags: [AWS, Spring]
sidebar: [about-box] # One of: 'about-box', 'article-menu', 'category-list', 'tag-list', 'archive-list'
hide: [related, navigator] # Can be 'header', 'navigator', 'related', 'comments', 'share'. Implementation in post.html
hidden: 1 # Hide from listing
hide_from_related: 1   # Don't appear in "More Articles"
permalink: "/reference.html"  # Custom url
# top: 1 # Pinned post 


// -- Maintenance:
`bundle update`
`jek = bundle exec jekyll`
`jek clean`
`jek build`
`jek s` 
```
