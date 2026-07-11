# AgonAlpha

AgonAlpha is an agent-based framework for automated alpha discovery. It follows the principles of [Prompt Economy](https://arxiv.org/abs/2606.08878).

## TODO

- [x] Integrate WorldQuant BRAIN
- [ ] Integrate vectorbt
- [ ] Integrate QuantConnect LEAN

## Quick Start

```
cd alphas
claude --plugin-dir .. --dangerously-skip-permissions --model claude-sonnet-5[1m]
# in claude code
/alpha-mcts 1
```
