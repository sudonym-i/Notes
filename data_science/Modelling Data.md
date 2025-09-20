
## Entities

In data science, an **entity** represents a distinct, real-world object or concept that we want to store information about. Think of entities as the "nouns" in your data. Each entity has a unique identity and can be differentiated from other entities.

**Key Characteristics:**

- **Real-world Object/Concept:** Entities correspond to things that exist or are conceptualized, such as a person, a product, an event, a location, or an organization.
- **Distinguishable:** Each instance of an entity can be uniquely identified. For example, two different customers are distinct entities.
- **Has Attributes:** Entities possess characteristics or properties that describe them. These are called attributes.

**Examples:**

- **Customer:** A specific individual who purchases products.
- **Product:** An item sold by a company.
- **Order:** A record of a customer's purchase.
- **Employee:** A person working for an organization.
- **Movie:** A film title.

---

## Relationships

A **relationship** describes how two or more entities are connected or associated with each other. Relationships define the interactions and dependencies between different entities in a dataset. They are crucial for understanding the structure and meaning of your data.

**Key Characteristics:**

- **Connects Entities:** Relationships always link at least two entities.
- *Always Bi-directional*
- **Describes Interaction:** They explain how entities relate to one another (e.g., "a customer places an order," "an employee works in a department").
- **Cardinality:** Relationships often have cardinality, which specifies how many instances of one entity can be associated with how many instances of another entity. Common cardinalities include:
    - **One-to-One (1:1):** One instance of Entity A relates to one instance of Entity B. (e.g., A person has one passport).
    - **One-to-Many (1:N):** One instance of Entity A relates to multiple instances of Entity B. (e.g., A customer can place many orders).
    - **Many-to-Many (N:M):** Multiple instances of Entity A relate to multiple instances of Entity B. (e.g., Many students can enroll in many courses).
- **Visual representation 
	- -> First symbol represents mandatory/optional ( | / 0)
	- -> Second symbol represents one/many (| / ~~<~~)

**Examples:**

- **`places`:** A `Customer` `places` an `Order`. (One-to-Many)
- **`contains`:** An `Order` `contains` `Products`. (Many-to-Many, often resolved with an intermediate entity like `Order_Item`)
- **`works_for`:** An `Employee` `works_for` a `Department`. (Many-to-One, if an employee works for only one department)
- **`directed_by`:** A `Movie` is `directed_by` a `Director`. (Many-to-One)

---

## Attributes

**Attributes** are the specific characteristics or properties that describe an entity. They provide the details and data points that make up an entity. Think of attributes as the "adjectives" that describe the "nouns" (entities). (also FIELD)

**Key Characteristics:**

- **Describes an Entity:** Each attribute provides a piece of information about a particular entity.
- **Data Values:** Attributes hold specific data values (e.g., a customer's name, a product's price, an order's date).
- **Data Types:** Attributes have data types (e.g., text, number, date, boolean) that define the kind of values they can store.
- **Primary Key:** A special type of attribute (or set of attributes) that uniquely identifies each instance of an entity.

**Examples:**

For the `Customer` entity:

- `CustomerID` (Primary Key)
- `FirstName`
- `LastName`
- `Email`
- `PhoneNumber`
- `Address`

For the `Product` entity:

- `ProductID` (Primary Key)
- `ProductName`
- `Price`
- `Category`
- `StockQuantity`

For the `Order` entity:

- `OrderID` (Primary Key)
- `OrderDate`
- `TotalAmount`
- `ShippingAddress`
- `Status`

### Business Rules Cont.
- *Nouns* turn into entities
- *Verbs* turn into relationships
