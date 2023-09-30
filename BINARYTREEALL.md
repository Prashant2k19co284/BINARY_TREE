```python
class BinaryTreeNode:
    def __init__(self,data):
        self.data=data
        self.left=None
        self.right=None

```


```python
btn1=BinaryTreeNode(1)
btn2=BinaryTreeNode(2)
btn3=BinaryTreeNode(3)
btn4=BinaryTreeNode(4)
btn5=BinaryTreeNode(5)
btn6=BinaryTreeNode(6)
btn7=BinaryTreeNode(7)
btn1.left=btn2
btn1.right=btn3
btn2.left=btn4
btn2.right=btn5
btn3.left=btn6
btn3.right=btn7
```

# PRINTED TREE


```python
def print_binary_tree(root):
    if root==None:
        return
    print(root.data,end=":")
    if root.left is not None:
        print("L",root.left.data,end=",")
    if root.right is not None:
        print("R",root.right.data,end="")
    print()
    print_binary_tree(root.left)
    print_binary_tree(root.right)
```


```python
print_binary_tree(btn1)
```

    1:L 2,R 3
    2:L 4,R 5
    4:
    5:
    3:L 6,R 7
    6:
    7:
    

# TAKE INPUT RECURSIVELY 


```python
def takeinput():
    rootdata=int(input())
    if rootdata==-1:
        return 
    root=BinaryTreeNode(rootdata)
    lefttree=takeinput()
    righttree=takeinput()
    root.left=lefttree
    root.right=righttree
    return root
    
```


```python
root=takeinput()
print_binary_tree(root)
```

    1
    2
    3
    4
    -1
    -1
    -1
    -1
    -1
    1:L 2,
    2:L 3,
    3:L 4,
    4:
    

# NO OF NODES IN BINARY TREE


```python
def Num_Nodes(root):
    if root==None:
        return 0
    left_node=Num_Nodes(root.left)
    right_node=Num_Nodes(root.right)
    return left_node+right_node+1
```


```python
Num_Nodes(root)
```




    5



# SUM NODES


```python
def sum_nodes(root):
    if root==None:
        return 0
    left_sum=sum_nodes(root.left)
    right_sum=sum_nodes(root.right)
    return root.data+left_sum+right_sum
```


```python
sum_nodes(root)
```




    15



# POSTORDER


```python
def print_post_order(root):
    if root==None:
        return 
    if root.left is not None:
        print("L",root.left.data,end=",")
    if root.right is not None:
        print("R",root.right.data,end=":")
    print(root.data)
    print_post_order(root.left)
    print_post_order(root.right)
```


```python
print_post_order(root)
```

    L 2,R 5:1
    L 3,R 4:2
    3
    4
    5
    

# IN ORDER


```python
def print_in_order(root):
    if root==None:
        return 
    if root.left is not None:
        print("L",root.left.data,end=",")
    print(root.data,end="")
    if root.right is not None:
        print(":R",root.right.data,end="")
    print()
    print_post_order(root.left)
    print_post_order(root.right)
```


```python
print_in_order(root)
```

    L 2,1:R 5
    L 3,R 4:2
    3
    4
    5
    

# NODE WITH LARGEST DATA


```python
def largest_Node(root):
    if root==None:
        return -100000
    left_tree=largest_Node(root.left)
    right_tree=largest_Node(root.right)
    return max(root.data,left_tree,right_tree)
```


```python
largest_Node(root)
```




    5



# NODES GREATOR THAN X


```python
def node_greator(root,x):
    if root==None:
        return 0
    left_tree=node_greator(root.left,x)
    right_tree=node_greator(root.right,x)
    if root.data>x:
        return 1+left_tree+right_tree
    else:
        return left_tree+right_tree
```


```python
node_greator(root,5)
```




    0



# HEIGHT OF A TREE


```python
def height(root):
    if root==None:
        return 0
    left_height=height(root.left)
    right_height=height(root.right)
    h_tree=1+max(left_height,right_height)
    return h_tree
```


```python
height(root)
```




    3



# NO OF LEAF NODES


