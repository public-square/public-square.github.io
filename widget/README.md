## Virtual Public Square Website Plugins & Widgets

Website widgets display a list, a feed or a set of search results in an iframe
on a website. High traffic publishers use PSQR widgets to exchange referral traffic
within a group, enhancing reach and engagement for all participants.

The `Virtual Public Square` WordPress plugin hosts `did:psqr` identities on WordPress
site for the entire domain or individual authors.

### Exchanging Referral Traffic with Website Widgets

#### 1. Create an Identity and Publish
Use the `psqr` command to create key pairs and an identity to host on your own
website. This identity will be displayed with your content, and the keys you
create will be used to sign that content, proving it is yours.

The `psqr` command can be scripted to crawl sitemaps and RSS to publish new
content to a Virtual Public Square. Refer to the CLI documentation for details.

Note that if your site runs WordPress, the Virtual Public Square plugin handles
identity, publishing to a Virtual Public Square (soon), and PSQR Widgets as
blocks (soon). The plugin supports root domain identity for the entire site, and
identities for individual authors which share the author profile URL.

#### 2. Find Collaborators
Reach out to other publishers you wish to exchange traffic with and ensuring they
are publishing to the same Virtual Public Square on a regular basis and assemble
a list of identities used by the group. These identities will form the basis of
the content that appears in your widget.

#### 3. Create a Feed and List
Using all of the identities in the group, create a feed to capture everything
from any of the publishers in the group. This feed may be used to populate the
widgets directly if low overhead is preferred and curation is not needed.

To support curation, create a list specifically for you site and schedule the
`psqr` command to update it periodically. Grant `curate` permission on this list
to an instance of the web application for granular manual control over widget
contents, including removing specific entries and adding others at will.

#### 4. Add a Widget to Each Site in the Group
Include a widget on each website as an iframe tag referencing the feed or list to
display on that site. These widgets may all reference lists are curated individually,
or they may share a singular list.

If the sites run WordPress, the Virtual Public Square plugin is used to add Widgets
as theme blocks (coming soon).
