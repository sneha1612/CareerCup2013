9.1
===

    public void sortedMerge(int[] a, int[] b, int m, int n) {
      int k = m+n-1;
      int i = m-1;
      int j = n-1;

      while(i>=0 && j>= 0)
      if(a[i] > b[j]) {
        a[k] = a[i];
        k--;
        i--;
      } else {
        a[k] = b[j];
        k--;
        j--;
      }

      while(j>=0) {
        a[k] = b[j];
        k--;
        j--;
      }
    }

9.2
===

    public void sortChars(String s) {
      char[] charArray = s.toCharArray();
      Arrays.sort(charArray);
      return new String(charArray);
    }

    public compare(String s1, String s2) {
      sortChars(s1).compareTo(sortChars(s2));
    }

9.3
===

    public void modSearch(int[] arr, int n) {
      int low = 0;
      int high = arr.length -1;

      while(low <= high) {
        mid = (low+high/2);
        if(n == arr[mid])
          return mid;
        else if(arr[low] < arr[mid]) {
          if(n < arr[mid])
            high = mid -1;
          else if(arr[low] <= arr[mid]) {
            if(n > arr[mid])
              low = mid+1;
            else if (n >= arr[low])
              mid = high -1;
            else
              low = mid+1;
          }
          else if(n < arr[mid])
            high = mid-1;
          else if (n <= arr[high])
            low = mid+1;
          else
            high = mid-1;
        }
      }
      return -1;
    }

9.6
===

    public boolean find(int[][] input, int val, int m, int n) {
      int row = 0;
      int column = n-1;

      while(row <= m && column >= 0) {
        if(input[row][column] == val)
          return true;
        if(input[row][column] > val)
          col--;
        else
          row++;
      }
      return false;
    }