```python
def No_of_leaf_Nodes(root):
    if root is None:
        return 0
    if root.left is None and root.right is None:
        return 1
    left_tree=No_of_leaf_Nodes(root.left)
    right_tree=No_of_leaf_Nodes(root.right)
    return left_tree+right_tree
    
```


```python
No_of_leaf_Nodes(root)
```




    3



# PRINT LEAF NODE AT K DEPTH


```python
def print_node_depth_k(root,k):
    if root==None:
        return 
    if k==0:
        print(root.data)
        return
    print_node_depth_k(root.left,k-1)
    print_node_depth_k(root.right,k-1)
```


```python
print_node_depth_k(root,2)
```

    3
    4
    

# REPLACE NODE WITH DEPTH K 


```python
def replace_node_at_depth_k(root,k,d=0):
    if root== None:
        return 
    if k>=d:
        root.data=d
    replace_node_at_depth_k(root.left,k,d+1)
    replace_node_at_depth_k(root.right,k,d+1)
```


```python
replace_node_at_depth_k(root,2)
print_binary_tree(root)
```

    0:L 1,R 1
    1:L 2,R 2
    2:
    2:
    1:
    

# NODE WITH DATA K IS PRESENT OR NOT 


```python
def Is_present(root,k):
    if root==None:
        return False
    if root.data==k:
        return True
    return Is_present(root.left,k) or Is_present(root.right,k)
```


```python
Is_present(root,5)
```




    False



# NODES WITHOUT SIBLINGS


```python
def Nodes_without_siblings(root):
    if root==None:
        return 
    if root.left!=None and root.right==None:
        print(root.left.data)
    if root.right!=None and root.left==None:
        print(root.right.data)
    Nodes_without_siblings(root.left)
    Nodes_without_siblings(root.right)
```


```python
root=takeinput()
print_binary_tree(root)
Nodes_without_siblings(root)

```

    1
    2
    4
    -1
    -1
    5
    -1
    -1
    4
    -1
    -1
    1:L 2,R 4
    2:L 4,R 5
    4:
    5:
    4:
    

# Remove Leaf Nodes

def remove(root):
    if root==None:
        return None
    if root.left is None and root.right is None:
        return None
    root.left=remove(root.left)
    root.right=remove(root.right)
    return root


```python
root=takeinput()
root=remove(root)
print_binary_tree(root)
```

    1
    2
    4
    -1
    -1
    5
    -1
    -1
    3
    -1
    -1
    


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[33], line 2
          1 root=takeinput()
    ----> 2 root=remove(root)
          3 print_binary_tree(root)
    

    NameError: name 'remove' is not defined


# MIRROR TREE


```python
def mirror_tree(root):
    if root==None:
        return
    root.left,root.right=mirror_tree(root.right),mirror_tree(root.left)
    return root
```


```python
root=takeinput()
root=mirror_tree(root)
print_binary_tree(root)

```

    1
    2
    4
    -1
    -1
    5
    -1
    -1
    3
    -1
    -1
    1:L 3,R 2
    3:
    2:L 5,R 4
    5:
    4:
    

# TO CHECK A TREE IS BALANCE OR NOT (DIFFERNCE BETWEEN LEFT AND RIGHT SHOULD NOT BE GREATOR THAN 1)


```python
def height_2(root):
    if root==None:
        return 0
    return 1+max(height_2(root.left),height_2(root.right))
```


```python
def balance_or_not(root):
    if root==None:
        return True
    left_height,left_balance=height_2(root.left),balance_or_not(root.left)
    right_height,right_balance=height_2(root.right),balance_or_not(root.right)
    if abs(left_height-right_height)>1:
        return False
    return  left_balance and right_balance
```


```python
root=takeinput()
balance_or_not(root)
```

    1
    2
    4
    -1
    -1
    5
    -1
    -1
    3
    -1
    -1
    




    True



# IMPROVED BALANCE O(N)



```python
def improved_balanced(root):
    if root==None:
        return 0,True
    lh,left_balance=improved_balanced(root.left)
    rh,right_balance=improved_balanced(root.right)
    h=1+max(lh,rh)
    if abs(lh-rh)>1:
        return h,False
    if left_balance and right_balance:
        return h,True
    else:
        return h,False
```

