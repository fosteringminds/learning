# Aggregate Root

It is important to understand an aggregate root as it is used in the [eShopOnContainers repository](https://github.com/dotnet-architecture/eShopOnContainers). Martin Fowler uses an [example](https://martinfowler.com/bliki/DDD_Aggregate.html) of an order consisting of order items to illustrate an aggregate. An aggregate is a cluster of domain objects. The cluster of domain objects can be treated as a single unit. The order acts as the aggregate root. What does this mean? It means when you are adding items to an order you add it to the order. Imagine having an Entity Framework context with two entities - an Order and an Order Item. The order will be the aggregate root - a single point of access to all your domain objects. Retrieving an order will also retrieve a list of order items. It suggests not retrieving order items or performing operations on them. Instead when you perform a single transaction you will treat the order with its order items as a single collection or single aggregate. 

> Aggregate is a pattern in Domain-Driven Design. A DDD aggregate is a cluster of domain objects that can be treated as a single unit. An example may be an order and its line-items, these will be separate objects, but it's useful to treat the order (together with its line items) as a single aggregate.

> An aggregate will have one of its component objects be the aggregate root. Any references from outside the aggregate should only go to the aggregate root. The root can thus ensure the integrity of the aggregate as a whole.

It suggests only having a repository for the aggregate root - not every entity.

> Aggregates are the basic element of transfer of data storage - you request to load or save whole aggregates. Transactions should not cross aggregate boundaries.

> DDD Aggregates are sometimes confused with collection classes (lists, maps, etc). DDD aggregates are domain concepts (order, clinic visit, playlist), while collections are generic. An aggregate will often contain mutliple collections, together with simple fields. The term "aggregate" is a common one, and is used in various different contexts (e.g. UML), in which case it does not refer to the same concept as a DDD aggregate.

