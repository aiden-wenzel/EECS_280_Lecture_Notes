## Linked List
- Data isn't stored together in memory
- Linked lists contain a group of Nodes
- Each node contains data and a pointer to the next node
- The Linked list should know where the first node is

```cpp
class Linked_List {
private:
    Node* first;
    struct Node {
        typename data;
        Node* next;
    };
public:
    Linked_List() {
        this->first = nullptr;
    }

    bool empty() const {
        return first == nullptr;
    }

    int& peek() const {
        assert(!this->empty());
        return first->data;
    }

    void push(int value) {
        Node* push_node = new Node;
        push_node->data = value;
        push_node->next = this->first;
        this->first = push_node;
    }

    int pop() {
        assert(!this->empty());
        int return_val = this->first->data;
        Node* temp = this->first;
        this->first = first->first;
        delete temp;
        return return_val;
    }
};

// traversing the list 
for (Node* s = first; s != nulptr; s = s->next) {
    cout << s->data << '\n';
}
```

## Traversing a Linked List


