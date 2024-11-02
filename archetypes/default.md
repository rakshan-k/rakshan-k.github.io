---
date: {{ page.date | date: "%d-%m-%Y" }}
draft: true
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
---
