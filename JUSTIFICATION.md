
---

#  `JUSTIFICATION.md` (short design rationale)

```markdown
# Design Justification

## Goals
- Support **dynamic categories** (dresses now; watches/smartphones later).
- Allow **custom attributes per category** (e.g., RAM for phones, Dial Size for watches).
- Keep the model **normalized, scalable, and maintainable**.

## Why this schema?
- **Category** defines a product family.
- **Attribute** belongs to a Category, so each category can have its own fields (e.g., `OS`, `RAM` for Smartphones; `Dial Size` for Watches) without changing the database schema.
- **Product** links to one Category.
- **ProductAttributeValue** stores the actual value of each Attribute for a specific Product.

This is a classic **EAV (Entity–Attribute–Value)** pattern: highly flexible, no schema migrations required when new categories/attributes are introduced.

## Normalization & Integrity
- Foreign keys maintain referential integrity.
- Cardinalities:
  - Category 1—* Attribute
  - Category 1—* Product
  - Product 1—* ProductAttributeValue
  - Attribute 1—* ProductAttributeValue
- (Optional enhancement) Add uniqueness:
  - Unique `(category_id, name)` on Attribute to avoid duplicates.
  - Unique `(product_id, attribute_id)` on ProductAttributeValue so each product has at most one value per attribute.

## Future-Proofing
- Adding a new category or attribute is **data-only** (no code/db schema change).
- Optional next steps:
  - Add `datatype` on Attribute (text/number/boolean/option).
  - Add `AttributeOption` for dropdown values (e.g., OS: Android/iOS).
