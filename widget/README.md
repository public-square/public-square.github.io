## Virtual Public Square Website Plugins & Widgets

Website widgets display a list, a feed or a set of search results in an iframe
on a website. High traffic publishers use PSQR widgets to exchange referral traffic
within a group, enhancing reach and engagement for all participants.

The `Virtual Public Square` WordPress plugin hosts `did:psqr` identities on WordPress
site for the entire domain or individual authors.


## Widget Components

The Ology Newswire Widget is composed of 2 components: the widget web page and the insertion script. The widget web page pulls in the content from a list specified in the url params and displays it in the desired format. The insertion script creates iframes on the page that it is loaded onto and sets the appropriate size.

## Widget Web Page

The web page is located at [https://broadcast.ology.com/embed/](https://broadcast.ology.com/embed/) and accepts the following url parameters:

* `url`: this is the url for the list or feed that contains the content to be displayed. For example: `url=https://list.ology.com/list/example-list/index.jsonl`
* `format`: this specifies which widget format you want to use with the list, the default is `feed` but options include `med-rect, wide-sky, billboard, widget, responsive, feed, fallback`
* `style`: this allows you to specify some basic css styles that will be applied inline to the `body` tag of the widget, this **must** be encoded with `encodeURIComponent()`

You can create an iframe and add the widget url as a source but you will need to specify the width and height and any other styling for the iframe.

### Widget Formats

Widget formats have default sizes that they will use. `med-rect`, `wide-sky`, and `billboard` are designed for those exact sizes but should be able to handle some slight variation. `widget`, `responsive`, and `feed` are more adaptable with `widget` and `feed` meant for tall sizes and `responsive` being the most adaptable.

* `med-rect` (300x250): standard medium-rectangle unit as offered by google ads
* `wide-sky` (320x600): wide skyscraper unit with double the width to fit content
* `billboard` (970x250): standard billboard unit as specified by iab
* `widget` (1000x600): widget unit matching the required minimum size by taboola
* `responsive` (390x844): responsive unit that should work with most medium-large sizes
* `feed` (1100x980): responsive unit that is meant for long feeds


## Widget Insertion Script

The insertion script is located at [https://broadcast.ology.com/embed/ology-newswire-widget.js](https://broadcast.ology.com/embed/ology-newswire-widget.js). It is best included in the beginning of the `body` but it can be included anywhere. It will search the page for `a` tags with the class `js-ology-widget` and convert them into iframes with the specified config and the appropriate size.

### Anchor Tag

The anchor tag contains all of the configuration for the iframe you can specify the default src, custom styles, and breakpoint configuration. Here's an example tag:

```html/text
<a class="js-ology-widget" href="https://broadcast.ology.com/embed/?format=feed&url=https://list.ology.com/list/example-list/index.jsonl" target="_blank"
    style="background-color: rgb(227, 227, 227)"
    data-breakpoints='{
        "0": {"width": 300, "height": 250, "format": "med-rect"},
        "576": {"width": 320, "height": 600, "format": "wide-sky", "src": "https://broadcast.ology.com/embed/?format=feed&url=https://list.ology.com/list/other-list/index.jsonl"},
        "992": {"format": "billboard"}
    }'
>Ology Newswire</a>
```

* `style`: this is a standard inline style attribute, all styles specified here will be added to the `body` as an inline style attribute
* `data-breakpoints`: this is a json array that contains any changes you need to make at the specified breakpoints
* `href`: this is the base widget url that will be used, it's the only required attribute

### Breakpoint Config

The breakpoint config is a json string where each property is a breakpoint. The key is the minimum size for the breakpoint and the object can specify the `format`, `src`, `width`, and `height`.

* `format`: this allows you to override the format at the specified breakpoint, it will override the format contained in the `src` if both are present
* `src`: this is the full url src for the widget, this allows you to change the url or any other param
* `width`: all formats have a default width but you can override it with this
* `height`: all formats have a defualt height but you can override it with this

## Exchanging Referral Traffic with Website Widgets

### 1. Create an Identity and Publish
Use the `psqr` command to create key pairs and an identity to host on your own
website. This identity will be displayed with your content, and the keys you
create will be used to sign that content, proving it is yours.

The `psqr` command can be scripted to crawl sitemaps and RSS to publish new
content to a Virtual Public Square. Refer to the CLI documentation for details.

Note that if your site runs WordPress, the Virtual Public Square plugin handles
identity, publishing to a Virtual Public Square (soon), and PSQR Widgets as
blocks (soon). The plugin supports root domain identity for the entire site, and
identities for individual authors which share the author profile URL.

### 2. Find Collaborators
Reach out to other publishers you wish to exchange traffic with and ensuring they
are publishing to the same Virtual Public Square on a regular basis and assemble
a list of identities used by the group. These identities will form the basis of
the content that appears in your widget.

### 3. Create a Feed and List
Using all of the identities in the group, create a feed to capture everything
from any of the publishers in the group. This feed may be used to populate the
widgets directly if low overhead is preferred and curation is not needed.

To support curation, create a list specifically for you site and schedule the
`psqr` command to update it periodically. Grant `curate` permission on this list
to an instance of the web application for granular manual control over widget
contents, including removing specific entries and adding others at will.

### 4. Add a Widget to Each Site in the Group
Include a widget on each website as an iframe tag referencing the feed or list to
display on that site. These widgets may all reference lists are curated individually,
or they may share a singular list.

If the sites run WordPress, the Virtual Public Square plugin is used to add Widgets
as theme blocks (coming soon).
