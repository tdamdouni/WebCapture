# Binary Tree (Stuff Formally Trained Programmers Know)

_Captured: 2018-06-14 at 13:20 from [dzone.com](https://dzone.com/articles/binary-tree-stuff-formally-trained-programmers-kno?edition=384193&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-13)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

This post is one in a series about stuff formally trained programmers know - the rest of the series can be found [here](https://www.sadev.co.za/content/stuff-formally-trained-programmers-know).

## Binary Tree

In the [previous post](https://dzone.com/articles/sftpk-tree), we looked at the tree pattern, which is a theoretical way of structuring data with many advantages. A tree is just a theory though, so what does an actual implementation of it look like? A common data structure implementation is a binary tree.

The name binary tree gives us a hint to how it is structured, each node can have at most 2 child nodes.

![Example of annotated binary tree](https://www.sadev.co.za/files/binarytree1tn.png)

## Classifications

As a binary tree has some flexibility in it, a number of classifications have come up to have a consistent way to discuss a binary tree. Common classifications are:

  * **Full** binary tree: Each node in a binary tree can have zero, one, or two child nodes. In a **full** binary tree, each node can only have zero or two child nodes.

  * **Perfect** binary tree: This is a full binary tree with the additional condition that all leaf nodes (i.e. nodes with no children) are at the same level/depth.

  * **Complete** binary tree: The complete binary tree is where each leaf node is as far left as possible.

  * **Balanced** binary tree: A balanced binary tree is a tree where the height of the tree is as small a number as possible.

## Implementations

While a binary tree is more than just a pattern, there are no out of the box implementations in C#, Java, or JavaScript for it. The reason is that it is a very simple data structure and so if you need just the data structure you could implement it yourself but, more importantly, you likely want more than the simple structure - you want a structure that optimizes for traversal or data management.

## References

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
