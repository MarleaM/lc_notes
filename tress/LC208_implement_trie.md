## Problem 208: Implement Trie
A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

Trie() Initializes the trie object.
void insert(String word) Inserts the string word into the trie.
boolean search(String word) Returns true if the string word is in the trie (i.e., was inserted before), and false otherwise.
boolean startsWith(String prefix) Returns true if there is a previously inserted string word that has the prefix prefix, and false otherwise.
 

```python
## Problem 208: Implement Trie
# A trie (pronounced as "try") or prefix tree is a data structure used for efficiently storing and retrieving keys in a dataset of strings.
# Common applications of this structure include autocomplete and spellchecking features.

# Implement the Trie class with three main methods:
# - insert(String word): Adds a word to the trie.
# - search(String word): Checks if a word is present in the trie.
# - startsWith(String prefix): Checks if there is any word in the trie that starts with the given prefix.

class TrieNode(object):
    def __init__(self):
        # Initialize an empty dictionary to hold child nodes, where each key is a character
        # and the value is the corresponding TrieNode.
        self.children = {}  # E.g., {'x': TrieNode(), 'y': TrieNode(), 'z': TrieNode()}
        
        # Boolean to mark if this node represents the end of a complete word.
        self.isLastLetter = False


class Trie(object):
    def __init__(self):
        # Initialize the Trie with a root TrieNode (an empty node with no children initially).
        self.root = TrieNode()

    def insert(self, word):
        """
        :type word: str
        :rtype: None
        """
        curr = self.root  # Start from the root node

        # Loop through each character in the word and insert it into the Trie.
        for c in word:
            # If the character is not already a child of the current node, add it.
            if c not in curr.children:
                curr.children[c] = TrieNode()
            # Move to the child node corresponding to the current character.
            curr = curr.children[c]
        
        # After inserting all characters, mark the last node as the end of a word.
        curr.isLastLetter = True

    def search(self, word):
        """
        :type word: str
        :rtype: bool
        """
        curr = self.root  # Start from the root node

        # Loop through each character in the word to check if it exists in the Trie.
        for c in word:
            # If the character is not found among the current node's children, the word isn't in the Trie.
            if c not in curr.children:
                return False  # The word doesn't exist in the Trie
            # Move to the child node corresponding to the current character.
            curr = curr.children[c]
        
        # Check if the last node reached is marked as the end of a word.
        return curr.isLastLetter

    def startsWith(self, prefix):
        """
        :type prefix: str
        :rtype: bool
        """
        curr = self.root  # Start from the root node

        # Loop through each character in the prefix to check if it exists in the Trie.
        for c in prefix:
            # If the character is not found among the current node's children, the prefix isn't in the Trie.
            if c not in curr.children:
                return False  # No word starts with this prefix
            # Move to the child node corresponding to the current character.
            curr = curr.children[c]
        
        # If all characters in the prefix are found, return True.
        return True


# Example usage of the Trie:
# obj = Trie()                # Initialize a new Trie object
# obj.insert("apple")         # Insert the word "apple" into the Trie
# param_2 = obj.search("apple")  # Returns True if "apple" is found
# param_3 = obj.startsWith("app") # Returns True if any word starts with "app"

```
### Comments
