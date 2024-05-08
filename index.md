---
layout: default
title: Ant Colony Decision Tree
---


## Abstract
Decision trees have been widely used in machine learning for classification and regression tasks based on its tree-like structure that represents a series of decisions and their possible consequences. In order to improve the accuracy of decision trees, researchers have proposed a new method called Ant Colony Decision Trees (ACDT), based on the Ant Colony Optimization (ACO). The ACO is a metaheuristic inspired by the foraging behavior of real ants, where they search for the shortest path between their nest and food sources by considering both local heuristic and previous knowledge, observed by pheromone changes. This article will start with a basic definition of a decision tree and then expand to the more complex ACDT, including its background and detailed explanations of the algorithm. 


## Decision Trees
A decision tree is a non-parametric supervised learning algorithm for classification and regression tasks. It has a hierarchical tree structure consisting of a root node, internal nodes, edges, and leaf nodes. It follows an iterative top-down procedure of selecting the best attribute to label an internal node of the tree. It starts at the root node that contains the entire sample, then splits at the internal node that serves as the test condition, and ends at the leaf node that is the final prediction result (Figure 1). This basic approach represents a greedy strategy to create a decision tree, since the selection of an attribute at early iterations cannot be reconsidered at later iterations. i.e., the selection of the best attribute is made locally at each iteration, without taking into consideration its influence over the subsequent iterations. However, the newly proposed ACDT algorithm is able to construct the decision tree with the in a top-down fashion by probabilistically selecting attributes to be added as decision nodes based on the amount pheromone and heuristics information, with the pheromone values represent the quality of the connection between a parent and child decision nodes.

<p align="center">
<img src="/assets/DecisionTree.jpg" width="400" height="250">
</p>


