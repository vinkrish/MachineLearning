### Questions Data Science Answers

1. Is it A or B? : Classfication algorithms
    - whether a coupon or discount bring more customer.
2. Is this weird? : Anomaly detection algorithms
    - credit card spending habit, flags unsual behaviour.
3. How much? How many? : Regression algorithms
    - what will my nth quarter sales be.
4. How is this organized? : Clustering algorithms
    - which viewers like same type of movies, which printer model fails same way.
5. What should I do now? : Reinforcement Learning algorithms
    - self driving car, whether to brake or accelerate at yellow light.

### Is data ready for Data Science

- Relevant?
- Connected?
- Accurate?
- Enough to work with?

### New model building workflow

1. Gather data
2. Feature extraction
3. Pick ML framework
4. Spin up AWS EC2 instance
5. Setup machine
6. Launch training job
7. Analyze results

When you have a standard computer, and you want to run multiple processes on it, the operating system is what deals with the scheduling - it determines which process gets access to which processor at a given point in time, which process gets access to which parts of memory, decides which processes should be frozen or die in cases where there is a shortage of resources.

Use **Docker** to containerize model development environment, setup code and dependencies on each remote machine.

**Kubernetes** is an open-source container-orchestration system for automating application deployment, scaling and management.

These tools allow for easy to use debugging and monitoring.

**Borg** is a Cluster OS Google uses for managing internal workloads. It manages thousands of machines with very good internal network connectivity. When you want to run a “service” - which is the equivalent of a “daemon” on a normal machine, something that should stay up all the time - you “run it on Borg” - that is, you tell the Borg cluster scheduler that you want, say, 200 copies of the binary that determines the service. The Borg scheduler identifies machines in the cluster that will have the spare capacity to run your service and sends a request to run the service to the node agents on these machines.

### Recommendation System

#### Collaborative Filtering

Collaborative filtering systems recommend items based on how well users prefer those items over others. It's based on crowdsourced user preference data.

Two approaches:

- User based: Systems that recommend items based on similarity between users. eg. customer who are similar to you like x,y,z products so you might like this as well.
- Item based: Items recommended to you - people who like this product also like x,y,z product. Generate recommendation based on similarity between items with respect to user ratings or purchase history.

#### Content Based Recommenders

Content-based recommenders recommend items based on their features and how similar those are to features of other items in a dataset. eg: Pandora uses this for music recommendation.

#### Popularity Based Recommenders

Popularity-based recommenders offer a very primitive form of collaborative filtering, where items are recommended to users based on how popular those items are among other users.

- Rely on purchase history data
- Used by online news sites
- Cannot produce personlized results

#### Correlation Based Recommendations

Use Pearson's _r_ correlation to recommend an item that is most similar to the item a user has already purchased. Recommend an item based on how well it correlates with other items with respect to use ratings.
