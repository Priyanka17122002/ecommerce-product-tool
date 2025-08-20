classDiagram
    class Product {
      +int id
      +string name
      +int category_id
    }

    class Attribute {
      +int id
      +string name
      +int category_id
    }

    class ProductAttributeValue {
      +int id
      +string value
      +int product_id
      +int attribute_id
    }

    Product "1" --> "*" ProductAttributeValue : has
    Attribute "1" --> "*" ProductAttributeValue : describes
