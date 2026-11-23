# Database Normalization Assignment (1NF & 2NF)

## Question 1: First Normal Form (1NF)
To satisfy **1NF**, multi-valued entries in the `Products` column were split so every column contains atomic values and each row represents one product per order, using a composite primary key `(OrderID, Product)`.

### Resulting `ProductDetail_1NF` Table
| OrderID | CustomerName | Product |
| :--- | :--- | :--- |
| 101 | John Doe | Laptop |
| 101 | John Doe | Mouse |
| 102 | Jane Smith | Tablet |
| 102 | Jane Smith | Keyboard |
| 102 | Jane Smith | Mouse |
| 103 | Emily Clark | Phone |

---

## Question 2: Second Normal Form (2NF)

### Partial Dependency Identification
In `OrderDetails` with composite primary key `(OrderID, Product)`:
- `Quantity` depends on the full composite key `(OrderID, Product)`.
- `CustomerName` depends only on `OrderID` (part of the composite key), which is a **partial dependency**.

### Resulting 2NF Tables
- **`Orders`**: Stores `OrderID` (Primary Key) and `CustomerName`.
- **`OrderItems`**: Stores `OrderID` (part of composite Primary Key and Foreign Key referencing `Orders(OrderID)`), `Product` (part of composite Primary Key), and `Quantity`.
