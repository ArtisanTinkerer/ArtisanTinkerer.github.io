---
layout: post
title: "The Pizza Hut Pickle"
date: 2016-02-12
---

How can I handle those pesky product codes?

I want a user to be able to type WH CP100 or WHCP100 and the Twitter Typeahead will still work.

## The Solution

I read this:
[Elastic Search as You Type](https://www.elastic.co/guide/en/elasticsearch/guide/current/_index_time_search_as_you_type.html)

Then this:
[Pizzah not Pizza H](https://medium.com/@davedash/writing-a-space-ignoring-autocompleter-with-elasticsearch-6c3c28e3a974#.5rmprpbaf)

Then followed these steps:

### 1 Fire this in the command line:

```

curl -XPUT "http://blahblah:9200/parts" -d '
{
    "settings": {
        "number_of_shards": 1, 
"analysis": {
  "filter": {
    "autocomplete_filter": {
      "type": "edge_ngram",
      "min_gram": "1",
      "max_gram": "20"
    },
    "word_joiner": {
      "type": "word_delimiter",
      "catenate_all": true
    }
  },
  "analyzer": {
    "autocomplete": {
      "type": "custom",
      "filter": [
        "lowercase",
        "word_joiner",
        "autocomplete_filter"
      ],
      "tokenizer": "keyword"
    }
  }
}
    }
}
'

```

### 2 Add the mapping.

```
curl -XPUT "http://blahblah:9200/parts/_mapping/parts" -d '

{
    "parts": {
        "properties": {
            "PART_NO": {
                "type":     "string",
                "analyzer": "autocomplete"
            }
        }
    }
}'

```

### Test
```
curl -s -XGET 'http://blahblah:9200/parts/_analyze?analyzer=autocomplete&pretty=1' -d "Pizza Hut"|jq ".tokens[]|.token" -r
```

Then I added all to the index, using:
[Elasticquent](https://github.com/elasticquent/Elasticquent)

The Twitter Typeahead uses AJAX to call this:


    $products = Product::complexSearch(array(
            'body' => array(
                'query' => array(
                    'match' => array(
                        'PART_NO' => $

        $arrProducts = $products->

        return response()->json( $arrProducts);
        
```
        
Bingo! It worked.
