```java
import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;

class Main {
  public static void main(String[] args) throws IOException {
    BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
    int tNum = Integer.parseInt(bf.readLine());

    for(int i = 0; i < tNum; i++) {
      String[] line = bf.readLine().split(" ");
      MyList list = new MyList();
      list.add(Integer.parseInt(line[0]));
      list.suicide(Integer.parseInt(line[1]));
      list.show();
    }
  }
}

class MyList {
  Node head;
  int size;

  public MyList() {
    head = null;
    size = 0;
  }

  private class Node {
    private Node next;
    private int data;

    Node(int data) {
      this.data = data;
      next = null;
    }
  }

  public void add(int num) {
    for(int i = 1; i <= num; i++) {
      Node newNode = new Node(i);
      if(head == null) {
        head = newNode;
      } else {
        Node temp = head;
        while(temp.next != null) {
          temp = temp.next;
        }
        temp.next = newNode;
      }
      size++;
    }
  }

  public void suicide(int num) {
    int nextN = 0;
    Node temp = head.next;
    head = temp;
    nextN++;
    size--;
    while(this.size > 2) {
      if(nextN == num-1) {
        if(temp.next == null) {
          head = head.next;
          temp = head;
        } else {
          temp.next = temp.next.next;
          temp = temp.next;
          if(temp == null) {
            temp = head;
          }
        }
        size--;
        nextN = 1;
      } else {
        temp = temp.next;
        if(temp == null) {
          temp = head;
        }
        nextN++;
      }
    }
  }

  public void show() {
    System.out.println(head.data + " " + head.next.data);
  }
}
```
