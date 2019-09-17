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

### Descriptive Statistics

Descriptive statistics summarize a given data set, which can be either a representation of the entire or a sample of a population. It is broken down into measure of central tendency (mean, median & mode) and measure of variability (standard deviation, variance & skewness).

### Inferential Statistics

It is the process of using data analysis to deduce properties of an underlying probability distribution. Inferential statistical analysis infers properties of a population, for example by testing hypotheses and driving estimates. It is assumed that the observed data set is sampled from a larger population.
