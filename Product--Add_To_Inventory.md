### URLs

POST /products/inventory-lists/<inventory-list-uuid>/add-items
POST /products/inventory-lists/<inventory-list-uuid>/add-skus
POST /products/inventory-lists/<inventory-list-uuid>/add-skus-by-search

### By Item UUID Request

```json
{
  items: [<uuid>, <uuid>, ...]
}
```

### By SKU UUID Request

```json
{
  skus: [<uuid>, <uuid>, ...]
}
```

### By Search Request

```json
{
  search_term: <string>,
  filters: {
    // See filters object on catalog search request
  },
}
```

### Response

```json
status: 200 level
```