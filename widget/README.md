## Virtual Public Square Website Widgets

Website widgets display a list, a feed or a set of search results in an iframe
on a website. High traffic publishers use PSQR widgets to exchange referral traffic
within a group, enhancing reach and engagement for all participants.

### Exchanging Referral Traffic with Website Widgets

#### 1. Create an Identity and Publish
Use the `psqr` command to create key pairs and an identity to host on your own
website. This identity will be displayed with your content, and the keys you
create will be used to sign that content, proving it is yours.

The `psqr` command can be scripted to crawl sitemaps and RSS to publish new
content to a Virtual Public Square. Refer to the CLI documentation for details.

Note that if your site runs WordPress, the PSQR WordPress plugin handles identity
and publishing to a Virtual Public Square. (Coming soon.)

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
