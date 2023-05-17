import java.util.Scanner;

// program untuk melakukan insert di AVL Tree
class Node {
    int data, height;
    Node left, right;

    Node(int data) {
        this.data = data;
        height = 1;
    }
}

class AVLTree {
    Node root;

    // fungsi untuk height dari tree
    int height(Node node) {
        if (node != null) {
            return node.height;
        }
        return 0;
    }

    // fungsi untuk max 2 nilai
    int max(int a, int b) {
        return (a < b) ? b : a;
    }

    // method untuk rotate ke kanan
    Node rightRotate(Node y) {
        Node x = y.left;
        Node temp = x.right;

        // melakukan rotasi
        x.right = y;
        y.left = temp;

        // memperbarui height
        y.height = max(height(y.left), height(y.right)) + 1;
        x.height = max(height(x.left), height(x.right)) + 1;

        // return new root
        return x;
    }

    // method untuk rotate ke kiri
    Node leftRotate(Node x) {
        Node y = x.right;
        Node temp = y.left;

        // melakukan rotasi
        y.left = x;
        x.right = temp;

        // memperbarui height
        x.height = max(height(x.left), height(x.right)) + 1;
        y.height = max(height(y.left), height(y.right)) + 1;

        // return new root
        return y;
    }

    // menghitung dan memeriksa imbalance
    int countBalance(Node node) {
        if (node != null) {
            return height(node.left) - height(node.right);
        }
        return 0;
    }

    // method untuk menambahkan node baru
    Node insert(Node node, int data) {
        // insert BST biasa
        if (node != null) {
            if (data < node.data) {
                node.left = insert(node.left, data);
            } else if (data > node.data) {
                node.right = insert(node.right, data);
            } else {
                return node;
            }

            // memperbarui height dari ancestor
            node.height = 1 + max(height(node.left), height(node.right));
            
            // mendapatkan faktor balance dari ancestor untuk memeriksa apakah menjadi tidak balance
            int balance = countBalance(node);

            // jika tidak seimbang, akan ada 4 case
            // Left Left
            if (balance > 1 && data < node.left.data) {
                return rightRotate(node);
            // Right Right
            } else if (balance < -1 && data > node.right.data) {
                return leftRotate(node);
            // Left Right
            } else if (balance > 1 && data > node.left.data) {
                node.left = leftRotate(node.left);
                return rightRotate(node);
            // Right Left
            } else if (balance < -1 && data < node.right.data) {
                node.right = rightRotate(node.right);
                return leftRotate(node);
            }
            return node;
        }
        return (new Node(data));
    }

    // method print preorder
    void printPreorder(Node node, int level) {
        if (node != null) {
            for (int i = 0; i < level; i++) {
                System.out.print("--");
            }
            System.out.println(node.data);
            printPreorder(node.left, level + 1);
            printPreorder(node.right, level + 1);
        }
    }

    // method print inorder
    void printInorder(Node node, int level) {
        if (node != null) {
            printInorder(node.left, level + 1);
            for (int i = 0; i < level; i++) {
                System.out.print("--");
            }
            System.out.println(node.data);
            printInorder(node.right, level + 1);
        }
    }

    // method print postorder
    void printPostorder(Node node, int level) {
        if (node != null) {
            printPostorder(node.left, level + 1);
            printPostorder(node.right, level + 1);

            for (int i = 0; i < level; i++) {
                System.out.print("--");
            }
            System.out.println(node.data);
        }
    }

    // method untuk menghitung level atau tingkatan tree berdasarkan height
    int countLevels(Node node) {
        if (node != null) {
            int height = node.height;
            return height;
        }
        return 0;
    }
}

class MainAVLTree {
    public static void main(String[] args) {
        AVLTree tree = new AVLTree();
        Scanner scan = new Scanner(System.in);

        System.out.println("Ketikkan Perintah : ");

        while (true) {
            String perintah = scan.nextLine();
            String[] kata = perintah.split(" ");

            switch (kata[0]) {
                case "insert":
                    int angka = Integer.parseInt(kata[1]);
                    tree.root = tree.insert(tree.root, angka);
                    break;
                case "print":
                    if (tree.root == null) {
                        System.out.println("Tree kosong.");
                    } else {
                        switch (kata[1]) {
                            case "preorder":
                                System.out.println("Pre-Order: ");
                                tree.printPreorder(tree.root, 0);
                                break;
                            case "inorder":
                                System.out.println("In-Order: ");
                                tree.printInorder(tree.root, 0);
                                break;
                            case "postorder":
                                System.out.println("Post-Order: ");
                                tree.printPostorder(tree.root, 0);
                                break;
                            case "levels":
                                int levels = tree.countLevels(tree.root);
                                System.out.println("Jumlah level: " + levels);
                                break;
                            default:
                                System.out.println("Method tidak ada");
                        }
                        System.out.println();
                    }
                    break;
                case "exit":
                    System.out.println("Program Berakhir.");
                    return;
                default:
                    System.out.println("Perintah tidak ada");
                    System.out.println();
            }
        }
    }
}
