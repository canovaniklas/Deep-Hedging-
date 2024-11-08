# Deep-Hedging

## Project Overview

This repository demonstrates how to hedge a European call option using neural networks, an approach sometimes called “Deep Hedging.” We compare:

1) A collection of small networks, each acting at its own time step.
2) A single network that outputs the hedge ratio for any time/price pair.

We generate synthetic price paths under a simplified Black–Scholes model (with r=0) and then train our models to minimize the squared difference between the option payoff and the hedged portfolio outcome. We also compare against the Black–Scholes “Delta Hedge” strategy to see how close the learned strategies come to the theoretical solution—keeping in mind that discrete rebalancing and numerical noise can affect results.

## File Contents

1) Data Generation: Simulates geometric Brownian motion paths.

2) Multiple-Network Deep Hedging Model: Trains a separate neural network for each rebalancing date. Learns to predict the optimal hedge ratio at each step.

3) Single-Network Deep Hedging Model: Uses a single neural network that takes (t,St)(transformed appropriately) as input and outputs the hedge ratio for that time/price. Reduces the total number of parameters.

4) Comparison with Black–Scholes Delta Hedging: Evaluates how well each approach approximates the analytical hedge (and why discrepancies arise).



## Key Results
The multi-network model and the single-network model both achieve near-zero mean hedging losses in a simulated Black–Scholes market.The single-network approach has fewer parameters, training more efficiently while retaining comparable performance.The classic Black–Scholes hedge also performs similarly, though practical factors like discrete rebalancing and sampling noise lead to nonzero variance in all methods.
