# binary
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package binarytree;


public class BinarySearchTree {
    private TreeNode root;
    
    public BinarySearchTree() {
        this.root = null;
    }

    public void insert(int val) {
        root = insertRec(root, val);
    }

    private TreeNode insertRec(TreeNode node, int val) {
        if (node == null) {
            return new TreeNode(val);
        }
        if (val < node.val) {
            node.left = insertRec(node.left, val);
        } else if (val > node.val) {
            node.right = insertRec(node.right, val);
        }
        return node;
    }

    public void delete(int val) {
        root = deleteRec(root, val);
    }

    private TreeNode deleteRec(TreeNode node, int val) {
        if (node == null) {
            return null;
        }
        if (val < node.val) {
            node.left = deleteRec(node.left, val);
        } else if (val > node.val) {
            node.right = deleteRec(node.right, val);
        } else {
            if (node.left == null) {
                return node.right;
            } else if (node.right == null) {
                return node.left;
            }
            node.val = findMin(node.right);
            node.right = deleteRec(node.right, node.val);
        }
        return node;
    }

    private int findMin(TreeNode node) {
        while (node.left != null) {
            node = node.left;
        }
        return node.val;
    }

    public void inOrderTraversal() {
        inOrderRec(root);
    }

    private void inOrderRec(TreeNode node) {
        if (node != null) {
            inOrderRec(node.left);
            System.out.print(node.val + " ");
            inOrderRec(node.right);
        }
    }

    public void preOrderTraversal() {
        preOrderRec(root);
    }

    private void preOrderRec(TreeNode node) {
        if (node != null) {
            System.out.print(node.val + " ");
            preOrderRec(node.left);
            preOrderRec(node.right);
        }
    }

    public void postOrderTraversal() {
        postOrderRec(root);
    }

    private void postOrderRec(TreeNode node) {
        if (node != null) {
            postOrderRec(node.left);
            postOrderRec(node.right);
            System.out.print(node.val + " ");
        }
    }

    public static void main(String[] args) {
        // Create a binary search tree
        BinarySearchTree bst = new BinarySearchTree();

        // Insert some values into the tree
        bst.insert(50);
        bst.insert(30);
        bst.insert(70);
        bst.insert(20);
        bst.insert(40);
        bst.insert(60);
        bst.insert(80);

        // Perform in-order traversal and print the output
        System.out.println("In-order Traversal:");
        bst.inOrderTraversal();
        System.out.println();

        // Perform pre-order traversal and print the output
        System.out.println("Pre-order Traversal:");
        bst.preOrderTraversal();
        System.out.println();

        // Perform post-order traversal and print the output
        System.out.println("Post-order Traversal:");
        bst.postOrderTraversal();
        System.out.println();
    }
}

