# Stacks and Queues

# What is a Stack

- a data structure that consist of Nodes. Each Node references the next node in the stack, but does not reference its previous.
- Push: Node or items that are put into the stack are pushed.
- Pop: Node or items that are removed from the stack are popped. Exception will be raised when trying to pop an empty stack.
- Top: top of the stack.
- Peek: peek means you will view the value of the top Node in the stack. Exception will be raised when trying to peep an empty stack.
- IsEmpty: returns true when stack is empty or false when not empty.

- FILO: First In Last Out - the first item added in the stack will be the last item popped out of the stack.
- Push O(1) - Pushing a Node onto the stack will always be an O(1) operation. When adding a Node, you push it into the stack by assigning it as the new top, with its next property equal to the original top.
- Pop O(1) - when conducting a pop, the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user. Typically you would check isEmpty before doing a pop as this will ensure an exception is not raised, you can also wrap the call in a try/catch block.
- Peek O(1) - you will only be inspecting the top Node of the stack and would check isEmpty before conducting a peek or you can wrap the call in a try/catch block.

## What is a Queue
- Enqueue: Nodes or items that are added to the queue.
- Dequeue: Node or items that are removed from the queue. Exception will be raised when queue is empty.
- Front: front/first Node of queue.
- Rear: rear/last Node of queue.
- Peek: view the value of the front Node in the queue. Exception will be raised if queue is empty.
- isEmpty: returns true when queue is empty or false when it is not empty.
- FIFO: First In First Out - the first item in the queue will be the first item out of the queue.
- LILO: Last In Last Out - last item in the queue will be the last item out of the queue.
## Enqueue O(1)
- when you add an item to the queue, you use the enqueue action. This is done with an O(1) operation in time because it does not matter how many other items live in the queue(n); it take the same amount of time to perform the operation.
node = new Node(value)
   rear.next <-- node
   rear <-- node
## Dequeue O(1)
- remove an item from the queue, use the dequeue action. This is done with an O(1) operation in time because it doesn't matter how many other items are in the queue, you are always just removing the front node of the queue.
Node temp <-- front
   front <-- front.next
   temp.next <-- null

   return temp.value