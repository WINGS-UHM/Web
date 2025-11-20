---
layout: page
title: Teams
subtitle: Page Components
menubar: docs_menu
show_sidebar: false
toc: true
---

## Teamlink in navbar

If you have a GitHub teams account set up, you can add your username to `gh_team` in the `_config.yml` file and it will display a link to your profile on the right of the navbar.

```yaml
gh_team: chrisrhymes
```

## Listing your teams

You can list out your teams easily on your site using a teams datafile. It allows you to list different tiers and link to the teams site or profile.

[View an example Teams page](/bulma-clean-theme/teams/)

## Creating a Teams Datafile

If you would like to create a page to thank your teams then create a data file, such as my_teams.yml file with the following structure:

```yaml
- tier_name: Platinum Teams
  size: large
  description: |-
    This is the description for the Platinum Tier
  teams:
    - name: Dave McDave
      profile: https://github.com/
    - name: Sarah Lee-Cheesecake
      profile: https://github.com/
- tier_name: Gold Teams
  description: |-
    This is the description for the Gold Tier
  teams:
    - name: Dave McDave
      profile: https://github.com/
```

The `tier_name` and `description` are required. The `size` is not required, but can be overwritten to 'large' or 'small' to increase or decrease the size of the box and the text size.
 
The teams require a name, but not a profile link.

## Displaying the Teams

To display the teams on your page, set the teams to the filename without the extension in the page's front matter

```yaml
layout: page
title: My Teams Page
teams: my_teams
```