root=takeinput()
print_binary_tree(root)
improved_balanced(root)

# DIAMETER OF BINARY TREE


```python
def diameter_binary_tree(root,a=-1000000):
    if root==None:
        return 0,0
    lh,ld=diameter_binary_tree(root.left,a)
    rh,rd=diameter_binary_tree(root.right,a)
    h=1+max(lh,rh)
    d=lh+rh
    if d>a:
        a=d
        return h,d
    
```


```python
root=takeinput()
print_binary_tree(root)
diameter_binary_tree(root)
```

    1
    2
    4
    -1
    -1
    4
    -1
    -1
    3
    -1
    -1
    1:L 2,R 3
    2:L 4,R 4
    4:
    4:
    3:
    




    (3, 3)



# LEVELWISE INPUT() WE CAN'T USE RECURSION WE SHOULD HAVE TO USE ITERATIVE APPROACH USING QUEUE



```python
import queue
def take_input_levelwise():
    rootdata=int(input())
    if rootdata==-1:
        return None
    root=BinaryTreeNode(rootdata)
    q=queue.Queue()
    q.put(root)
    while not(q.empty()):
        temp=q.get()
        print("Enter the left child of ",temp.data)
        leftchild=int(input())
        if leftchild!=-1:
            left=BinaryTreeNode(leftchild)
            temp.left=left
            q.put(left)
        print("Enter the right child of ",temp.data)
        rightchild=int(input())
        if rightchild!=-1:
            right=BinaryTreeNode(rightchild)
            temp.right=right
            q.put(right)
    return root
        
        
```


```python
root=take_input_levelwise()
print_binary_tree(root)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    4
    Enter the left child of  2
    -1
    Enter the right child of  2
    -1
    Enter the left child of  4
    5
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    5
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    1:L 2,R 4
    2:
    4:L 5,
    5:R 5
    5:
    

# PRINT LEVELWISE BINARY TREE


```python
import queue
def print_level_wise(root):
    q=queue.Queue()
    q.put(root)
    while not(q.empty()):
        temp=q.get()
        print(temp.data,end=":")
        if temp.left is not None:
            print("L",temp.left.data,end=",")
            q.put(temp.left)
        else:
            print("-1",end=",")
        if temp.right is not None:
            print("R",temp.right.data,end="")
            q.put(temp.right)
        else:
            print("-1",end="")
        print()
    return 
```


```python
root=take_input_levelwise()
print_level_wise(root)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    6
    Enter the right child of  3
    7
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    Enter the left child of  6
    -1
    Enter the right child of  6
    -1
    Enter the left child of  7
    -1
    Enter the right child of  7
    -1
    1:L 2,R 3
    2:L 4,R 5
    3:L 6,R 7
    4:-1,-1
    5:-1,-1
    6:-1,-1
    7:-1,-1
    

# BUILD A TREE USING INORDER


```python
def Tree_using_in_and_preorder(preorder,inorder):
    if len(preorder)==0:
        return None
    rootdata=preorder[0]
    root=BinaryTreeNode(rootdata)
    inorderindex=-1
    for i in range(len(inorder)):
        if rootdata==inorder[i]:
            inorderindex=i
            break
    if inorderindex==-1:
        return None
    left_tree=Tree_using_in_and_preorder(preorder[1:inorderindex+1],inorder[:inorderindex])
    right_tree=Tree_using_in_and_preorder(preorder[inorderindex+1:],inorder[inorderindex+1:])
    root.left=left_tree
    root.right=right_tree
    return root
    
```


```python
root=Tree_using_in_and_preorder([4,5,1,2,6,3,9],[1,5,2,4,3,6,9])
print_level_wise(root)
```

    4:L 5,R 6
    5:L 1,R 2
    6:L 3,R 9
    1:-1,-1
    2:-1,-1
    3:-1,-1
    9:-1,-1
    

# CONSTRUCT A TREE USING INORDER AND POST ORDER 


