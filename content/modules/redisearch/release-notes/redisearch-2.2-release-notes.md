---
Title: RediSearch 2.2 release notes
linkTitle: v2.2 (November 2021)
description: Search and index JSON documents. Profiling queries. Field aliasing. 
min-version-db: "6.0.0"
min-version-rs: "6.0.0"
weight: 94
alwaysopen: false
categories: ["Modules"]
---
## Requirements

RediSearch v2.2.5 requires:

- Minimum Redis compatibility version (database): 6.0.0
- Minimum Redis Enterprise Software version (cluster): 6.0.0

## v2.2.5 (November 2021)

This is the General Availability release of RediSearch 2.2.

### Headlines

#### Searching and indexing JSON documents

This release introduces the ability to [index, query, and full-text search JSON documents](https://oss.redis.com/redisearch/master/Indexing_JSON/) using JSONPath queries.

On the schema creation [FT.CREATE](https://oss.redis.com/redisearch/master/Commands/#ftcreate), it is now possible to map a JSONPath query with a field. When a JSON document is indexed, the value extracted by the JSONPath query is indexed in the given field.

 _This features require the module [RedisJSON 2.0](https://www.redisjson.io) to be installed._ 

#### Profiling queries

With the new [FT.PROFILE](https://oss.redis.com/redisearch/master/Commands/#ftprofile) command, it is now possible to profile in detail the execution time of several internal steps involved in the execution of [FT.SEARCH](https://oss.redis.com/redisearch/master/Commands/#ftsearch) and [FT.AGGREGATE](https://oss.redis.com/redisearch/master/Commands/#ftaggregate).
That way, it is possible to understand which part of the query is taking most of the resources.

#### Field aliasing

With the support of JSON document indexing, it is now possible to map a JSONPath query to an alias. Therefore, it is possible to index the same value in different fields with different indexing strategies.

### Details

- Enhancements:
  - #[2337](https://github.com/redisearch/redisearch/issues/2337) Add support for Redis COPY command 
  - #[2243](https://github.com/redisearch/redisearch/issues/2243) Add `LOAD *` for [FT.AGGREGATE](https://oss.redis.com/redisearch/master/Commands/#ftaggregate)
  - #[2207](https://github.com/redisearch/redisearch/issues/2207) Add multi value recursive decent tag
  - #[2188](https://github.com/redisearch/redisearch/issues/2188) Add [UNF flag for SORTABLE](https://oss.redis.com/redisearch/master/Sorting/#normalization_unf_option) fields
  - #[2184](https://github.com/redisearch/redisearch/issues/2184) LLAPI getter functions for score, language, and stopwords list
  - #[2133](https://github.com/redisearch/redisearch/issues/2133) JSON array can be stored in a TAG field
  - #[2153](https://github.com/redisearch/redisearch/issues/2153) Improve [FT.INFO](https://oss.redis.com/redisearch/master/Commands/#ftinfo) complexity to O(1) 
  - #[2138](https://github.com/redisearch/redisearch/issues/2138) Add [CASESENSITIVE](https://oss.redis.com/redisearch/master/Tags/#creating_a_tag_field) to TAG fields
  - #[2137](https://github.com/redisearch/redisearch/issues/2137) [FT.INFO](https://oss.redis.com/redisearch/master/Commands/#ftinfo) has identifier and attribute for fields

- Bug fixes:
  - #[2341](https://github.com/redisearch/redisearch/issues/2341) Fix score field for JSON
  - #[2325](https://github.com/redisearch/redisearch/issues/2325) Fix escaping for tags
  - #[2269](https://github.com/redisearch/redisearch/issues/2269) Remove empty tag values
  - #[2223](https://github.com/redisearch/redisearch/issues/2223) Replace NULL with empty iterator for child of negative iterator
  - #[2215](https://github.com/redisearch/redisearch/issues/2215) Update field limit on tags
  - #[2143](https://github.com/redisearch/redisearch/issues/2143) Partial JSON documents are not indexed
  - #[2109](https://github.com/redisearch/redisearch/issues/2109) Field loaded with 'AS' can't be used by functions

Notes:
This is the first GA version of 2.2. The version inside Redis will be 2.2.5 in semantic versioning.
_Since the version of a module in Redis is numeric, we could not add a GA flag._
