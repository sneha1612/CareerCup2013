1.1
===

O(n) - Using External Hash
--------------------------

  public boolean hasUniqueChars(String input) {
    Set<Character> charSet = new HashSet<Character>();
    char[] charArray = input.toCharArray();

    for(char c : charArray) {
      if(charSet.contains(c))
        return true;
      else
        charSet.add(c);
    }
    return false;
  }

O(n^2)
------

  public boolean hasUniqueChars(String input) {
    char[] charArray = input.toCharArray();

    for(int i=0;i<input.length-1;i++) {
      for(iny j=i+1;j<input.length;j++) {
        if(charArr[i] == charArr[j)
          return true;
      }
    }
    return false;
  }

O(n) - Using Bit Masks
----------------------

  public boolean hasUniqueCharsBit(String input) {
    char[] charArray = input.toCharArray();
    int temp = 0;

    for(char c : charArray) {
      int index = c - 'a';

      if (temp & (1 << index) == 1)
        return true;
      temp |= (1 << index);
    }
    return false;
  }