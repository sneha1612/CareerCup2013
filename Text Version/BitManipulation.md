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

5.4
===
  
    ((n & (n-1)) == 0)

    This will be true when n and n-1 have no positions of 1's in common. That will happen when n is a power of 2.

5.5
===

    public int numBitsChanged(int a, int b) {
      int temp = a ^ b;
      int count = 0;
      for(int i=0; i< 32; i++) {
        if(temp & (1<<i) != 0)
          count++;
      }
      return count;
    }

5.3
===

    public void nextSmallestAndLargest(int n) {
      int final = getNumberOfOnes(n);

      for(int k = n-1; k>=0; k--) {
        if(final == getNumberOfOnes(k))
          System.out.println("Next smallest:" +  k);
          break;
      }

      for(int k = n+1; k<=32; k++) {
        if(final == getNumberOfOnes(k))
          System.out.println("Next largest:" +  k);
          break;
      }
    }

    public int getNumberOfOnes(int n) {
      int count = 0;
      for(int i=0; i< 32; i++) {
        if(n & (1<<i) != 0)
          count++;
      }
      return count;
    }

5.4
===

    public int swapBits(int n) {
      int temp1 = (n & (10101010101010101010101010101010)) >> 1;
      int temp2 = (n & (01010101010101010101010101010101)) << 1;

      return temp1 | temp2;
    }