```python
def tree_using_in_and_postorder(postorder,inorder):
    if len(postorder)==0:
        return None
    rootdata=postorder[-1]
    root=BinaryTreeNode(rootdata)
    inorderindex=-1
    for i in range(len(inorder)):
        if rootdata==inorder[i]:
            inorderindex=i
            break
    if inorderindex==-1:
        return None
    root.left=tree_using_in_and_postorder(postorder[:inorderindex],inorder[:inorderindex])
    root.right=tree_using_in_and_postorder(postorder[inorderindex:len(postorder)-1],inorder[inorderindex+1:])
    return root
```


```python
root=tree_using_in_and_postorder([1,2,5,3,9,6,4],[1,5,2,4,3,6,9])
print_level_wise(root)
```

    4:L 5,R 6
    5:L 1,R 2
    6:L 3,R 9
    1:-1,-1
    2:-1,-1
    3:-1,-1
    9:-1,-1
    

# DUPLICATE NODE ATTACH TO ITS LEFT SIDE


```python
def duplicate_attach(root):
    if root==None:
        return None
    newnode=BinaryTreeNode(root.data)
    temp=root.left
    root.left=newnode
    newnode.left=temp
    duplicate_attach(temp)
    duplicate_attach(root.right)
    return root
    
```


```python
root=take_input_levelwise()
root=duplicate_attach(root)
print_level_wise(root)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    6
    Enter the right child of  3
    7
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    Enter the left child of  6
    -1
    Enter the right child of  6
    -1
    Enter the left child of  7
    -1
    Enter the right child of  7
    -1
    1:L 1,R 3
    1:L 2,-1
    3:L 3,R 7
    2:L 2,R 5
    3:L 6,-1
    7:L 7,-1
    2:L 4,-1
    5:L 5,-1
    6:L 6,-1
    7:-1,-1
    4:L 4,-1
    5:-1,-1
    6:-1,-1
    4:-1,-1
    

# MINIMUM AND AMXIMUM DATA VALUE NODE


```python
def min_max(root):
    if root==None:
        return 10000000,-100000000
    lh=min_max(root.left)
    rh=min_max(root.right)
    return min(root.data,lh[0],rh[0]),max(root.data,lh[1],rh[1])
    
    
```


```python
root=take_input_levelwise()
min_max(root)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    6
    Enter the right child of  3
    7
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    Enter the left child of  6
    -1
    Enter the right child of  6
    -1
    Enter the left child of  7
    -1
    Enter the right child of  7
    -1
    




    (1, 7)



# LEVEL ORDER TRANSVERSAL


```python
def level_order_traversal(root):
    q=queue.Queue()
    q.put(root)
    q.put(None)
    print(root.data)
    while not (q.empty()):
        temp=q.get()
        if temp!=None:
            if temp.left is not None:
                print(temp.left.data,end=" ")
                q.put(temp.left)
            if temp.right is not None:
                print(temp.right.data,end=" ")
                q.put(temp.right)
        else:
            print()
            if not(q.empty()):
                q.put(None)
    return 

                
                
```

# root=take_input_levelwise()
level_order_traversal(root)

# PATH SUM TO LEAF 


```python
def path_to_leaf(root,k,s=""):
    if root==None:
        return s 
    s+=str(root.data)+" "
    if k==root.data and root.left==None and root.right==None:
        print(s)
        return s
    path_to_leaf(root.left,k-root.data,s)
    path_to_leaf(root.right,k-root.data,s)
    
    
```


```python
root=take_input_levelwise()
path_to_leaf(root,6)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    6
    Enter the right child of  3
    7
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    Enter the left child of  6
    -1
    Enter the right child of  6
    -
    


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[56], line 1
    ----> 1 root=take_input_levelwise()
          2 path_to_leaf(root,6)
    

    Cell In[42], line 18, in take_input_levelwise()
         16     q.put(left)
         17 print("Enter the right child of ",temp.data)
    ---> 18 rightchild=int(input())
         19 if rightchild!=-1:
         20     right=BinaryTreeNode(rightchild)
    

    ValueError: invalid literal for int() with base 10: '-'


# PRINT NODE AT DISTANCE K FROM A TARGET NODE


```python
def helper(root,node,k):
    if root==None:
        return -1
    if root.data==node:
        print_node(root,k)
        return 0
    ld=helper(root.left,node,k)
    if ld!=-1:
        if ld+1==k:
            print(root.data)
        else:
            print_node(root.right,k-ld-2)
        return 1+ld
    rd=helper(root.right,node,k)
    if rd!=-1:
        if rd+1==k:
            print(root.data)
        else:
            print_node(root.left,k-rd-2)
        return 1+rd
    return -1
    
