```java
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;

class Main {
  public static void main(String[] args) throws IOException {
    BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
    int tNum = Integer.parseInt(bf.readLine());

    long[] signal = new long[5000000];
    int[] input = new int[5000000];
    signal[0] = 1983l;
    int curSig = 1;

    for(int i = 0; i < tNum; i++) {
      String[] line = bf.readLine().split(" ");
      int K = Integer.parseInt(line[0]);
      int N = Integer.parseInt(line[1]);

      for(int j = curSig; j < N; j++) {
        input[j] = (int)(signal[j-1] % 10000) + 1;
        signal[j] = (signal[j-1] * 214013 + 2531011) % (long)Math.pow(2, 32);
      }

      int head = 1, tail = 1;
      int temp = 0;
      int result = 0;

      for(int j = curSig; j < N; j++) {
        temp += input[tail++];
        //System.out.println(temp + " : " + head + ", " + tail);
        while(temp > K) {
          temp -= input[head++];
        }
        if(temp == K) {
          //System.out.println(temp + " : " + head + ", " + tail);
          result++;
          temp -= input[head++];
        }

        if(head >= N || tail >= N)
          break;
      }
      System.out.println(result);
    }
  }
}
```