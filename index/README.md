## Virtual Public Square Indexes

Feeds and Lists are assembled from queries executed against search clusters
containing the content handled by that Virtual Public Square. Dedicated indexes
for specific use cases are supported, with Feed and Search as the two initial
examples. Feed clusters contain a smaller data set of recent content and support
complex queries, often matching hundreds of publishers, while Search
clusters hold content much longer and anticipate smaller but more varied queries.
The retention window in each cluster is set based on the policy of that Virtual
Public Square, which is subject to change.

### Query Results
Query results are packaged in JSONL and delivered by an API server. Typically,
the JSONL files are served via CDN with the API acting as an origin to reduce
traffic to the API systems.

### Implementations
The initial implementation of indexes is on OpenSearch. The Virtual Public Square
API code could be refactored to support lighter weight indexes for specific use
cases if desired.
