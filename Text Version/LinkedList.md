2.2
===

    public int nthToLast(Node root, int n) {
      Node temp = root;
      Node prev = root;
      int counter = 0;

      while(counter < n - 1) {
        if(temp == null)
          return;
        temp = temp.getNext();
        counter++;
      }

      while(temp.getNext() != null) {
        temp = temp.getNext();
        prev = prev.getNext();
      }
      return prev.getVal();
    }

2.4
===

    public Node addTwoNumbers(Node root1, Node root2) {
      Node temp1 = root1;
      Node temp2 = root2;

      Node result;
      int carry = 0;
      while(temp1 != null && temp2 != null) {
        int sum = temp1.getVal() + temp2.getVal() + carry;
        carry = sum/10;

        Node newNode = new Node(sum%10, null);
        appendNodeToResult(newNode);
        temp1 = temp1.getNext();
        temp2 = temp2.getNext();
      }

      if(temp1 == null) {
        while(temp2 != null) {
          int sum = temp2.getVal() + carry;
          carry = sum/10;

          Node newNode = new Node(sum%10, null);
          appendNodeToResult(newNode);
          temp2 = temp2.getNext();
        }
      }

      if(temp2 == null) {
        while(temp1 != null) {
          int sum = temp1.getVal() + carry;
          carry = sum/10;

          Node newNode = new Node(sum%10, null);
          appendNodeToResult(newNode);
          temp1 = temp1.getNext();
        }
      }

      return result;
    }

    public void appendNodeToResult(Node result, Node newNode) {
      if (result == null)
        result = newNode;
      else {
        Node temp3 = result;
        while(temp3.getNext() != null) {
          temp3 = temp3.getNext();
        }
        temp3.setNext(newNode);
      }
    }

2.5
===

    public Node findStartOfLoop(Node root) {
      Node slow = root;
      Node fast = root;

      while(fast.getNext() != null) {
        slow = slow.getNext();
        fast = fast.getNext().getNext();

        if(slow == fast)
          break;
      }

      slow = head;
      while(slow != fast) {
        slow = slow.getNext();
        fast = fast.getNext();
      }

      return fast;
    }

2.1
===

    public void removeDuplicates(Node root) {
      Set<Integer> hashSet = new HashSet<Integer>();

      Node temp = root;
      Node prev = null;

      while(temp!=null) {
        if(hashSet.contains(temp.getData())
          prev.setNext(temp.getNext());
        else {
          hashSet.put(temp.getData());
          prev = temp;
        }
        temp = temp.getNext();
      }
    }

2.3
===

    public boolean deleteNode(Node curr) {
      if(curr == null || curr.getNext() == null)
        return false;

      curr.setData(curr.getNext().getData());
      curr.setNext(curr.getNext().getNext());
    }


  