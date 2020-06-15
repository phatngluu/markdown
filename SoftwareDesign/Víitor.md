Applicability:

**when you need to perform an operation on all elements of a complex object structure (for example, an object tree).**

CompoundShape.accept(): means that: "Hey visitor, come here and visit me"

```
accept(Visitor visitor){
	visitor.visit(this)
}
```

## SingleBadmintonTournamentVisitor

```
visit(SingpleBadmintonTournament visitable){
	// visitable can be: composite or a leaf
	// increase level
	left.accept(this)
	right.accept(this)
	// decrease level
}
```

# Exercise 2 - Visit with Level

`SingleBadmintonTournament_Visitor` is  a concrete class of `Visitor` contains an attribute `level : Integer`. In particular:

```
class SingleBadmintonTournament_Visitor
	int level
  method visit(SingleBadmintonTournament tournament){
    // print tournament with current level
    
    // increase level when visit it children
    this.level++
    
    // visit the children
    visitable.left.accept(this) // "this" is current visitor, accepted by tournament
    visitable.right.accept(this)
    
    // decrease level when end visitting children
    this.level--
  }
```

**Note**: We pass parent's visitor for the children => Parent's visitor = children's visitor.

![image-20200611120141624](Vi%CC%81itor.assets/image-20200611120141624.png)

