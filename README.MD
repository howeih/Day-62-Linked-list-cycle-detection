Day 62: Linked-list cycle detection
<br>
![Alt text](Linked-List-Loop.gif?raw=true "Linked-List-Loop")
<br>
The algorithm is to start two pointers, slow and fast from head of linked list. We move slow one node at a time and fast two nodes at a time. If there is a loop, then they will definitely meet. This approach works because of the following facts.
<br>
1) When slow pointer enters the loop, the fast pointer must be inside the loop. Let fast pointer be distance k from slow.
<br>
2) Now if consider movements of slow and fast pointers, we can notice that distance between them (from slow to fast) increase by one after every iteration. After one iteration (of slow = next of slow and fast = next of next of fast), distance between slow and fast becomes k+1, after two iterations, k+2, and so on. When distance becomes n, they meet because they are moving in a cycle of length n.
<br>
For example, we can see in below diagram, initial distance is 2. After one iteration, distance becomes 3, after 2 iterations, it becomes 4. After 3 iterations, it becomes 5 which is distance 0. And they meet.
<br>

![Alt text](Floyd-Proof.jpg?raw=true "Floyd-Proof")

<br>

run:
```
fn main() {
    let mut linked_list_with_loop = gen_linked_list_with_loop();
    let mut linked_list = gen_linked_list();
    let r = linked_list.find_loop();
    check_result(r);
    let rl = linked_list_with_loop.find_loop();
    check_result(rl);
}
```

result:
```
No Loop found
Iterator meet at: 3 loop found.

```
