### URL

PATCH /products/inventory-lists/<inventory-list-uuid>
PATCH /products/catalogs/<catalog-uuid>

### Request

```json
{
  name: <string>,
  description: <string>,
  retailers: [<uuid>,<uuid>], // in the case of sub-catalog
}
```

### Response

```json
status: 200 level
```