```


```python
def print_node(root,k):
    if root==None:
        return 
    if k==0:
        print(root.data)
        return 
    print_node(root.left,k-1)
    print_node(root.right,k-1)
```


```python
root=take_input_levelwise()
helper(root,3,2)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    6
    Enter the right child of  3
    7
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    Enter the left child of  6
    -1
    Enter the right child of  6
    -1
    Enter the left child of  7
    -1
    Enter the right child of  7
    -1
    2
    




    1



# BINARY SEARCH TREE

if everything in left is less than and in right is greator than or equal to is known as binary search tree


```python
def search_node(root,ele):
    if root==None:
        return False
    if root.data==ele:
        return True
    elif root.data<ele:
        return search_node(root.right,ele)
    else:
        return search_node(root.left,ele)
```

# root=take_input_levelwise()
search_node(root,20)

# PRINT ELEMENT BTW K1 AND K2


```python
def print_ele(root,k1,k2):
    if root==None:
        return 
    if root.data<k1:
        print_ele(root.right,k1,k2)
    elif root.data>k2:
        print_ele(root.left,k1,k2)
    else:
        print_ele(root.left,k1,k2)
        print(root.data)
        print_ele(root.right,k1,k2)
        
```


```python
root=take_input_levelwise()
print_ele(root,10,15)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    6
    Enter the right child of  3
    7
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    Enter the left child of  6
    -1
    Enter the right child of  6
    -1
    Enter the left child of  7
    -1
    Enter the right child of  7
    -1
    

# SORTED ARRAY TO BST


```python
def array_to_BST(arr):
    if len(arr)==0:
        return
    mid_index=len(arr)//2
    root=BinaryTreeNode(arr[mid_index])
    root.left=array_to_BST(arr[:mid_index])
    root.right=array_to_BST(arr[mid_index+1:])
    return root
```


```python
arr=[int(ele) for ele in input().split()]
root=array_to_BST(arr)
print_level_wise(root)
```

    1 2 3 4 5 6 7 8
    5:L 3,R 7
    3:L 2,R 4
    7:L 6,R 8
    2:L 1,-1
    4:-1,-1
    6:-1,-1
    8:-1,-1
    1:-1,-1
    

# CHECKING IS BST OR NOT 

# TIME COMPLEXITY IS O(N)


```python
#Wrong ans 


def check_BST(root):
    if root==None:
        return True
    if root.left!=None and root.left.data>root.data:
        return False
    if root.right!=None and root.right.data<root.data:
        return False
    return check_BST(root.left) and check_BST(root.right)
```

# RIGHT SOLUTION WITH TIME COMPLEXITY O(nlog(n))


```python
def left_max(root):
    if root==None:
        return -100000
    lm=left_max(root.left)
    rm=left_max(root.right)
    return max(root.data,lm,rm)
```


```python
def right_min(root):
    if root==None:
        return 100000
    lm=right_min(root.left)
    rm=right_min(root.right)
    return min(root.data,lm,rm)
```


```python
def IS_BST(root):
    if root==None:
        return True
    l_max=left_max(root.left)
    R_min=right_min(root.right)
    if root.data<=l_max or root.data>R_min:
        return False
    return IS_BST(root.left) and IS_BST(root.right)
```

# MORE EFFICIENT SOLUTION WITH TIME COMPLEXITY O(n)


```python
def Is_BST_Improved(root):
    if root==None:
        return -100000,100000,True
    left_max,left_min,left_balance=Is_BST_Improved(root.left)
    right_max,right_min,right_balance=Is_BST_Improved(root.right)
    l_max=max(left_max,right_max,root.data)
    r_min=min(left_min,right_min,root.data)
    
    if root.data<=left_max or root.data>right_min:
        return l_max,r_min,False
    result=left_balance and right_balance
    return l_max,r_min,result
