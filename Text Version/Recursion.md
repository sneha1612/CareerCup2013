8.1
===

Recursive
---------

    public int nthFibonacci(int n) {
      if(n==1 || n ==2)
        return 1;
      else
        return nthFibonacci(n-1) + nthFibonacci(n-2);
    }

Iterative
---------

    public int nthFibonacci(int n) {
      int i = 1;
      int j =1;
      int counter = 3;
      while(counter<=n) {
        int p = i + j;
        i = j;
        j = p;
        counter++;
      }
      return j;
    }

8.2
===

    public int getPaths(int n, int x, int y) {
      if((x == n-1) || (y==n-1)) 
        return 1;

      return getPaths(n, x, y+1) + getPaths(n, x+1, y);
    }

8.3
===

    public ArrayList<ArrayList<Integer>> findSubsets(ArrayList<Integer> inputSet, int index) {
      ArrayList<ArrayList<Integer>> finalSubsets = new ArrayList<ArrayList<Integer>>();

      if(index == inputSet.size()) {
        finalSubsets.add(new ArrayList<Integer>());
      }
      else {
        finalSubsets = getSubsets(inputSet, index + 1);
        ArrayList<ArrayList<Integer>> tempSubsets = new ArrayList<ArrayList<Integer>>();
        for(ArrayList<Integer> subSet : finalSubsets) {
          newSubset = subSet;
          newSubset.add(inputSet.get(index));
          tempSubsets.add(newSubset);
        }
        finalSubsets.add(tempSubsets);
      }
      return finalSubsets;
    }

8.4
===

    public void permutations(String str) {
      doPermute("", str);
    }

    public void doPermute(String prefix, String str) {
      int n = str.length();
      if(n == 0)
        System.out.println(prefix);
      else {
        for(int i = 0; i < n; i++) {
          doPermute(prefix + str.charAt(i), str.substring(0,i) + str.substring(i+1, n));
        }
      }
    }

8.5
===

    public void printParens(int count) {
      char[] input = char[count*2];
      parenCalc(count, count, input, 0);
    }

    public void parenCalc(int left, int right, char[] input, int count) {
      if(left < 0 || right < left) 
        return;
      if(left == 0 && right == 0)
        System.out.println(input);
      else {
        if(left > 0) {
          input[count] = "(";
          parenCalc(left-1, right, input, count+1);
        }
        if(right > left) {
          input[count] = ")";
          parenCalc(left, right-1, input, count+1);
        }
      }
    }

8.6
===

    public void paint(Color[][] screen, int x, int y, Color ocolor, Color ncolor) {
      if(x < 0 || x > screen[0].length) || (y<0 || y > screen.length)
        return;

      if(screen[y][x] == ocolor) {
        screen[y][x] = ncolor;
        paint(screen, x-1, y, ocolor, ncolor);
        paint(screen, x+1, y, ocolor, ncolor);
        paint(screen, x, y-1, ocolor, ncolor);
        paint(screen, x, y+1, ocolor, ncolor);
      }
    }

8.7
===

    public int makeChange(int n, int denomination) {
      int result = 0;
      if(denomination == 25) {
        next = 10;
        break;
      } else if(denomination == 10) {
        next = 5;
        break;
      } else if(denomination == 5) {
        next = 1;
        break;
      } else if(denomination == 1) {
        return 1;
      }

      int result = 0;
      for(int i = 0; i* denomination <= n; i++) {
        result += makeChange(n-i*denomination, next);
      } 
      return result;
    }