## Ant Colony Optimization (ACO)
### Background 
Ant colony optimization (ACO)  technique is inspired by the foraging behavior of ant colonies. These eusocial insects prefer community survival while their individual behavior is relatively simple and straightforward. Ants indirectly communicate between each other by making small modifications to their environment, enabling them to accomplish sophisticated tasks. When ants leave their colony in search of food, they explore various potential routes from their nest to the targeted food source. Each ant leaves behind a pheromone trail on its path. If a path is selected by multiple ants, it would collect a higher concentration of pheromone. Conversely, if there are no ants continuously following this path, the pheromone deposited by previous ants would evaporate. The concentration of pheromone on each path would affect the ant’s decision-making. Path with higher pheromone concentration would be more attractive for the following ants, whereas path with lower concentration of pheromone would be less likely to be chosen. Since ants would traverse shorter paths much quicker, shorter paths tend to gain higher pheromone concentration over time. Ultimately, ants are able to identify and converge to the optimal and shortest path from their nest to the food source. [ACO Visualisation](https://courses.cs.ut.ee/demos/visual-aco/#/visualisation "ACO Visualisation")

<p align="center">
<img src="/assets/ACOVisualization.gif" width="300" height="250">

### Algorithm 
In the ACO algorithm, a colony of ants builds a candidate solution that is optimal or near-optimal guided by their pheromone and heuristic information. These ants traverse a construction graph to where each vertex in the graph indicates a potential element of the solution and the act of an ant moving along an edge symbolizes one ant is adding to the current solution. Once the ants successfully identify the optimal path through the problem’s construction graph, they achieve the best solution. 

In the following figure, we present the pseudocode of a basic ACO algorithm which remains four primary procedures.
* **Initialize:** In this procedure, we define the algorithm’s parameters and set up the pheromone matrix along with heuristic information relevant to the vertices and edges of our construction graph.
* **Construct Ant Solution:** In this procedure, we simulate the movement of artificial ants to gradually construct the candidate solutions. These ants navigate through the construction graph and make decisions at each step by applying a stochastic decision policy which incorporates the heuristic and pheromone information. 
* **Apply local search:** The application of local search is optional and it facilitates us to refine ant’s solution. Local search would introduce minor adjustments to a solution to examine its neighbor solutions and the implementation of this algorithm usually exhibits great enhancement on our ACO algorithm’s performance. 
* **Update pheromones:** In this procedure, we would update the pheromone levels on the components of the problem’s construction graph. The update involves either an increase as ants deposit pheromones along the paths while forming their candidate solutions, or a decrease due to the evaporation of pheromone. 

We would iterate through the constructing and updating steps until we met the termination criteria, at which point we are able to achieve the optimal solution.

<p align="center">
<img src="/assets/ACO_algorithm_pseudocode.jpg" width="400" height="250">
</p>

## Ant Colony Decision Trees (ACDT)
Based on the structure of the ACO algorithm, researchers have proposed applying it on decision tree modeling. As a result, a new metaheuristics approach based on ant colony algorithms, known as Ant Colony Decision Trees (ACDT), has been developed. Compared to the general decision tree algorithm, in ACDT,  each ant chooses the appropriate attribute for splitting in each node of the constructed decision tree according to the heuristic function and pheromone values. Following the logic of ACO, the algorithm for ACDT can be written as below.

As can be seen in Figure 3, the algorithm starts by initializing the pheromone values and computing the heuristic information for each attribute of the training set. Then, it enters in an iterative for loop. In each iteration, an ant in the colony creates a new decision tree until the maximum number of iterations is reached. 

Each ant creates a decision tree (for loop) in a top-down fashion by probabilistically
selecting attributes to be added as decision nodes based on the amount of pheromone and heuristic information. The procedure for creating a decision tree (CreateTree procedure) involves three parameters: the collection of training examples, the predictor attributes, and the edge that the ant is following, which initially corresponds to the default edge (indicated by the symbol '-'). Once the tree construction procedure has finished, the created tree is pruned in order to simplify the tree and thus potentially avoid overfitting of the model to the training data. 

After the pruning, the tree is evaluated and if the quality of the newly pruned tree surpasses the quality of the existing iterative optimal tree, the iterative optimal tree (treeib) is updated. Finally, the iteration-best tree constructed by the ants is used to update the pheromone values, the global-best tree (treegb) is stored/updated and a new iteration of the algorithm starts. When the maximum number of iterations is reached or the algorithm has converged
(CheckConvergence procedure), the global-best tree is returned as the discovered decision
tree.

<p align="center">
<img src="/assets/ACDT_algo.jpeg" width="700" height="400">
</p>



## ACDT

The Ant Colony Decision Tree algorithm consists of the following key components:
* Pheromone Trails: A pheromone matrix is used to represent the desirability of selecting specific features and splitting criteria at each node of the decision tree. Initially, the pheromone values are set to a small positive constant.
* Ant Colony: A population of artificial ants is initialized, each representing a candidate decision tree. The ants traverse the feature space, constructing decision trees based on the pheromone trails and a probabilistic decision rule.
* Ant Evaluation: Each ant's constructed decision tree is evaluated using a fitness function, typically based on the accuracy or information gain of the tree on the training data.
*  Pheromone Update: The pheromone trails are updated based on the performance of the ants' decision trees. Pheromone evaporation is applied to prevent premature convergence, and the best-performing ants deposit additional pheromone along their paths, reinforcing promising feature selections and splits.
*  Termination Criterion: The algorithm iterates until a predefined termination criterion is met, such as a maximum number of iterations or a satisfactory level of convergence.
  
## Advantages of ACDT
### 1. Exploration and Exploitation
The probabilistic nature of the ant movements allows for both exploration of new regions in the feature space and exploitation of promising areas, balancing the search between diversification and intensification.
### 2. Paralelization
The algorithm is inherently parallel, as multiple ants can construct decision trees concurrently, making it suitable for efficient implementation on modern computing architectures.
### 3. Robustness
The swarm-based approach and the pheromone update mechanism help the algorithm escape local optima and converge toward globally optimal or near-optimal solutions.
### 4. Interpretability
Like traditional decision trees, the models constructed by ACDT are inherently interpretable, making them suitable for applications where explainability is crucial, such as medical diagnosis, credit risk assessment, or decision support systems.
