---
title: 'Home'
date: 2023-10-24
type: landing
sections:
  - block: resume-biography
    content:
      # The user's folder name in content/authors/
      username: admin
    design:
      spacing:
        padding: [0, 0, 0, 0]
      biography:
        style: 'text-align: justify; font-size: 0.8em;'
  - block: collection
    content:
      title: hugo - default
      filters:
        folders:
          - card
    design:
      spacing:
        padding: ['3rem', 0, '3rem', 0]

  - block: collection
    content:
      title: weeknotes
      filters:
        folders:
          - weeknotes
    design:
      spacing:
        padding: ['3rem', 0, '6rem', 0]
  - block: collection
    content:
      title: travel
      filters:
        folders: 
          - travel
    design:
      spacing:
        padding: ['3rem', 0, '9rem', 0]
---
