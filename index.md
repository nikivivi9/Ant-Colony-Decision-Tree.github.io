---
layout: default
title: Home
---
# Ant Colony Decision Tree

## Abstract 
Decision trees have been widely used in machine learning for classification and regression tasks based on its tree-like structure that represents a series of decisions and their possible consequences. In order to improve the accuracy of decision trees, researchers have proposed a new method called Ant Colony Decision Trees (ACDT), based on the Ant Colony Optimization (ACO). The ACO is a metaheuristic inspired by the foraging behavior of real ants, where they search for the shortest path between their nest and food sources by considering both local heuristic and previous knowledge, observed by pheromone changes. This article will start with a basic definition of a decision tree and then expand to the more complex ACDT, including its background and detailed explanations of the algorithm. 


## Decision Trees
A decision tree is a non-parametric supervised learning algorithm for classification and regression tasks. It has a hierarchical tree structure consisting of a root node, internal nodes, edges, and leaf nodes. It follows an iterative top-down procedure of selecting the best attribute to label an internal node of the tree. It starts at the root node that contains the entire sample, then splits at the internal node that serves as the test condition, and ends at the leaf node that is the final prediction result (Figure 1). This basic approach represents a greedy strategy to create a decision tree, since the selection of an attribute at early iterations cannot be reconsidered at later iterations. i.e., the selection of the best attribute is made locally at each iteration, without taking into consideration its influence over the subsequent iterations. However, the newly proposed ACDT algorithm is able to construct the decision tree with the in a top-down fashion by probabilistically selecting attributes to be added as decision nodes based on the amount pheromone and heuristics information, with the pheromone values represent the quality of the connection between a parent and child decision nodes.
