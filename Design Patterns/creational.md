# Known Design Patterns
## Factory
![](/assets/img/2020-05-26-00-03-28.png)
1. The Product declares the interface, which is common to all objects that can be produced by the creator and its subclasses.

2. Concrete Products are different implementations of the product interface.

3. The Creator class declares the factory method that returns new product objects. It’s important that the return type of this method matches the product interface.

    You can declare the factory method as abstract to force all subclasses to implement their own versions of the method. As an alternative, the base factory method can return some default product type.

    Note, despite its name, product creation is not the primary responsibility of the creator. Usually, the creator class already has some core business logic related to products. The factory method helps to decouple this logic from the concrete product classes. Here is an analogy: a large software development company can have a training department for programmers. However, the primary function of the company as a whole is still writing code, not producing programmers.

4. Concrete Creators override the base factory method so it returns a different type of product.

    Note that the factory method doesn’t have to create new instances all the time. It can also return existing objects from a cache, an object pool, or another source.

## Abstract Factory
![](/assets/img/2020-05-26-00-03-49.png)
1. **Abstract Products** declare interfaces for a set of distinct but related products which make up a product family.

2. **Concrete Products** are various implementations of abstract products, grouped by variants. Each abstract product (chair/sofa) must be implemented in all given variants (Victorian/Modern).

3. The **Abstract Factory** interface declares a set of methods for creating each of the abstract products.

4. **Concrete Factories** implement creation methods of the abstract factory. Each concrete factory corresponds to a specific variant of products and creates only those product variants.

5. Although concrete factories instantiate concrete products, signatures of their creation methods must return corresponding abstract products. This way the client code that uses a factory doesn’t get coupled to the specific variant of the product it gets from a factory. The Client can work with any concrete factory/product variant, as long as it communicates with their objects via abstract interfaces.

## Builder
![](/assets/img/2020-05-26-00-06-12.png)
1. The **Builder** interface declares product construction steps that are common to all types of builders.

2. **Concrete Builders** provide different implementations of the construction steps. Concrete builders may produce products that don’t follow the common interface.

3. **Products** are resulting objects. Products constructed by different builders don’t have to belong to the same class hierarchy or interface.

4. The **Director** class defines the order in which to call construction steps, so you can create and reuse specific configurations of products.

5. The **Client** must associate one of the builder objects with the director. Usually, it’s done just once, via parameters of the director’s constructor. Then the director uses that builder object for all further construction. However, there’s an alternative approach for when the client passes the builder object to the production method of the director. In this case, you can use a different builder each time you produce something with the director.

## Prototype
Khi nào cần prototype? 
- Khi cái giá của việc tạo object nó quá lớn

Prototype được đùng với Factory, Abstract Factory:
- Because the cost of creation is costly -> Use Prototype in this case. 
- Factory stores a set of clone objects, instead of creating, let's clone.

![](/assets/img/2020-05-26-00-05-06.png)
1. The **Prototype** interface declares the cloning methods. In most cases, it’s a single `clone` method.

2. The **Concrete Prototype** class implements the cloning method. In addition to copying the original object’s data to the clone, this method may also handle some edge cases of the cloning process related to cloning linked objects, untangling recursive dependencies, etc.

3. The **Client** can produce a copy of any object that follows the prototype interface.


## Singleton
When? 
- If the cost of creating factory is costly, multiple create and destroy is not necessary.
Use with other DS:
- Known Design Patterns
  - Factory
  - Abstract Factory
  - Builder
  - Prototype
  - Singleton

![](/assets/img/2020-05-26-00-04-17.png)