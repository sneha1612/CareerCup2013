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
