Temporal Difference (TD) Method start by focusing on the policy evaluation or prediction problem, the problem of estimating the value function \(v_\pi\) for a given policy \(\pi\). For the control problem (finding an optimal policy), DP, TD, and Monte Carlo methods all use some variation of _generalized policy iteration (GPI)_.

### TD Prediction

Both TD and Monte Carlo methods use experience to solve the prediction problem. Given some experience following a policy \(\pi\), both methods update their estimate \(V\) of \(v_\pi\) for the nonterminal states \(S_t\) occurring in that experience.

Roughly speaking, Monte Carlo methods wait until the return following the visit is known, then use that return as a
target for \(V(S_t)\). A simple every-visit Monte Carlo method suitable for nonstationary environments is

\(V(S_t) \leftarrow V(S_t) + \alpha [G_t - V(S_t)]\)

where \(G_t\) is the actual return following time \(t\), and \(\alpha\) is a constant step-size parameter.

Whereas Monte Carlo methods must wait until the end of the episode to determine the increment to \(V(S_t)\) (only then is
\(G_t\) known), TD methods need to wait only until the next time step. At time \(t + 1\) they immediately form a target and make a useful update using the observed reward \(R_{t+1}\) and the estimate \(V(S_{t+1})\). The simplest TD method makes the update

\(V(S_t) \leftarrow V(S_t) + \alpha [R_{t+1} + \gamma V(S_{t+1}) - V(S_t)]\)

immediately on transition to \(S_{t+1}\) and receiving \(R_{t+1}\). In effect, the target for the Monte Carlo update is \(G_t\), whereas the target for the TD update is \(R_{t+1} + \gamma V(S_{t+1})\). This TD method is called _TD(0)_, or _one-step TD_,

![td-prediction](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/td-prediction.jpg)

TD(0) is guaranteed to converge to the true state-value function, as long as the step-size parameter \(\alpha\) is sufficiently small. If you recall, this was also the case for constant-\(\alpha\) MC prediction. However, TD(0) has some nice advantages:

- Whereas MC prediction must wait until the end of an episode to update the value function estimate, TD prediction methods update the value function after every time step. Similarly, TD prediction methods work for continuous and episodic tasks, while MC prediction can only be applied to episodic tasks.

### sarsa

![sarsa](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/sarsa.jpg)

Sarsa(0) is guaranteed to converge to the optimal action-value function, as long as the step-size parameter \(\alpha\) is sufficiently small, and the Greedy in the Limit with Infinite Exploration (GLIE) conditions are met. Although there are many ways to satisfy the GLIE conditions, one method involves gradually decaying the value of \(\epsilon\) when constructing \(\epsilon\)-greedy policies.

In particular, let \(\epsilon_i\) correspond to the \(i\)-th time step. Then, if we set \(\epsilon_i\) such that:
- \(\epsilon_i>0\) for all time steps \(i\), and
- \(\epsilon_i\) decays to zero in the limit as the time step \(i\) approaches infinity (that is, \(\lim_{i\to\infty} \epsilon_i = 0\)),

then the algorithm is guaranteed to yield a good estimate for \(q_*\), as long as we run the algorithm for long enough. A corresponding optimal policy \(\pi_*\) can then be quickly obtained by setting \(\pi_*(s) = \arg\max_{a\in\mathcal{A}(s)} q_*(s, a)\) for all \(s\in\mathcal{S}\).

### Sarsamax

![sarsamax](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/sarsamax.jpg)

Sarsamax is guaranteed to converge under the same conditions that guarantee convergence of Sarsa.

### Expected Sarsa

![expected-sarsa](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/expected-sarsa.jpg)

Expected Sarsa is guaranteed to converge under the same conditions that guarantee convergence of Sarsa and Sarsamax.

Remember that theoretically, the as long as the step-size parameter \(\alpha\) is sufficiently small, and the Greedy in the Limit with Infinite Exploration (GLIE) conditions are met, the agent is guaranteed to eventually discover the optimal action-value function (and an associated optimal policy). However, in practice, for all of the algorithms we have discussed, it is common to completely ignore these conditions and still discover an optimal policy. You can see an example of this in the solution notebook.

### Analyzing Performance

All of the TD control algorithms we have examined (Sarsa, Sarsamax, Expected Sarsa) converge to the optimal action-value function \(q_*\) (and so yield the optimal policy \(\pi_*\)) if (1) the value of \epsilonϵ decays in accordance with the GLIE conditions, and (2) the step-size parameter \(\alpha\) is sufficiently small.

The differences between these algorithms are summarized below:

- Sarsa and Expected Sarsa are both on-policy TD control algorithms. In this case, the same (\epsilonϵ-greedy) policy that is evaluated and improved is also used to select actions.
- Sarsamax is an off-policy method, where the (greedy) policy that is evaluated and improved is different from the (\epsilonϵ-greedy) policy that is used to select actions
- On-policy TD control methods (like Expected Sarsa and Sarsa) have better online performance than off-policy TD control methods (like Sarsamax).
- Expected Sarsa generally achieves better performance than Sarsa.
