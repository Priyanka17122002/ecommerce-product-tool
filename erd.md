# ERD – Internal Catalog Tool

## Entities

### CATEGORY
- **id** (PK)
- name

### ATTRIBUTE
- **id** (PK)
- name
- category_id (FK → CATEGORY.id)

### PRODUCT
- **id** (PK)
- name
- category_id (FK → CATEGORY.id)

### PRODUCT_ATTRIBUTE_VALUE
- **id** (PK)
- value
- product_id (FK → PRODUCT.id)
- attribute_id (FK → ATTRIBUTE.id)

---

## Relationships
- CATEGORY `1 -- *` ATTRIBUTE : defines
- CATEGORY `1 -- *` PRODUCT : contains
- PRODUCT `1 -- *` PRODUCT_ATTRIBUTE_VALUE : has
- ATTRIBUTE `1 -- *` PRODUCT_ATTRIBUTE_VALUE : describes

---

## ERD Diagram (Mermaid)

```mermaid
erDiagram
    CATEGORY {
        int id PK
        string name
    }

    ATTRIBUTE {
        int id PK
        string name
        int category_id FK
    }

    PRODUCT {
        int id PK
        string name
        int category_id FK
    }

    PRODUCT_ATTRIBUTE_VALUE {
        int id PK
        string value
        int product_id FK
        int attribute_id FK
    }

    CATEGORY ||--o{ ATTRIBUTE : defines
    CATEGORY ||--o{ PRODUCT : contains
    PRODUCT ||--o{ PRODUCT_ATTRIBUTE_VALUE : has
    ATTRIBUTE ||--o{ PRODUCT_ATTRIBUTE_VALUE : describes
