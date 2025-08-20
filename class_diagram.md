
---

#  `class_diagram.md` (UML diagram)

```markdown
# Class Diagram – Internal Catalog Tool

```mermaid
classDiagram
    class Category {
        +int id
        +string name
        +__str__()
    }

    class Attribute {
        +int id
        +string name
        +Category category
        +__str__()
    }

    class Product {
        +int id
        +string name
        +Category category
        +__str__()
    }

    class ProductAttributeValue {
        +int id
        +string value
        +Product product
        +Attribute attribute
        +__str__()
    }

    Category "1" --> "*" Attribute : defines
    Category "1" --> "*" Product : contains
    Product "1" --> "*" ProductAttributeValue : has
    Attribute "1" --> "*" ProductAttributeValue : describes
