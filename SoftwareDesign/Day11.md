Problem Description:

Traverse a structure/tree with:

- Depth First
- Breadth First
- Inorder
- Postorder

Solution: use **Iterator** pattern

What is iterator?

Iterator helps us traverse a complex structure easiser in specific traverse rule.



```java
tournament : Tournament
// get iterator
iterator = tournament.getIterator("depthfirst") 

// client code - it does not change
// because it is independent on which kind of iterator (depth first or breadth first)
while (iterator.hasNext()){
	currentTournament = iterator.next()
}
```



Tournament With Iterator Class

```
public Iterator getIterator(String type){
	Iterator = null
	switch (type){
		case : {
			Iterator = new DepthFirstIterator(Tournament)
			return iter
		}
		case ....
	}
}
public class DepthFirstIterator(Tournament) extends {
	@Override
	method next(){
		...
	}
	@Override
	method hasNext(){
		...
	}
}
```

Iterator:

Advantages

Usage: 

- when need to traverse to a complex structure (not a simple collection)

- when need to decide where to go in a branch