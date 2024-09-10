# POLICY ITERATION ALGORITHM

## AIM
Write the experiment AIM.

## PROBLEM STATEMENT
Explain the problem statement.

## POLICY ITERATION ALGORITHM
Include the steps involved in policy iteration algorithm

## POLICY IMPROVEMENT FUNCTION
### Name: Sriram G
### Register Number: 212222230149

```
def policy_improvement(V,P, gamma = 1.0):
  Q = np.zeros((len(P),len(P[0])),dtype = np.float64)
  for s in range(len(P)):
    for a in range(len(P[s])):
      for prob,next_state,reward,done in P[s][a]:
         Q[s][a]+=prob*(reward+gamma*V[next_state]*(not done))

  new_pi = lambda s: {s:a for s,a in enumerate(np.argmax(Q,axis=1))}[s]

  return new_pi
```

## POLICY ITERATION FUNCTION
### Name : Sriram G
### Register Number: 212222230149

```
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions = np.random.choice(tuple(P[0].keys()),len(P))
  pi = lambda s: {s:a for s,a in enumerate(random_actions)}[s]

  while True:
    old_pi = {s:pi(s) for s in range(len(P))}
    V = policy_evaluation(pi,P,gamma,theta)
    pi = policy_improvement(V,P,gamma)

    if old_pi == {s:pi(s) for s in range(len(P))}:
      break
  return V,pi
```

## OUTPUT:



## RESULT:

Write your result here
