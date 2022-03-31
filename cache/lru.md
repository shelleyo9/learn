哈希表+双向链表

实现O(1)的get()&put()

```c++
struct Node {
    int key;
    int value;
    Node(int k, int v) {
        key = k;
        value = v;
    };
    Node* prev;
    Node* next;
};

class DoublyLinkedList {
public:
    // ATTENTION: dummy nodes
    Node *head, *tail;

    DoublyLinkedList() {
        head = new Node(0, 0);
        tail = new Node(0, 0);
        head->next = tail;
        tail->prev = head;
    }
    void remove(Node* node) {
        node->prev->next = node->next;
        node->next->prev = node->prev;
    }

    void push_back(Node* node) {
        tail->prev->next = node;
        node->prev = tail->prev;
        tail->prev = node;
        node->next = tail;
    }

    Node* pop_front() {
        if (head->next == tail) {
            return nullptr;
        }
        Node* deleteNode = head->next;
        head->next = head->next->next;
        deleteNode->next->prev = head;
        return deleteNode;
    }
};

class LRUCache {
public:
    unordered_map<int, Node*> sMap;
    DoublyLinkedList* sList;
    int cap;
    int size;

    LRUCache(int capacity) {
        size=0;
        cap=capacity;
        sList = new DoublyLinkedList();
    }
    
    int get(int key) {
        if (!sMap.count(key)) {
            return -1;
        }
        Node* node = sMap[key];
        // TODO: move node to tail
        sList->remove(node);
        sList->push_back(node);
        //cout << "refresh " << key << endl;
        return node->value;
    }
    
    void put(int key, int value) {
        //cout << "size " << size << endl;
        if (sMap.count(key)) {
            //cout << "update " << key << endl;
            Node* curNode = sMap[key];
            curNode->value = value;
            sList->remove(curNode);
            sList->push_back(curNode);
            return;
        }
        if (size == cap) {
            Node* firstNode = sList->pop_front();
            sMap.erase(firstNode->key);
            //cout << "remove " << firstNode->key << endl;
            size--;
        }
        Node *newNode = new Node(key, value);
        sList->push_back(newNode);
        sMap[key]=newNode;
        //cout << "add " << key << endl;
        size++;
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */
```

