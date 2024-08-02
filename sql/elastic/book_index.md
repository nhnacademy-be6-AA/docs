elasticsearch index

```
DELETE /aa-bb_book_index

PUT /aa-bb_book_index
{
  "settings": {
    "analysis": {
      "analyzer": {
        "nori_analyzer": {
          "type": "custom",
          "tokenizer": "nori_tokenizer",
          "filter": [
            "nori_part_of_speech",
            "lowercase",
            "nori_readingform",
            "cjk_bigram"
          ]
        }
      },
      "filter": {
        "nori_part_of_speech": {
          "type": "nori_part_of_speech",
          "stoptags": [
            "E", "IC", "J", "MAG", "MAJ", "MM", "SP", "SSC", "SSO", "SY",
            "UNA", "VSV", "VV", "VX", "XPN", "XSA", "XSN", "XSV"
          ]
        }
      }
    }
  },
  "mappings": {
    "properties": {
      "bookId": { "type": "long" },
      "productId": { "type": "integer" },
      "isbn": { "type": "keyword" },
      "bookTitleEng": { 
        "type": "text", 
        "analyzer": "standard" 
      },
      "bookTitle": { 
        "type": "text", 
        "analyzer": "nori_analyzer" 
      },
      "description": { 
        "type": "text", 
        "analyzer": "nori_analyzer" 
      },
      "forwardDate": { 
        "type": "date" 
      },
      "authors": { 
        "type": "text", 
        "analyzer": "nori_analyzer" 
      }
    }
  }
}
```



