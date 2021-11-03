# Model-free Prediction

## Introduction to lecture

| Framework           | Posible actions | State                | Model                              |
| ------------------- | --------------- | -------------------- | ---------------------------------- |
| Bandits             | Multiple        | One                  | No model                           |
| Dynamic programming | Multiple        | Sequential Structure | Given                              |
| Now                 | Multiple        | Sequential Structure | Not given, obtained by interaction |

- We're dont have an explicit MDP but we can interact with it and in that way is that we learn the optimal behavior
- This lecture is about model free prediction to estimate values in an unknown MDP

## Monte Carlo Algorithms

> Monte carlo means that we sample complete episodes of the problem.

#### Bandits with states 

Consider bandits with different states: Episodes are still one step and as a consequence actions do not affect state transitions and there aren't long term consequences.

#### Value function Approximation

Until now we've considered lookup tables where every state $s$ has an entry $v(s)$, this is a problem for larger MDPS where this could overflow memory, increase the runtime or simply not tractable. 

Our solution for this problems is to use function approximation where:
$$
v_w(s) \approx v_\pi(s) \\
q_w(s,a) \approx q_\pi(s,a)
$$
Where $w$ is a parameter that will be updated using MC or some other technique. Ideally this function should generalise to unseen states.

#### Agent state update

If the environment state is not fully observable we'll consider the agent state as follows:
$$
S_t = u_\omega(S_{t-1}, A_{t-1}, O_t)
$$
For now we won't talk about how to learn the agent state update

#### Linear function approximation

Consider the following feature vector
$$
x(s) = \begin{pmatrix} x_1(s) \\ ... \\ x_m(s) \end{pmatrix}
$$
where $x(S_t) = x(s)$ is a fixed mapping from the agent state to features.

Then, the approximate value function is given by:
$$
v_w(s) = w^\top x(s) = \sum_{j=1}^n x_j(s)w_j
$$
And the objective function is:
$$
L(w) = \mathbb{E}_{S \sim d}[(v_\pi(S) - v_w(s))^2]
$$


###### Observation

The table lookup we made with bandits is a special case of linear value function approximation





















