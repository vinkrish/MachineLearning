- **Iterative policy evaluation** is an algorithm used in the dynamic programming setting to estimate the state-value function \(v_\pi\) corresponding to a policy \(\pi\). In this approach, a Bellman update is applied to the value function estimate until the changes to the estimate are nearly imperceptible.

- **Estimation of Action Values**: In the dynamic programming setting, it is possible to quickly obtain the action-value function \(q_\pi\) from the state-value function \(v_\pi\)

- **Policy improvement** takes an estimate \(V\) of the action-value function \(v_\pi\) corresponding to a policy \(\pi\), and returns an improved (or equivalent) policy \(\pi'\), where \(\pi'\geq\pi\). The algorithm first constructs the action-value function estimate \(Q\). Then, for each state \(s\in\mathcal{S}\), you need only select the action \(a\) that maximizes \(Q(s,a)\). In other words, \(\pi'(s) = \arg\max_{a\in\mathcal{A}(s)}Q(s,a)\) for all \(s\in\mathcal{S}\)

- **Policy iteration** is an algorithm that can solve an MDP in the dynamic programming setting. It proceeds as a sequence of policy evaluation and improvement steps, and is guaranteed to converge to the optimal policy (for an arbitrary finite MDP).

- **Truncated policy iteration** is an algorithm used in the dynamic programming setting to estimate the state-value function \(v_\pi\) corresponding to a policy \(\pi\). In this approach, the evaluation step is stopped after a fixed number of sweeps through the state space. We refer to the algorithm in the evaluation step as truncated policy evaluation.

- **Value iteration** is an algorithm used in the dynamic programming setting to estimate the state-value function \(v_\pi\) corresponding to a policy \(\pi\). In this approach, each sweep over the state space simultaneously performs policy evaluation and policy improvement.
