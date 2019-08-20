def distanceK(self, root, target, K):
        """
        :type root: TreeNode
        :type target: TreeNode
        :type K: int
        :rtype: List[int]
        """
 
        def convertTreeToGraph(root):
            '''
			***   HELPER FUNCTION  ***
			***   Goal -> loose directionality of tree using DFS  ***
            DFS --> stack --> FILO
            stack --> stores the tuple (node, parent)
            '''
            # build our dict:
            from collections import defaultdict
            d = defaultdict(list)
            stack = [(root, None)] # initially root has no parent
            while stack:
                # pop it
                node, parent = stack.pop()
                # visit it (store in dict)
                if parent != None: # i don't need to store this particular link 
                    d[node.val].append(parent.val)
                    d[parent.val].append(node.val)
                # progress-further down
                if node.right:
                    stack.append((node.right, node))
                if node.left:
                    stack.append((node.left, node))
            # return the adj lst representing the graph
            return d
     
        '''
		*** MAIN FUNCTION ***
		*** Goal -> to find neighbours using BFS ***
        BFS on graph returned from the helper function
        queue -> FIFO -> level counter -> raduis analogy
        '''
        # convert tree into graph (aka loose directionality)
        d = convertTreeToGraph(root)
        # start BFS
        from collections import deque
        q = deque()
        q.append(target.val) # must start with special node (here called target)
        visited = set()
        visited.add(target.val) # target is also a node object
        level = 0
        while q and level < K:
            for i in range(len(q)): # make sure I finish current level before moving on
                # pop it
                node = q.popleft()
                # visit it
                for n in d[node]:
                    if n not in visited:
                        q.append(n)
                        visited.add(n)
                        d[n].remove(node)
                del d[node]
            level += 1
        return list(q)
      
