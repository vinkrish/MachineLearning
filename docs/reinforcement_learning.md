# Reinforcement Learning

![reinforce_learning](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/reinforce_learning.png)

## The Setting, Revisited

- The reinforcement learning (RL) framework is characterized by an **agent** learning to interact with its **environment**.
- At each time step, the agent receives the environment's **state** (the environment presents a situation to the agent), and the agent must choose an appropriate **action** in response. One time step later, the agent receives a **reward** (the environment indicates whether the agent has responded appropriately to the state) and a new state.
- All agents have the goal to maximize expected **cumulative reward**, or the expected sum of rewards attained over all time steps.

## Episodic vs. Continuing Tasks

- A **task** is an instance of the reinforcement learning (RL) problem.
- **Continuing tasks** are tasks that continue forever, without end.
- **Episodic tasks** are tasks with a well-defined starting and ending point.
    - In this case, we refer to a complete sequence of interaction, from start to finish, as an episode.
    - Episodic tasks come to an end whenever the agent reaches a terminal state.

## The Reward Hypothesis

- **Reward Hypothesis**: All goals can be framed as the maximization of (expected) cumulative reward.

## Cumulative Reward

The return at time step t is $$G_t := R_{t+1} + R_{t+2} + R_{t+3} + \ldots$$
The agent selects actions with the goal of maximizing expected (discounted) return.

## Discounted Return

- The discounted return at time step t is $$G_t := R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \ldots$$
- The discount rate \(\gamma\) is something that you set, to refine the goal that you have the agent.
    - It must satisfy 0 <= \(\gamma\) <= 1
    - If \(\gamma=0\), the agent only cares about the most immediate reward.
    - If \(\gamma=1\), the return is not discounted.
    - For larger values of \(\gamma\), the agent cares more about the distant future. Smaller values of \(\gamma\) result in more extreme discounting, where - in the most extreme case - agent only cares about the most immediate reward.

## MDPs and One-Step Dynamics

