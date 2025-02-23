
ReadMe
Overview
This Tkinter application allows you to create cascading text boxes in a tree-like hierarchy. Each text box represents a node in a double-linked tree—every node references its parent, child, and sibling. The tree is traversed with DFS and BFS to manage layout and operations like adding/removing nodes.

Key Features
Double-linked Tree: Each node (metaBox) has parent, child, and sibling pointers.
Dynamic Layout: Nodes auto-resize, and their positions are recalculated whenever a new node is added or removed.
DFS & BFS: Used in methods like sortButtons (reorganizing layout), countChildren, traverse (pre-order collection for saving), and more.


![image](https://user-images.githubusercontent.com/36753290/170846460-1703f019-fa4b-4351-bf40-a6230a6f68ed.png)

**Note** The updated verseion has been implemented into https://github.com/Parry-Zhuo/DeliberatePracticeTimer

Here is an example code snippet from "selectedButton.py" which uses Depth first search to delete a node.
```python
    def deleteSelf(self):#deletes itself as well as all descendents of self utilizing DFS
        deleteThis = []
        findParent = self
        curr = self
        self.txt.destroy()
        if(self.child is not None):#here we are seeing if it has children so we can delete it and the rest of it's descendents using dfs
            deleteThis.append(self.child)
        self.parent.child = None
        if(self.sibling is not None):#here we replace the link between the parent and the self with either none or it's sibling.
            self.parent.child = self.sibling
        else:		
            self.parent.sibling =None
        while deleteThis:
            curr = deleteThis.pop(0)
            curr.txt.destroy()
            if(curr.child is not None):
                deleteThis.append(curr.child)
            if(curr.sibling is not None):
                deleteThis.append(curr.sibling)
            curr = None # DELETES REFERENCE To child
            sortButtons(head,0,0) #reorganizes GUI to fit the new structure created


