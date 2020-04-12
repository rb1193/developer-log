# Elasticsearch

## Indexing

It’s possible to set a custom ID when indexing items in ElasticSearch

When changing mappings for search indexes, the best approach is always to create a new index with the new mapping, index all the data to the new index, and then switch config to point to the new index once it’s good and ready. Updating the mapping on an existing index isn’t really possible
