
### Trees  
• Composed of:  
	◦ Nodes, which hold data  
	◦ Edges, which connect nodes  
• Each node has:  
	◦ One parent  
	◦ Zero or more children (or child nodes)  
• Trees have one special node, termed the root.  
	◦ The root node is the only node that has no parent.  
• Tree are typically drawn like an upside-down tree  
	◦ Root is topmost node  
	◦ Children are drawn below parents  
• By definition a tree cannot have a cycle  
	◦ "I’m my own grandpa!"  
Terminology  
	• Use terms from family trees:  
	◦ Parent and child have already been used  
	◦ Siblings are nodes that share a parent  
	◦ The grandparent of a node is its parent’s parent.  
	◦ A grandchild of a node is its child’s child.  
	◦ An ancestors is a parent, grandparent, etc.  
	◦ A descendant is a child, grandchild, etc.  
	◦ Aunts and uncles are siblings of the parent.  
	◦ Etc.  
	• A leaf node has no children.  

• An internal node has at least one child, but isn’t the root. (Depending on the definition you find, the root is sometimes included as an internal node.  
• A path is a sequence of nodes from an ancestor to a descendant.  
	◦ For each step there must be an edge.  
	◦ Often a path will start at the root and conclude at a leaf.  
	◦ The path length is the number of edges on a path.  
• A subtree is defined by a node and is the tree formed by pretending that node is the root of a tree.  
	◦ I.e. it is that node and all of its descendants.  
Attributes  
	• The depth of a node is the length of the path from the root to the node.  
	◦ Recursively:  
	▪ The depth of the root node is 0  
▪ The depth of all other nodes is the parent’s depth plus one.  
	◦ Note: some definitions makes the depth one higher by saying the depth of the root is 1.  
• A tree can be broken into levels. Each level is composed of all nodes with the same depth.  
	◦ I.e. the root is level 0, its children are level 1, etc.  
• The height of a node is the length of the longest path from this node to a leaf plus one.  
	◦ Recursively:  
▪ The height of a leaf is 1  
▪ The height of all other nodes is the maximum of all children’s height plus one.  
	◦ Note: some definitions makes the height one lower by saying the height of a leaf is 0.  
• Height of a Tree  
	◦ The height of a tree is equal to the height of the root node.  
	◦ You can compute height of the tree recursively; we’ll go over this algorithm a little later.  
Tree Classifications  
	• The maximum number of children for any node is the order of the tree.  
	• General trees have no limit to the number of children a node may have  
	• A tree that limits each node to no more than n children is referred to as an n-ary tree.  
	• A tree with order 2 is known as a binary tree.  

### Tree Structures  

• These definitions only apply to trees where the order (number of possible children) of the tree is  
set.  
• A balanced tree has all leaves on the same level or within one level of each other. The order of the  
tree determines when a level is full.  
	◦ I.e. each level is filled before the next level has nodes.  
• A left-complete tree is a balanced tree with the nodes filled left-to-right.  
• Similarly a right-complete tree is a balanced tree with the nodes filled right-to-left.  
• A full tree has all of the nodes filled in at each level.  
	◦ This is only possible for certain sizes.  
	◦ The possible sizes are dependant on the order of the tree.  
Traversals  
• Sometimes we need to "visit" each node once.  
• Visit may be:  
	◦ print node  
	◦ add node’s value to sum  
	◦ etc.  
• To do this, we traverse the tree.  
• All traversals are O(n), since they must visit each node once.  
• Fairly easy in trees since we have no cycles.  
• Two main kinds of traversals:  
	◦ depth-first (easy with recursion using the implied stack)  
	◦ breadth-first (requires a queue)  
• Depth-first can be further broken down into  
	◦ pre-order  
	◦ post-order  
	◦ in-order (only applicable to binary trees, so later)  
• Pre-order Traversal  
	◦ Visit node and then traverse all of the children  
	◦ Give algorithm  
	◦ Demonstrate with sample tree  


• Post-order  
	◦ Traverse all children and then visit the node.  
	◦ Modify above algorithm.  
	◦ Demonstrate with sample tree  
• Breadth-first  
	◦ AKA Level-order  
	◦ Is always done in a pre-order style with the root before its children.  
	◦ Visit all of the nodes on one level, and then move to the next.  
	◦ Start with root.  
	◦ Requires a queue:  
Enqueue the root node of the tree  

	While the queue is not empty  
	{  
	Dequeue node  
	Visit node  
	Enqueue children of node  
	}  

◦ Demonstrate with sample tree  
◦ The same algorithm works for depth-first traversals if a stack is used.  
▪ If you replace the queue with a stack you will get a post-order depth-first traversal.  

▪ If you print before you push on the stack instead of when you pop it off the stack you will get a pre-order depth-first traversal  

▪ Either way to get the children in the same order as above, you have to push them on the  
stack in reverse, i.e. if you push them on right-to-left, they will print left-to-right.  
