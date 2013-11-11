1.1
===

O(n) - Using External Hash
--------------------------

    public boolean hasUniqueChars(String input) {
      Set<Character> charSet = new HashSet<Character>();
      char[] charArray = input.toCharArray();

      for(char c : charArray) {
        if(charSet.contains(c))
          return false;
        else
          charSet.add(c);
      }
      return true;
    }

O(n^2)
------

    public boolean hasUniqueChars(String input) {
      char[] charArray = input.toCharArray();

      for(int i=0;i<input.length-1;i++) {
        for(iny j=i+1;j<input.length;j++) {
          if(charArr[i] == charArr[j)
            return false;
        }
      }
      return true;
    }

O(n) - Using Bit Masks
----------------------

    public boolean hasUniqueCharsBit(String input) {
      char[] charArray = input.toCharArray();
      int temp = 0;

      for(char c : charArray) {
        int index = c - 'a';

        if (temp & (1 << index) > 0)
          return false;
        temp |= (1 << index);
      }
      return true;
    }

1.2
===

O(n) - In Place
---------------

    public char[] reverseInPlace(char[] charArray) {
      for(int i=0,j=charArray.length-1; i<=j; i++, j--) {
        char temp = charArray[i];
        charArray[i] = charArray[j];
        charArray[j] = temp;
      }
      return charArray;
    }

O(n) - New String
-----------------

    public String reverse(String input) {
      StringBuilder ret = new StringBuilder();
  
      for(int i=input.length-1; i>=0; i--) {
        ret.append(input.charAt(i));
      }
      return ret.toString();
    }

1.3
===

O(n^2) - In Place - No External Data Structures
-----------------------------------------------

    public String removeDuplicateCharacters(String input) {
      char[] charArray = input.toCharArray();
      int counter = 0;
      for(int i = 0; i < input.length; i++) {
        if(isDuplicate(input, i)) {
          for(int j=i; j<input.length-counter-1; j++) {
            charArr[j] = charArr[j+1];
          }
          counter++;
        }
      }
    }

    public boolean isDuplicate(String input, int index) {
      char[] charArray = input.toCharArray();
      int temp = 0;
      for(int i = 0; i < input.length; i++) {
        if (i != index) {
          temp = temp | (1 << charArray[i] - 'a')
        }
      }

      if(temp & (1<< charArray[index] - 'a'))
        return true;
      else
        return false;
    }

1.4
===

O(n) - Anagrams
---------------

    public boolean isAnagram(String str1, String str2) {
      Map<Character> hMap1 = new HashMap<Character>();
      Map<Character> hMap2 = new HashMap<Character>();

      if(str1.length != str2.length)
        return false;

      for(int i = 0; i<str1.length; i++) {
        if(hMap1.contains(str1.charAt(i)))
          hMap1.put(str1.charAt(i), hMap1.get(str1.charAt(i)) + 1);
        else
          hMap1.put(str1.charAt(i), 1);
      }

      for(int i = 0; i<str2.length; i++) {
        if(hMap2.contains(str2.charAt(i)))
          hMap2.put(str2.charAt(i), hMap2.get(str2.charAt(i)) + 1);
        else
          hMap2.put(str2.charAt(i), 1);
      }

      for(int i=0; i<str1.length; i++) {
        if(hMap1.get(str1.charAt(i)) != hMap2.get(str1.charAt(i)))
          return false;
      }

      return true;
    }

1.5
===

O(n) - Replace spaces
---------------------

    public String relaceSpaces(String input) {
      StringBuilder result = new StringBuilder();

      for(int i=0; i<input.length; i++) {
        if(input.charAt(i) == ' ')
          result.append("%20");
        else
          result.append(input.charAt(i));
      }

      return result.toString();
    }

1.7
===

O(n^2)
------

    public int[][] setMatrixRowColumnToZero(int[][] input) {
      int[] row = new int[input.length];
      int[] column = new int[input[0].lenght];

      for(int i = 0; i<input.length; i++) {
        for(int j = 0; j<input.length; j++) {
          if(input[i][j] == 0) {
            row[i] = 1;
            column[j] = 1;
          }
        }
      }

      for(int i=0; i< input.length; i++) {
        for(int j=0; j< input.length; j++) {
          if(row[i] == 1 || column[j] == 1) {
            input[i][j] = 0;
          }
        }
      }

      return input;
    }

1.8
===

O(n^2)
------

    public boolean isRotation(String str1, String str2) {
      if(str1.length != str2.length)
        return false;

      String concatString = str1 + str1;
      return isSubstring(str2, concatString);
    }


    public boolean isSubstring(String needle, String haystack) {
      int haystackLength = haystack.length;
      int needleLength = needle.length;

      if(haystackLength < needleLength)
        return false;

      for(int i=0; i< haystackLength; i++) {
        if (i + needleLength > haystackLenght)
          return false;

        for(int j=0, int k=i; j < needleLength; j++, k++) {
          if(needle[j] != haystack[k]) {
            break;
          }
        }
      }

      if(j == needleLength)
        return true;
      else
        return false;
    }

