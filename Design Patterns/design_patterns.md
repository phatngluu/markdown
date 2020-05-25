# Known Design Patterns
## Factory
![](/assets/img/2020-05-21-09-41-06.png)
1. The Product declares the interface, which is common to all objects that can be produced by the creator and its subclasses.

2. Concrete Products are different implementations of the product interface.

3. The Creator class declares the factory method that returns new product objects. It’s important that the return type of this method matches the product interface.

    You can declare the factory method as abstract to force all subclasses to implement their own versions of the method. As an alternative, the base factory method can return some default product type.

    Note, despite its name, product creation is not the primary responsibility of the creator. Usually, the creator class already has some core business logic related to products. The factory method helps to decouple this logic from the concrete product classes. Here is an analogy: a large software development company can have a training department for programmers. However, the primary function of the company as a whole is still writing code, not producing programmers.

4. Concrete Creators override the base factory method so it returns a different type of product.

    Note that the factory method doesn’t have to create new instances all the time. It can also return existing objects from a cache, an object pool, or another source.

## Abstract Factory
![](/assets/img/2020-05-21-09-33-46.png)
1. **Abstract Products** declare interfaces for a set of distinct but related products which make up a product family.

2. **Concrete Products** are various implementations of abstract products, grouped by variants. Each abstract product (chair/sofa) must be implemented in all given variants (Victorian/Modern).

3. The **Abstract Factory** interface declares a set of methods for creating each of the abstract products.

4. **Concrete Factories** implement creation methods of the abstract factory. Each concrete factory corresponds to a specific variant of products and creates only those product variants.

5. Although concrete factories instantiate concrete products, signatures of their creation methods must return corresponding abstract products. This way the client code that uses a factory doesn’t get coupled to the specific variant of the product it gets from a factory. The Client can work with any concrete factory/product variant, as long as it communicates with their objects via abstract interfaces.

## Prototype
Khi nào cần prototype? 
- Khi cái giá của việc tạo object nó quá lớn

Prototype được đùng với Factory, Abstract Factory:
- Because the cost of creation is costly -> Use Prototype in this case. 
- Factory stores a set of clone objects, instead of creating, let's clone.

## Singleton
When? 
- If the cost of creating factory is costly, multiple create and destroy is not necessary.
Use with other DS:
- Known Design Patterns
  - Factory
  - Abstract Factory
  - Prototype
  - Singleton

![](/assets/img/2020-05-21-10-05-47.png)