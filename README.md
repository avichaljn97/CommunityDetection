# Experiments and Results
This section shows the statistics of network, results of the implementation of the algorithm and the experiments done. We will discuss the results of Zachary Karate Club in detail, seeing the communities and how they are derived at each step. The idea is to show how the algorithm works, showing the processing and results for each iteration of the algorithm. 
For the other networks, we will only the final partition and results. 
# 4.1 Zachary’s Karate Club
![karatekid](https://user-images.githubusercontent.com/56877090/125959443-6a84d373-8304-4229-8fde-9dcebdcd89a3.JPG)


When it comes to social network analysis, ZKC is perhaps the most well known example. Therefore, it is important to discuss the background of this popular network.

It was introduced by Wayne Zachary in the paper "An Information Flow Model for Conflict and Fission in Small Groups" in 1977 and has been a popular example ever since. It is important to note that the network became a popular example of community structure after its use by Michelle Girvan and Mark Newman in 2002.

The network models the relationships between 34 members of a karate club: each node representing an individual, and the edges documenting links between pairs of members who interacted outside the club.

The story goes that a conflict arose between the administrator "John A" and instructor "Mr. Hi" (pseudonyms) because of the course price, which led to the split of the club into two. John A is represented by node 33(Red) and Mr. Hi by node 0(Green). Half of the members formed a new club around Mr. Hi; members from the other part found a new instructor or gave up karate.

One might expect that each member's decision to join either group would be driven by their relationships with the other members of the club. Based on collected data, Zachary correctly assigned all but one member of the club to the groups they actually joined after the split.

We will be using this network for understanding our algorithm, which is already included in networkx. 

## 4.1.1 Data Statistics
We should now look at the important statistics of Zachary Karate Club in order to uunderstand the network better.

![stat1](https://user-images.githubusercontent.com/56877090/125960732-c1d3a3e0-50ad-44fe-ac94-4ce9f58be343.JPG)

![stat2](https://user-images.githubusercontent.com/56877090/126037861-08cbe220-e178-4d07-a7e8-3207cc94f07b.JPG)

Degree Distribution - Majority of the members of the club do not have high degrees, i.e. do not have many links, mostly have up to 4. A few nodes have high degrees, which correspond to Mr.Hi and John A.

![stat3](https://user-images.githubusercontent.com/56877090/126037905-42c7615e-7769-4d82-8ce7-416495984bb4.JPG)

The value of average clustering coefficient is good here. A low value of the clustering coefficient would have indicated the presence of a structural hole, which would mean that a node is located on the outside of a cluster.

Centrality Measures of the nodes.

![stat4](https://user-images.githubusercontent.com/56877090/126037946-e2ba89ed-cb65-4aa0-b22d-feed629a5ff4.JPG)

## 4.1.2 Implementation Results for ZKC

Nodes of the graph:
1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29,30, 31, 32, 33

Edges of the graph:
(0, 1) (0, 2) (0, 3) (0, 4) (0, 5) (0, 6) (0, 7) (0, 8) (0, 10) (0, 11) (0, 12) (0, 13) (0, 17) (0, 19) (0, 21) (0, 31) (1, 2) (1, 3) (1, 7) (1, 13) (1, 17) (1, 19) (1, 21) (1, 30) (2, 3) (2, 7) (2, 8) (2, 9) (2, 13) (2, 27) (2, 28) (2, 32) (3, 7) (3, 12) (3, 13) (4, 6) (4, 10) (5, 6) (5, 10) (5, 16) (6, 16) (8, 30) (8, 32) (8, 33) (9, 33) (13, 33) (14, 32) (14, 33) (15, 32) (15, 33) (18, 32) (18, 33) (19, 33) (20, 32) (20, 33) (22, 32) (22, 33) (23, 25) (23, 27) (23, 29) (23, 32) (23, 33) (24, 25) (24, 27) (24, 31) (25,31) (26, 29) (26, 33) (27, 33) (28, 31) (28, 33) (29, 32) (29, 33) (30, 32) (30, 33) (31, 32) (31, 33) (32, 33)

### Level 1

Edge removed with betweenness centrality:  ((0, 31), 0.1272599949070537)
Edge removed with betweenness centrality:  ((0, 6), 0.07813428401663695)
Edge removed with betweenness centrality:  ((0, 5), 0.07813428401663694)
Edge removed with betweenness centrality:  ((0, 2), 0.0777876807288572)
Edge removed with betweenness centrality:  ((0, 8), 0.07423959482783014)
Edge removed with betweenness centrality:  ((2, 32), 0.06898678663384543)
Edge removed with betweenness centrality:  ((13, 33), 0.06782389723566191)
Edge removed with betweenness centrality:  ((19, 33), 0.05938233879410351)
Edge removed with betweenness centrality:  ((0, 11), 0.058823529411764705)

*Observation: The degree of node 11 is very low, i.e. 1. This might mislead one into thinking that the EBC value for the edge incident on this node must be low, since this edge would not fall in any of the shortest paths for some other node. But the EBC value for this edge (0,11) turns out to be high. This is because this edge would be a part of every single shortest path from a node to 11.*

After removal of edge (0, 11)

![karate_lvl1](https://user-images.githubusercontent.com/56877090/126038052-2dc5a413-65b1-4144-80c8-bdb3d80b70fb.JPG)

**Modularity of graph:** -8.21827744905179e-05

### Level 2

Edge removed with betweenness centrality:  ((1, 30), 0.2509665103415103)
Edge removed with betweenness centrality:  ((0, 1), 0.16572495791245792)
Edge removed with betweenness centrality:  ((30, 33), 0.1371625481000481)
Edge removed with betweenness centrality:  ((0, 10), 0.13257575757575757)
Edge removed with betweenness centrality:  ((0, 4), 0.13257575757575757)

Number of components in the partition:  3

![karate_lvl2](https://user-images.githubusercontent.com/56877090/126038255-6babf7fc-257c-4497-b5f2-58de43dc8792.JPG)

**Modularity of graph:**  0.13141025641025628

### Level 3

Removing edges from component 1...
Edge removed with betweenness centrality:  ((1, 2), 0.20105820105820105)
Edge removed with betweenness centrality:  ((2, 8), 0.16115520282186946)
Edge removed with betweenness centrality:  ((2, 27), 0.15167548500881833)
Edge removed with betweenness centrality:  ((2, 3), 0.11728395061728389)
Edge removed with betweenness centrality:  ((2, 28), 0.11044973544973546)
Edge removed with betweenness centrality:  ((9, 33), 0.08333333333333331)

Removing edges from component2...
Edge removed with betweenness centrality:  ((5, 10), 0.30000000000000004)
Edge removed with betweenness centrality:  ((4, 6), 0.30000000000000004)

Number of components in the partition:  5

![karate_lvl3](https://user-images.githubusercontent.com/56877090/126038319-4c6a3042-f857-41d0-9327-e38f71f33ee4.JPG)

**Modularity of graph:**  0.3735207100591716

### Level 4

Removing edges from component1...
Edge removed with betweenness centrality:  ((2, 9), 0.18181818181818182)

Removing edges from component2...
Edge removed with betweenness centrality:  ((27, 33), 0.10563725490196078)
Edge removed with betweenness centrality:  ((30, 32), 0.09926470588235294)
Edge removed with betweenness centrality:  ((31, 32), 0.09828431372549018)
Edge removed with betweenness centrality:  ((26, 33), 0.09803921568627451)
Edge removed with betweenness centrality:  ((28, 33), 0.08946078431372549)
Edge removed with betweenness centrality:  ((31, 33), 0.08725490196078431)
Edge removed with betweenness centrality:  ((8, 33), 0.0784313725490196)
Edge removed with betweenness centrality:  ((24, 31), 0.07279411764705883)
Edge removed with betweenness centrality:  ((22, 33), 0.06740196078431372)
Edge removed with betweenness centrality:  ((20, 33), 0.06740196078431372)
Edge removed with betweenness centrality:  ((18, 33), 0.06740196078431372)
Edge removed with betweenness centrality:  ((15, 33), 0.06740196078431372)
Edge removed with betweenness centrality:  ((14, 33), 0.06740196078431372)
Edge removed with betweenness centrality:  ((23, 25), 0.0639705882352941)
Edge removed with betweenness centrality:  ((23, 32), 0.06372549019607844)
Edge removed with betweenness centrality:  ((23, 33), 0.06004901960784313)
Edge removed with betweenness centrality:  ((25, 31), 0.05269607843137255)

Removing edges from component3...
Edge removed with betweenness centrality:  ((10, 4), 1.0)

Removing edges from component4...
Edge removed with betweenness centrality:  ((6, 16), 0.3333333333333333)
Edge removed with betweenness centrality:  ((5, 16), 0.3333333333333333)

Number of components in the partition:  9
Modularity of graph:  0.32092373438527283

*Observation: At this level, the modularity becomes less than the previous value, so we discard this partition and take the previous partition as final partition. Thus the final partition has 5 components.

The graph shows the modularity values at every level.

![stat5](https://user-images.githubusercontent.com/56877090/126038388-a45c36d1-d1f8-4705-af9d-f3fa40c42902.JPG)

The partitioning can be understood better with the following figure.

![flow](https://user-images.githubusercontent.com/56877090/126038439-95c99268-a783-4814-8b3f-d7093a72c303.jpg)

Results for Improvised Algorithm

![karateclub_algo2](https://user-images.githubusercontent.com/56877090/126038572-1681e662-a649-49ba-89f6-541196a7220d.JPG)

