---
layout: page
title: Course Pages
subtitle: Courses
menubar: docs_menu
show_sidebar: false
toc: true
---

## Courses Directory

The default collection name for courses is `courses`, so create a `_courses` directory to hold your course pages.

## Custom Collection Directory

**Added in v1.0.4**

You can override the default and create a folder with your own collection name. For example, using a collection of `books` would require you to create a folder called `_books`.

## Course Pages

 Create a new page for each course, such as `course1.md`. In the front matter for this page you can set the standard settings, such as your title, subtitle, description (for meta-description), hero_image, as well as the additional course settings such as semester, course_code, image, features, and rating. 

```yaml
title: Course 1 Name
subtitle: Course 1 tagline here
description: This is a course description
hero_image: /img/hero-img.jpg
course_code: ABC124
layout: course
image: https://via.placeholder.com/640x480
semester: £1.99 + VAT
features:
    - label: Great addition to any home
      icon: fa-location-arrow
    - label: Comes in a range of styles
      icon: fa-grin-stars
    - label: Available in multiple sizes
      icon: fa-fighter-jet
rating: 3
```

The text you write for the page content will be displayed as the course description. 

[View example Course page](/bulma-clean-theme/courses/course2/)

## Course Collections 

Next, add the following to your `_config.yml` to use collections to process the course pages and output them as individual pages. 

```yaml
collections:
  courses: 
    output: true
    layout: course
    image: https://via.placeholder.com/800x600
    show_sidebar: false
```

You can also set default course page values here if you like, such as the layout or image. 

{% include notification.html message="If you use a custom collection name then update `courses` to your custom collection name. In the example above for the `_books` folder use `books` as the collection name." %}

For more information on collections, please refer to the [Jekyll documentation](https://jekyllrb.com/docs/collections/). 