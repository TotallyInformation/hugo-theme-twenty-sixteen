---
title: "{{ replace .Name "_" " " | replace .Name "-" " " | title }}"
description: 
date: {{ .Date }}
lastMod: {{ .Date }}
draft: true
comments: true
# aliases [], expiryDate, headless, keywords, layout, linkTitle, outputs, publishDate. slug, taxonomies, type, url, weight
# tags: [], categories: [], menu
---