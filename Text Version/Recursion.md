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

