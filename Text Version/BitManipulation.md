5.1
===

    public int copyBits(int m, int n, int i, int j) {
      int mask = 0;
      for(int x=i; x<=j; x++) {
        mask = mask + Math.pow(2,x);
      }
      int relevant = m & mask;
      int clear = n & ~mask;
      return relevant | clear;
    }