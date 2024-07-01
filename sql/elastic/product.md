
DELETE /aa-bb_author_index
DELETE /aa-bb_book_index
DELETE /aa-bb_category_index
DELETE /aa-bb_product_index
DELETE /aa-bb_publisher_index
DELETE /aa-bb_tag_index


POST /_aliases
{
    "actions": [
    { "add": { "index": "aa-bb_author_index", "alias": "aa-bb_index" } },
    { "add": { "index": "aa-bb_book_index", "alias": "aa-bb_index" } },
    { "add": { "index": "aa-bb_category_index", "alias": "aa-bb_index" } },
    { "add": { "index": "aa-bb_product_index", "alias": "aa-bb_index" } },
    { "add": { "index": "aa-bb_publisher_index", "alias": "aa-bb_index" } },
    { "add": { "index": "aa-bb_tag_index", "alias": "aa-bb_index" } }
    
  ]
}


PUT /aa-bb_author_index
{
  "mappings":{
    "properties": {
      "id": { "type": "integer" },
      "name": { "type": "keyword" },
      "books": {"type": "nested", "properties": {"book_id":{"type":"integer"}}
      }
    }
  }
}



PUT /aa-bb_book_index
{
  "mappings": {
    "properties": {
      "id": { "type": "long" },
      "title": { "type": "text", "analyzer": "nori" },
      "description": { "type": "text", "analyzer": "nori"},
      "isbn": { "type": "keyword" },
      "publisher_id": { "type": "integer" },
      "publish_date": { "type": "date" },
      "product_id": { "type": "integer" },
      "authors": { "type": "nested", "properties": {"author_id":{"type":"integer"}}
      }
    }
  }
}



PUT /aa-bb_category_index
{
  "mappings": {
    "properties": {
      "id": {"type": "integer"},
      "name": {"type": "keyword"},
      "parentCategory": {"type": "join", "relations":{"category": "category"}}
    }
  }
}



PUT /aa-bb_product_index
{
  "mappings": {
    "properties": {
      "id": {"type": "integer"},
      "stock": {"type": "integer", "index": false},
      "productName": {"type": "text", "analyzer": "nori"},
      "description": {"type": "text", "analyzer": "nori"},
      "price": {"type": "integer","index": false},
      "forwardDate": {"type": "date"},
      "score": {"type": "integer", "index": false},
      "thumbnailPath": {"type": "keyword", "index": false, "doc_values": false},
      "stockStatus": {"type": "keyword"},
      "category_id": {"type": "integer"},
      "tags": {"type": "join", "relations":{"product": "tag"}
      }
    }
  }
}



PUT /aa-bb_publisher_index
{
  "mappings": {
    "properties": {
      "id": {"type": "integer"},
      "name": {"type": "keyword"}
    }
  }
}



PUT /aa-bb_tag_index
{
  "mappings": {
    "properties": {
      "id": {"type": "integer"},
      "name": {"type": "keyword"}
    }
  }
}




