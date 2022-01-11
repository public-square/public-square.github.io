## Interoperability of Virtual Public Squares

The Virtual Public Square is comprised of multiple instances of the Virtual
Public Square component software operated and controlled by different people or
companies.

The overall system exhibits an extreme degree of openness, driven by the unusual
characteristics of the initial design. The most important of these characteristics
are globally unique addressing and recognition that content in the public square
is public by definition.

### Virtual Public Square Characteristics

#### Exclusively Public
Publishers post content to Virtual Public Squares to gain reach for that content.
In some cases, the content might be complete works, and in other cases it will be
summaries linking back to websites for the purpose of generating traffic.

This content is portable between Virtual Public Squares without loss of
cryptographic provenance and without any change in the primary key of the content.

Virtual Public Squares serve feeds, lists, and search results over HTTPS as simple
JSONL files, with each line containing an article of content.

#### Globally Unique Identity
Publishers create and host their own decentralized identities using the did:psqr
standard and namespace within the overall W3C Decentralized IDentity framework.

This is easily accomplished. The PSQR command line interface generates keys and
identity documents that are served as static content. The PSQR WordPress plugin
handles proper did:psqr responses to make identities available for an entire site
or for specific user profiles on a site.

#### Globally Unique Content Addressing
Each article of content posted to a Virtual Public Square is identified with a
content address. The address is a simple hash of metadata and it does not change
as the content moves from Virtual Public Square to Virtual Public Square.

### The Mechanics of Interoperability

#### Feeds and Lists
The contents of a typical Virtual Public Square Feed can be examined with standard
software tools. Simply GET the Feed over HTTPS and examine the data. Each line of
a Feed contains an article of content, and each article of content identifies the
publisher and contains a JSON Web Signature that can be validated with the
public key in the did:psqr identity of the publisher.

```
curl --silent \
https://feed.ology.com/feed/politics-mainstream/latest.jsonl | \
head -1 | jq
```

#### Replicating an Entire Virtual Public Square
If there is a concern with the policies of any Virtual Public Square, the content
can easily be replicated and distributed in another Virtual Public Square operated
by some other group.

The broadcast firehose is also available as JSONL, but containing the JSON
Web Tokens posted by publishers directly so that any other Virtual Public Square
component may validate and ingest it all to create a new instance.
```
curl --silent \
https://broadcast.ology.com/broadcast/latest.jsonl | \
head -2 | jq
```
