4.3
===

    public Node createTreeFromSortedArray(int[] input) {
      return addNode(input, 0, input.length -1);
    }

    public Node addNode(int[] input, int start, int end) {
      if(end<start)
        return null;

      int mid = (start+end)/2;
      Node node = new Node(arr[mid], null, null);
      node.setLeft(addNode(input, start, mid));
      node.setRight(addNode(input, mid+1, end));
      return node;
    }

4.1
===

    public boolean isTreeBalanced(Node root) {
      return (maxDepth(root) - minDepth(root)) > 1
    }

    public int maxDepth(Node root) {
      if (root==null)
        return 0;
      else {
        lDepth = maxDepth(root.getLeft());
        rDepth = maxDepth(root.getRight());
        return max(lDepth, rDepth) + 1;
      }
    }
    
    public int minDepth(Node root) {
      if root(==null)
        return 0;
      else {
        lDepth = minDepth(root.getLeft());
        rDepth = minDepth(root.getRight());
        return min(lDepth, rDepth) + 1;
      }
    }

4.2
===

    public boolean isConnected(Node node, Node target) {        
      if(node == target)
        return true;
      else {
        while(node.getChildren() != null) {
          for(Node child : node.getChildren()) {
            isConnected(child, target);
          }
        }
        return false;
      }
    }



4.6
===

    public Node commonAncestor(Node root, Node n1, Node n2) {
      if(root == null)
        return null;
      if(isChild(root.getLeft(), n1) && isChild(root.getLeft(), n2))
        return commonAncestor(root.getLeft(), n1, n2);
      else if(isChild(root.getRight(), n1) && isChild(root.getRight(), n2))
        return commonAncestor(root.getRight(), n1, n2);
      else
        return root;
    }

    public boolean isChild(Node root, Node temp) {
      if(root == null)
        return false;
      if(root == temp)
        return true;

      return(isChild(root.getLeft(), temp) || isChild(root.getRight(), temp));
    }

4.5
===

    public Node inorderSuccesor(Node input) {
      if(input == null)
        return null;

      if(input.getRight() != null) {
        return getLeftChild(input.getRight());
      }
      else {
        while(input.parent() != null) {
          if(input.parent().getLeft() == input)
            break;
          input = input.parent();
        }
        return input.parent();
    }

    public Node getLeftChild(Node node) {
      if(node == null)
        return null;
      while(node.getLeft() != null) {
        node = node.getLeft();
      }
      return node;
    }

4.4
===

Method 1
--------

    public void linkedListBetweenLevel(Node root) {
      LinkedList<Node> list = new LinkedList<Node>();
      ArrayList<LinkedList<Node>> arrayList = new ArrayList<LinlkedList<Node>>();
      int level = 0;
      list.add(root);
      arrayList.add(level, list);

      while(true) {
        levelList<Node> = new LinkedList<Node>();
        for(int i=0;i<arrayList.get(level).size();i++) {
          Node n = arrayList.get(level).get(i);
          if(n != null) {
            if(n.getLeft() != null)
              list.add(linkedListBetweenLevel(n.getLeft()));
            if(n.getRight() != null)
              list.add(linkedListBetweenLevel(n.getRight()));
          }
        }
        if(list.size() >0)
          arrayList.add(level+1,list);
        else
          break;
        level++;
      }
    return result;
  }


Method 2
--------

    public void linkedListBetweenLevel(Node root) {
      Queue<Node> q = new LinkedList<Node>();
      List<List<Node>> arrayList = new ArrayList<List<Node>>();
      List<Node> list = new ArrayList<Node>();
      Map<Node, Integer> distanceMap = new HashMap<Node, Integer>();

      q.add(root);
      list.add(root);
      arrayList.add(0, list);
      distanceMap.put(root, 0);

      while(!q.isEmpty()) {
        Node node = q.dequeue();
        List<Node> children = node.getChildren();
        int currDistance = distanceMap.get(node);
        for(Node child : children) {
            q.enqueue(child);
            distanceMap.put(child, currDistance +1);
            if(arrayList.get(currDistance+1) != null)
              arrayList.get(currDistance+1).add(child);
            else
              arrayList.add(new ArrayList<Node<>(child));
        }
      }
      return arrayList;
    }



