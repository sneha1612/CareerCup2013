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
      else
        while(node.getChildren() != null) {
          for(Node child : node.getChildren()) {
            isConnected(child, target);
          }
        }
    }



4.6
===

    public Node commonAncestor(Node root, Node n1, Node n2) {
      if(root == null)
        return;
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