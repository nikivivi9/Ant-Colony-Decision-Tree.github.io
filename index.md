---
layout: default
title: Ant Colony Decision Tree
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script type="text/javascript">
    MathJax = {
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        displayMath: [['$$', '$$'], ['\\[', '\\]']]
      },
      svg: {
        fontCache: 'global'
      }
    };
  </script>
  <script type="text/javascript" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
  </script>
</head>
<body>
<div class="container-fluid">
  <div class="row">
    <nav id="sidebar" class="col-md-3 col-lg-2 d-md-block bg-light sidebar">
      <div class="sidebar-sticky">
        <ul class="nav flex-column">
          <li class="nav-item">
            <a class="nav-link active" href="#decision-trees">Decision Trees</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#ant-colony-optimization">Ant Colony Optimization (ACO)</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#ant-colony-decision-trees">Ant Colony Decision Trees (ACDT)</a>
          </li>
        </ul>
      </div>
    </nav>

    <main role="main" class="col-md-9 ml-sm-auto col-lg-10 px-md-4">
      <div id="decision-trees">
        <h2>Decision Trees</h2>
        <!-- A decision tree is a non-parametric supervised learning algorithm for classification and regression tasks. It has a hierarchical tree structure consisting of a root node, decision nodes, edges, and leaf nodes. It follows an iterative top-down procedure of selecting the best attribute to label an decision node of the tree. It starts at the root node that contains the entire sample, then splits at the decision node that serves as the test condition, and ends at the leaf node that is the final prediction result (Figure 1). This basic approach represents a greedy strategy to create a decision tree since the selection of an attribute at early iterations cannot be reconsidered at later iterations. i.e., the selection of the best attribute is made locally at each iteration, without taking into consideration its influence over the subsequent iterations. However, the newly proposed ACDT algorithm is able to construct the decision tree in a top-down fashion by probabilistically selecting attributes to be added as decision nodes based on the amount of pheromone and heuristics information, with the pheromone values represent the quality of the connection between a parent and child decision nodes. -->
        <p align="center">
<img src="https://raw.githubusercontent.com/nikivivi9/Ant-Colony-Decision-Tree.github.io/ant/assets/DecisionTree.png" alt="Decision Tree Image" width="400" height="250">
<figcaption align="center"> Figure 1. Visualization of Decision Tree </figcaption>
      </div>

      <div id="ant-colony-optimization">
        <h2>Ant Colony Optimization (ACO)</h2>
        <!-- Ant colony optimization (ACO)  technique is inspired by the foraging behavior of ant colonies.  The intelligent behavior of ant colonies is achieved by making small changes to the environment (i.e., leaving pheromones) in order to communicate indirectly with each other to accomplish complex tasks. When ants leave their colony in search of food, they explore various potential paths from their nest to the targeted food source. Each ant leaves behind a pheromone trail on its path. If a path is selected by multiple ants, it would collect a higher concentration of pheromone. Conversely, if there are no ants continuously following this path, the pheromone deposited by previous ants would evaporate. The concentration of pheromone on each path would affect the ant’s decision-making. Path with higher pheromone concentration would be more attractive for the following ants, whereas path with lower concentration of pheromone would be less likely to be chosen. Since ants would traverse shorter paths much quicker, shorter paths tend to gain higher pheromone concentration over time. Ultimately, ants are able to identify and converge to the optimal and shortest path from their nest to the food source.  The animation below is a visualization of the results of the ACO simulation, where the dots are the colonies and the gray lines are the paths that the ants traverse. The ants traverse between each colony on their own chosen path. As time goes, an optimal path is obtained, as shown by the solid black line. One can explore the simulation on their own by visiting this website. [ACO Visualisation](https://courses.cs.ut.ee/demos/visual-aco/#/visualisation "ACO Visualisation") -->
        <p align="center">
<img src="https://raw.githubusercontent.com/nikivivi9/Ant-Colony-Decision-Tree.github.io/ant/assets/ACOVisualization.gif" alt="ACO Image" width="300" height="250">
<figcaption align="center"> Figure 2. Simulation of ACO </figcaption>
<figcaption align="center"> Grey lines indicate the possible paths; Black line indicates the optimal path. </figcaption>
      </div>

      <div id="ant-colony-decision-trees">
        <h2>Ant Colony Decision Trees (ACDT)</h2>
        <!-- Based on the structure of the ACO algorithm, researchers have proposed applying it to decision tree modeling. As a result, a new metaheuristics approach based on ant colony algorithms, known as Ant Colony Decision Trees (ACDT), has been developed. Compared to the general decision tree algorithm, in ACDT,  each ant chooses the appropriate attribute for splitting in each decision node of the constructed decision tree according to the heuristic function and pheromone values. Following the logic of ACO, the algorithm for ACDT can be written as below. 

As can be seen in Figure 3, the algorithm starts by initializing the pheromone values and computing the heuristic information for each attribute of the training set. Then, it enters an iterative for loop. In each iteration, an ant in the colony creates a new decision tree until the maximum number of iterations is reached. 

Each ant creates a decision tree (for loop) in a top-down fashion by probabilistically selecting attributes to be added as decision nodes based on the amount of pheromone and heuristic information. The procedure for creating a decision tree (CreateTree procedure) involves three parameters: the collection of training examples, the predictor attributes, and the edge that the ant is following, which initially corresponds to the default edge (indicated by the symbol '-'). Once the tree construction procedure has finished, the created tree is pruned in order to simplify the tree and thus potentially avoid overfitting the model to the training data. 

After the pruning, the tree is evaluated and if the quality of the newly pruned tree surpasses the quality of the existing iterative optimal tree, the iterative optimal tree (treeib) is updated. Finally, the iteration-best tree constructed by the ants is used to update the pheromone values, the global-best tree (treegb) is updated and a new iteration of the algorithm starts. When the maximum number of iterations is reached the global-best tree is returned as the discovered decision tree.
 -->
 <p align="center">
<img src="https://raw.githubusercontent.com/nikivivi9/Ant-Colony-Decision-Tree.github.io/ant/assets/ACDT_Code.png" alt="ACDT Image" width="500" height="400">
<figcaption align="center"> Figure 5. Pseudocode of ACDT </figcaption>
      </div>
    </main>
  </div>
</div>

<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.2/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</body>
</html>