```

# ANOTHER SOLUTION FOR BST


```python
def IS_BST_Another(root,min=-1000000,max=1000000):
    if root == None:
        return True
    if root.data<=min or root.data>max:
        return False
    return IS_BST_Another(root.left,min,root.data) and IS_BST_Another(root.right,root.data,max)
        
```


```python
root=take_input_levelwise()
print(check_BST(root))
print(IS_BST(root))
print(Is_BST_Improved(root))
print(IS_BST_Another(root))
```

    10
    Enter the left child of  10
    4
    Enter the right child of  10
    16
    Enter the left child of  4
    2
    Enter the right child of  4
    30
    Enter the left child of  16
    11
    Enter the right child of  16
    19
    Enter the left child of  2
    -1
    Enter the right child of  2
    -1
    Enter the left child of  30
    -1
    Enter the right child of  30
    -1
    Enter the left child of  11
    -1
    Enter the right child of  11
    -1
    Enter the left child of  19
    -1
    Enter the right child of  19
    -1
    True
    False
    (30, 2, False)
    False
    

# ROOT TO NODE PATH IN A LIST


```python
def path_root_to_node(root,node):
    if root==None:
        return None
    if root.data==node:
        l=list()
        l.append(root.data)
        return l
    left=path_root_to_node(root.left,node)
    if left!=None:
        left.append(root.data)
        return left
    right=path_root_to_node(root.right,node)
    if right!=None:
        right.append(root.data)
        return right
    else:
        return None
    
```


```python
root=take_input_levelwise()
path_root_to_node(root,5)
```

    1
    Enter the left child of  1
    2
    Enter the right child of  1
    3
    Enter the left child of  2
    4
    Enter the right child of  2
    5
    Enter the left child of  3
    -1
    Enter the right child of  3
    -1
    Enter the left child of  4
    -1
    Enter the right child of  4
    -1
    Enter the left child of  5
    -1
    Enter the right child of  5
    -1
    




    [5, 2, 1]



# BST CLASS


```python
class BST:
    def __init__(self):
        self.root=None
        self.__numnodes=0
        
        
    def print_tree_helper(self,root):
        if root==None:
            return
        print(root.data,end=":")
        if root.left is not None:
            print("L:"+str(root.left.data),end=",")
        if root.right is not None:
            print("R:",str(root.right.data),end="")
        print()
        self.print_tree_helper(root.left)
        self.print_tree_helper(root.right)
        return 
        
    def print_tree(self):
        self.print_tree_helper(self.root)
    
    def insert_helper(self,root,data):
        if root==None:
            node=BinaryTreeNode(data)
            return node
        if root.data>data:
            root.left=self.insert_helper(root.left,data)
            return root
        else:
            root.right=self.insert_helper(root.right,data)
            return root
        
    def insert(self,data):
        self.root=insert_helper(self.root,data)
        self.nummodes+=1
        retrun
        
    def ispresent_helper(self,root,data):
        if root==None:
            return False
        if data==root.data:
            return True
        elif root.data>data:
            return self.ispresent_helper(root.left)
        else:
            return self.ispresent_helper(root.right)
    
    def ispresent(self,data):
        ispresent_helper(self.root,data)
        return False
    
    def nummodes(self):
        return self.__numnodes
    
    def minimum(self,root):
        if root==None:
            return 100000
        if root.left==None:
            return root.data
        return self.minimum(root.left)
    
    def delete_helper(self,root,data):
        if root==None:
            return False,None
        if root.data>data:
            isdeleted,left=self.delete_helper(root.left,data)
            root.left=left
            return root
        if root.data<data:
            isdelete,right=self.delete_helper(root.right,data)
            root.right=right
            return root
        if root.data==data:
            if root.left is None and root.right is None:
                return True,None
            elif root.left!=None and root.right==none:
                return True,root.left
            elif root.left==None and root.right!=None:
                return True,root.right
            else:
                m=self.minimum(root.right)
                root.data=m
                isdeleted,new=self.delete_helper(root.right,m)
                root.right=new
                return True,root
    
    def delete(self,data):
        deleted,self.root=delete_helper(self.root,data)
        if deleted:
            self.nummodes-=1
            return True
        else:
            return False
    
```


```python

```
