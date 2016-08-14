Red Hat Presentation Ligth Template.

Adaptation from the official 16x9 Google template to the Remark template slideshow tool.

Display tested under Chrome and Firefox in Fedora with 1920x1080 resolution.

# Introduction

Marketing has worked hard creating [templates for multiple presentation tools](https://mojo.redhat.com/docs/DOC-1039153):

- Google docs templates
- OpenDocument Presentation templates
- Keynote themes
- Microsoft PowerPoint Open XML templates
- Slides.com templates

But many engineers prefer working with a text tool that allows them to focus on the content away from the distractions of the layout formatting and that's why the Remark slideshow tool is one of the preferred tools for presentations.

Other advantage of using Remark include being able to use versioning tools, easy hosting with GitHub pages, and usage of open technologies.

The purpose of this template is make it easier for Remark users to present a common front with the rest of the company and remove the conflict of having to choose between following marketing request and using their preferred presentation tool.


# Acknowledgements

I initially created the template using full pictures for the backgrounds, but after seeing Alex Szczucko's superior approach in [his template](http://git.engineering.redhat.com/git/users/aszczucz/remark-redhat/) decided to change this template to do composite backgrounds.


# Differences with the original

While I have tried to maintain the presentation as close to the original as possible, there are some differences, some improvements, some not so much:

- The most important slides have been ported to Remark, but not all of them.
- The font used in this template is not the font used in the Google template -Proxima Nova- because it has licensing restrictions that would probably result in copyright infringement if stored openly in GitHub.  Free font "Montserrat" has been used instead for this template due to its likeliness, and is included in the fonts directory to prevents offline presentations from using other fonts.
- In the Google docs template that was used as reference the *designator* section on the slides' footer could not be changed, something that has been corrected in this template.
- Background images will have a thin white line at the bottom in Chrome and on the sides in Firefox.  This has nothing to do with the original images used or the conversion to jpg, it is due to Remark's way of building the slides and the scaling mechanism used.
- On the *thank you* slides the links to Google plus, LinkedIn, YouTube, etc. are actual links and not just text.
- There are 2 background images of rice fields on a mountain that originally had the 2 rightmost pictures on the right suffering from an aliasing effect, this has been corrected in the pictures used in this template.
- An additional slide has been added with a Creative Commons license.


# Adapting the template

## Title

The page's title is on line 4 in the `index.html` file and should always be changed to the name of our presentation.

In the template we use a layout called *title_layout* for the title pages because we have more than one sampling the different options, but for your presentation you may want to just remove the template and use directly the *title_slide* class in the title slide.

The picture used for default is *assets/background_title_red.jpg* and can be easily changed adding to the slide classes one of the other 2 title image's classes: *bg_building_red* or *bg_clouds_red* or directly modifying the CSS file, changing the *background-image* attribute in *.remark-slide .title_slide* to the one we want to use.

Create a title slide with the building background using a template would look like this:

```
layout: true
name: title_layout
class: title_slide bg_building_red

---

template: title_layout

# PRESENTATION TITLE SHOULD NOT EXCEED TWO LINES

## Subheading goes here

Presenter<br>
Presenter's title<br>
Date<br>
```

Without creating a template it would look like this:

```
class: title_slide bg_building_red

# PRESENTATION TITLE SHOULD NOT EXCEED TWO LINES

## Subheading goes here

Presenter<br>
Presenter's title<br>
Date<br>
```

## Agenda

Same as with the title we can either use existing *section_layout* template or use the *section_slide* class directly.

The agenda is a normal content slide -more details [in that section](#Content)- presented in 2 columns, so it uses the [2 column slide formatting](#Two columns), using one line for the time and another for the topic.

Due to markdown formatting you'll need an empty line in your *index.html* between each of the lines, as can be seen in the template, and as long as you respect the order of *time* then *topic* the CSS will do the formatting automatically without you needing to define which line is the time and which the topic.

## Sections

These are also called **dividers** and they are available in green and red versions being the default the red version with no background image.

Same as before we have a template already defined -*section_layout*- or we can use the class *section_slide*.

We have a good number of classes that can be added to the slide or the template to use different backgrounds:

- *bg_greeen*
- *bg_building_2_green*
- *bg_rice_green*
- *gb_bridge_green*
- *gb_bridge_2_green*
- *bg_waterfall_green*
- *bg_building_2_red*
- *bg_rice_red*
- *gb_bridge_red*
- *gb_bridge_2_red*
- *bg_waterfall_red*

## Content

Content layout has a template already defined -*content_layout*- or we can use the class *content_slide*, but unlike before we don't have different backgrounds available.

If you use layouts please be careful to define the default slide template as the last layout, as Remark will make it the default one.  Doing it this way will allow you to skip defining the layout to use in all your content slides.

We have three different headings defined for the content pages, h1 -`#`- is meant for the slide header, h2 -`##`- for the slide subheader and h3 -`###`- for any header that we need in the slide's content.  H2 and h3 have the same size, but the later uses bold for the font weight.

### Incremental Slides

The template assumes that incremental slides -defined by `--` instead of `---`- are used as animations and not to create complete new slides, so the page count will not be incremented.

If this is not the desired behavior it can be easily changed at the bottom of the *index.html* file, replacing where it says `countIncrementalSlides: false` with `countIncrementalSlides: true`.

### Page numbers

Page numbers are displayed in the page's footer as they were in the Google doc template, but they can easily be adapted to your preferences in the *index.html* by changing the contents of the `slideNumberFormat` dictionary key.

Displaying the total number of slides beside the current page number can be achieved using the `%total%` placeholder changing `slideNumberFormat: '%current%` with `slideNumberFormat: '%current%/%total%`.

### Designator

The designator is part of the footer where the slide number resides -in the `slideNumberFormat` value- and should be changing from the value defined in this template.  It is important to preserve it inside the `spam class` so that the proper formatting can be applied.

In the footer we preserve the spaces, instead of the default behavior of consolidating all spaces into a single one, to provide more freedom manually separating the slide number from the designator without having to change the CSS.

### Tables

We don't need to define any special class when creating tables, as they will default to the right formatting automatically with a red background for the header.

Besides the default background color for the header all other corporate and secondary colors are also available as allowed by the guidelines using these classes:

- *blue-table*
- *light-blue-table*
- *dark-gray-table*
- *light-gray-table*
- *black-table*
- *white-table*
- *red-table*
- *dark-red-table*

Header font color is white for all except for when we use the white background when the color will be black for obvious reasons.

For example to use the blue background for the header we would do it like this:

```
.blue-table[
| VALUE | VALUE | VALUE | VALUE |
|:-----:|:-----:|:-----:|:-----:|
| value | value | value | value |
| value | value | value | value |
| value | value | value | value |
]
```

### Code snippets

Code snippets use default markdown code formatting and the font size is close to the one defined in the original template, but we'll probably want to change this size and we can easily do this in CSS under the *Code snippets* section in `.remark-code *`.

### Two columns

We can define two column slides using classes *left-column* and *right-column* like this:

```
.left-column[
On the left column
...
]

.right-column[
On the right column
...
]
```

### Three columns

Like with two columns, we can also define slides with three columns and we'll use classes *left-column-3*, *middle-column-3*, and *right-column-3*.

## Thank you

The thank you slide uses define *thank_you* template or *thank_you* class and by default uses the red thank you background with no photograph.

Other backgrounds can be used instead of the default using classes *bg_thank_you_building* or *bg_thank_you_mountains*.

To position the links to the different social media sites we must use following classes:

- *google_plus*
- *linkedin*
- *youtube*
- *facebook*
- *twitter*

I recommend making these link actual HTML links instead of just text:

```
.google_plus[
[plus.google.com/+RedHat](https://plus.google.com/+RedHat)]

```
