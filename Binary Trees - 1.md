# CREATING THE BINARY TREE


```python
class BinaryTreeNode:
    def __init__(self,data):
        self.data=data
        self.left=None
        self.right=None
```

# printing all nodes of binary tree using recursion 


```python
def printbinarytreenodes(root):
    if root==None:
        return 
    print(root.data)
    printbinarytreenodes(root.left)
    printbinarytreenodes(root.right)
    
```

# printing all nodes with details of binary tree using recursion


```python
def printbinarydetailed(root):
    if root==None:
        return 
    print(root.data,end="")
    if root.left is not None:
        print(":l",root.left.data,end=",")
    if root.right is not None:
        print("R",root.right.data,end="")
    print()
    printbinarydetailed(root.left)
    printbinarydetailed(root.right)
```


```python
btn1=BinaryTreeNode(1)
btn2=BinaryTreeNode(4)
btn3=BinaryTreeNode(5)
btn1.left=btn2
btn1.right=btn3
```


```python
printbinarytreenodes(btn1)
```


```python
printbinarydetailed(btn1)
```

# Taking input Recursively


```python
def input_tree():
    root_data=int(input())
    if root_data==-1:
        return None
    root=BinaryTreeNode(root_data)
    left_tree=input_tree()
    right_tree=input_tree()
    root.left=left_tree
    root.right=right_tree
    return root
```


```python
root=input_tree()
printbinarydetailed(root)
```

# CREATING A TREE AND TAKING INPUT AND PRINTING


```python
class Binarytree():
    def __init__(self,data):
        self.data=data
        self.left=None
        self.right=None
        
```


```python
def takeinput():
    root_data=int(input())
    if root_data==-1:
        return None
    root=Binarytree(root_data)
    left_tree=takeinput()
    right_tree=takeinput()
    root.left=left_tree
    root.right=right_tree
    return root
```


```python
def print_tree(root):
    if root==None:
        return 
    print(root.data,end=":")
    if root.left is not None:
        print("L:",root.left.data,end=",")
    if root.right is not None:
        print("R:",root.right.data,end="")
    print()
    print_tree(root.left)
    print_tree(root.right)
    
    
```


```python
root=takeinput()
print_tree(root)
```

# remove leaf NODES


```python
def remove(root):
    if root==None:
        return None
    if root.left==None and root.right==None:
        return None
    root.left=remove(root.left)
    root.right=remove(root.right)
```


```python
root=input_tree()
remove(root)
```


```python
print_tree(root)
```


```python

```
