# Binary-Search-Tree

A special type of binary tree where each node has at most two children, the values in left sub-tree of a node are less than or equal to the node's value, while the right sub-tree values are greater than node value

### Level order traversal

Each level of Binary search tree from root towards leaf will be traversed one by one. Every node on a level from right to left will be traversed and than, the next level will be traversed in the same way <br><br>
<img src=https://github.com/Mahadi2478/Binary-Search-Tree/blob/main/1461696188-8eddd12300-BST.png>

```
#include <iostream>
#include <queue>  // Include the queue header
using namespace std;

class Node {
public:
    int data;
    Node* left;
    Node* right;

    Node(int d) {
        this->data = d;
        this->left = NULL;
        this->right = NULL;
    }
};

Node* insertintoBST(Node* root, int d) {
    if (root == NULL) {
        root = new Node(d);
        return root;
    }

    if (d > root->data) {
        root->right = insertintoBST(root->right, d);  // insert at right part
    } else {
        root->left = insertintoBST(root->left, d);
    }
    return root;
}

void takeinput(Node*& root) {
    int data;
    cin >> data;
    while (data != -1) {
        root = insertintoBST(root, data);
        cin >> data;
    }
}

void levelordertraversal(Node* root) {
    if (root == NULL) {
        return;
    }

    queue<Node*> q;
    q.push(root);
    q.push(NULL);

    while (!q.empty()) {
        Node* temp = q.front();
        q.pop();

        if (temp == NULL) {
            cout << endl;  // previous level has been completely traversed
            if (!q.empty()) {
                q.push(NULL);  // queue still has some child nodes
            }
        } else {
            cout << temp->data << " ";
            if (temp->left) {
                q.push(temp->left);
            }
            if (temp->right) {
                q.push(temp->right);
            }
        }
    }
}

int main() {
    Node* root = NULL;
    cout << "Enter data to create BST" << endl;
    takeinput(root);
    cout << "Printing the BST" << endl;
    levelordertraversal(root);

    return 0;  // Add a return statement in the main function
}
```


