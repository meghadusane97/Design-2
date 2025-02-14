# Design-2

## Problem 1: Design Queue using Stack

```Java
// Time Complexity : O(1)
// Space Complexity : O(n)
// Did this code successfully run on Leetcode : yes
// Any problem you faced while coding this : no

class MyQueue {
    Stack<Integer> s1;
    Stack<Integer> s2;

    public MyQueue() {
        this.s1 = new Stack<>();
        this.s2 = new Stack<>();
    }

    public void push(int x) { //O(n) -> every element pushed and popped twice
        s1.push(x);
    }

    public int pop() { //O(1)
        if(s2.isEmpty()){
            while(!s1.isEmpty()){
                s2.push(s1.pop());
            }
        }
        return s2.pop();
    }

    public int peek() { //O(1)
        if(s2.isEmpty()){
            while(!s1.isEmpty()){
                s2.push(s1.pop());
            }
        }
        return s2.peek();
    }

    public boolean empty() { //O(1)
        return s1.isEmpty() && s2.isEmpty();
    }
}
/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```

## Problem 2: Design HashMap

```Java
// Time Complexity : O(1)
// Space Complexity : O(n)
// Did this code successfully run on Leetcode : yes
// Any problem you faced while coding this : no

class MyHashMap{
    ListNode[] nodes = new ListNode[10000];
    public int get(int key){
        int index = getIndex(key);
        ListNode prev = findElement(index, key);
        
        return prev.next == null ? -1 : prev.next.val;
    }
    public void put(int key, int value) {
        int index = getIndex(key);
        ListNode prev = findElement(index, key);
        if (prev.next == null)
            prev.next = new ListNode(key, value);
        else
            prev.next.val = value;
    }
    public void remove(int key) {
        int index = getIndex(key);
        ListNode prev = findElement(index, key);
        if(prev.next != null)
            prev.next = prev.next.next;
    }
    private int getIndex(int key) {
        return Integer.hashCode(key) % nodes.length;
    }
    private ListNode findElement(int index, int key) {
        if(nodes[index] == null)
            return nodes[index] = new ListNode(-1, -1);
        
        ListNode prev = nodes[index];
        while(prev.next != null && prev.next.key != key) {
            prev = prev.next;
        }
        return prev;
    }
    private static class ListNode
    {
        int key, val;
        ListNode next;

        ListNode(int key, int val) {
            this.key = key;
            this.val = val;
        }
    }
}
/**
 * Your MyHashMap object will be instantiated and called as such:
 * MyHashMap obj = new MyHashMap();
 * obj.put(key,value);
 * int param_2 = obj.get(key);
 * obj.remove(key);
 */
```



