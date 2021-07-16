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

# 4.1.1 Data Statistics
We should now look at the important statistics of Zachary Karate Club in order to uunderstand the network better.

![stat1](https://user-images.githubusercontent.com/56877090/125960732-c1d3a3e0-50ad-44fe-ac94-4ce9f58be343.JPG)
