---
layout: page
title: Category Page
subtitle: Courses
menubar: docs_menu
show_sidebar: false
toc: true
---

## Category Page

To create a category page listing your courses you will need to create a course category page. 

Create a page, for example `courses.md`, with the `layout: course-category` in the front matter. You can set the sort order of the courses using `sort: title` to sort by the title, or by any setting in your course pages, such as price, rating or any custom front matter tags you wish to set. 

```yaml
title: Courses
subtitle: Check out our range of courses
layout: course-category
show_sidebar: false
sort: title
```

[View example Category page](/bulma-clean-theme/courses/)

## Customising the collection

**Added in v1.0.4**

To use a different collection than `courses`, set the collection name in the category page's front matter. 

The below example uses a collection called `books`. 

```yaml
title: Books
subtitle: Check out our range of books
layout: course-category
show_sidebar: false
sort: title
collection: books
```