- The **state space** \(\mathcal{S}\) is the set of all (nonterminal) states.
- In episodic tasks, we use \(\mathcal{S}^+\) to refer to the set of all states, including terminal states.
- The **action space** \(\mathcal{A}\) is the set of possible actions. (Alternatively, \(\mathcal{A(s)}\) refers to the set of possible actions available in state \(s \in (\mathcal{S}\)
- The **one-step dynamics** of the environment determine how the environment decides the state and reward at every time step. The dynamics can be defined by specifying

$$p(s',r|s,a) \doteq \mathbb{P}(S_{t+1}=s', R_{t+1}=r|S_{t} = s, A_{t}=a) \text{ for each possible } s', r, s, \text{and } a$$

- A **(finite) Markov Decision Process (MDP)** is defined by:
    - a (finite) set of states \(\mathcal{S}\) (or \(\mathcal{S}^+\), in the case of an episodic task)
    - a (finite) set of actions \(\mathcal{A}\)
    - a set of rewards \(\mathcal{R}\)
    - the one-step dynamics of the environment
    - the discount rate \(\gamma \in [0,1]\)

## Bellman Equations

In this gridworld example, once the agent selects an action,

- it always moves in the chosen direction (contrasting general MDPs where the agent doesn't always have complete control over what the next state will be), and
- the reward can be predicted with complete certainty (contrasting general MDPs where the reward is a random draw from a probability distribution).

In this simple example, we saw that the value of any state can be calculated as the sum of the immediate reward and the (discounted) value of the next state.

Alexis mentioned that for a general MDP, we have to instead work in terms of an expectation, since it's not often the case that the immediate reward and next state can be predicted with certainty. Indeed, we saw in an earlier lesson that the reward and next state are chosen according to the one-step dynamics of the MDP. In this case, where the reward _r_ and next state _s′_ are drawn from a (conditional) probability distribution \(p(s',r|s,a)\), the **Bellman Expectation Equation** (for \(v_\pi)\) expresses the value of any state _s_ in terms of the expected immediate reward and the expected value of the next state:

$$v_\pi(s) = \mathbb{E}_\pi[R_{t+1} + \gamma v_\pi(S_{t+1})|S_t =s]$$

## Calculating the Expectation

In the event that the agent's policy π is **deterministic**, the agent selects action _π(s)_ when in state _s_, and the Bellman Expectation Equation can be rewritten as the sum over two variables (_s′_ and _r_):

$$v_\pi(s) = \text{} \sum_{s'\in\mathcal{S}^+, r\in\mathcal{R}}p(s',r|s,\pi(s))(r+\gamma v_\pi(s'))$$

In this case, we multiply the sum of the reward and discounted value of the next state \((r+\gamma v_\pi(s'))\) by its corresponding probability \(p(s',r|s,\pi(s))\) and sum over all possibilities to yield the expected value.

If the agent's policy π is **stochastic**, the agent selects action _a_ with probability _π(a∣s)_ when in state _s_, and the Bellman Expectation Equation can be rewritten as the sum over three variables \((s′, r, and a)\):

$$v_\pi(s) = \text{} \sum_{s'\in\mathcal{S}^+, r\in\mathcal{R},a\in\mathcal{A}(s)}\pi(a|s)p(s',r|s,a)(r+\gamma v_\pi(s'))$$

In this case, we multiply the sum of the reward and discounted value of the next state \((r+\gamma v_\pi(s'))\) by its corresponding probability \(π(a∣s)p(s′,r∣s,a)\) and sum over all possibilities to yield the expected value.

## Policies

- A **deterministic** policy is a mapping \(\pi: \mathcal{S}\to\mathcal{A}\). For each state s ∈ S, it yields the action a ∈ A that the agent will choose while in state _s_.

- A **stochastic policy** is a mapping \(\pi: \mathcal{S}\times\mathcal{A}\to [0,1]\). For each state s ∈ S and action a ∈ A, it yields the probability \(\pi(a|s)\) that the agent chooses action _a_ while in state _s_.

## State-Value Functions

- The state-value function for a policy π is denoted \(v_\pi\). For each state s ∈ S, it yields the expected return if the agent starts in state _s_ and then uses the policy to choose its actions for all time steps. That is,

$$v_\pi(s) \doteq \text{} \mathbb{E}_\pi[G_t | S_t=s]$$
We refer to \(v_\pi(s)\) as the **value of state** _s_ **under policy** π.

- The notation \(\mathbb{E}_\pi[\cdot]\) is borrowed from the suggested textbook, where \(\mathbb{E}_\pi[\cdot]\) is defined as the expected value of a random variable, given that the agent follows policy π.

## Optimality

- A policy π′ is defined to be better than or equal to a policy π if and only if \(v_{\pi'}(s) \geq v_\pi(s)\) for all s ∈ S.

- An **optimal policy** \(\pi_*\) satisfies \(\pi_*\ge\pi\) for all policies π. An optimal policy is guaranteed to exist but may not be unique.
- All optimal policies have the same state-value function \(v_*\) called the **optimal state-value function**.

## Action-Value Functions

- The **action-value function** for a policy π is denoted \(q_\pi\). For each state s ∈ S and action a ∈ A, it yields the expected return if the agent starts in state _s_, takes action _a_, and then follows the policy for all future time steps. That is, 

$$q_\pi(s,a) \doteq \mathbb{E}_\pi[G_t|S_t=s, A_t=a]$$

We refer \(q_\pi(s,a)\) as the **value of taking action** _a_ **in state** _s_ **under a policy** π (or alternatively as the value of the state-action pair _s_,_a_).

- All optimal policies have the same action-value function \(q_*\), called the **optimal action-value function**.

## Optimal Policies

- Once the agent determines the optimal action-value function \(q_*\), it can quickly obtain an optimal policy \(\pi_*\) by setting:

$$\pi_*(s) = \arg\max_{a\in\mathcal{A}(s)} q_*(s,a)$$
