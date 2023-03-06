# Rotations
## Left rotation (x)
```
    |               |
    x               y
   / \       ->    / \
 xl   y           x  yr
     / \         / \  
    yl  yr      xl yl
```
```
1. If y has a left subtree yl
	then assign x.right -> yl
2. If parent of x is None (x is root)
	then set y as root
   Else
   	Set y as the child of x's parent
    (left or right child depends on x was left or right)
3. Make y.left -> x
```

## Right rotation (x)
```
    |           |
    x           y
   / \         / \
  y  xr   ->  yl  x
 / \             / \
yl yr           yr xr
```
```
1. If y has a right subtree yr
	then assign x.left -> yr
2. If parent of x is None (x is root)
	then set y as root
   Else
   	Set y as the child of x's parent
	(left or right child depends on x was left or right)
   (Same as left rotation)	
3. Make y.right -> x
```

## Left-right Rotation
```
      z                  z                   y
     / \                / \                /   \
    x  zr    LR(x)     y   zr  RR(y)      x     z
   / \        -->     / \       -->      / \   / \
  xl  y              x   yr             xl yl yr zr
  	 / \            / \
  	yl yr  	       xl yl
```
## Right-left Rotation
```
      z                  z                   y
     / \                / \                /   \
    zl  x    RR(x)     zl  y    LR(z)     z     x
       / \   -->          / \    -->     / \   / \
      y  xr              yl  x          zl yl yr xr
     / \                    / \
   yl  yr                  yr xr
```


# Insertion
```
If tree is Empty:
	Insert the newNode as Root node with color Black 
	and exit from the operation.

Else:
	Insert the newNode as leaf node with color RED.

	If the parent of newNode is Black:
		Exit from the operation.

	If the parent of newNode is Red 
		fixViolation()
```
## How to fixViolation()
```
	 grandParent(gp)
	   /	     \
	uncle	  parent(p)
		         |
	          NewNode(m)
```
```
IF parent p of NewNode is Red:
	CASE Uncle is red:
		Recolour(p), Recolour(gp), Recolour(uncle)
		Continue fix if voilation moves above
	CASE Uncle is black or None:
		IF "triangle":
			rotate(NewNode.p) *opposite* direction (of NewNode's branch)
			fixViolation(NewNode.child) # NewNode.child after rotation
		ELIF "line":
			rotate(NewNode.gp) *opposite* direction
			Recolour(p), Reclour(gp), Recolour(uncle)
```

"Line" means:
```
    gp(B)                gp(B)
    /   \               /     \
  p(R) u(B/None)    u(B/None) p(R)
  /                             \
 new(R)	                       new(R)
```
"Triangle" means:
```
    gp(B)                  gp(B)
   /     \                /      \
p(R)   u(B/None)     u(B/None)  p(R)
   \                             /
  new(R)                      new(R)
```

- where recolour means flip colour
- also the focus NewNode not necessarily NewNode, but any node in the three tha violated a rule











