[![make.fun · sokoban-solver-01-run-20261121](https://make.fun/badge/sokoban-solver-01-run-20261121.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121?utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121)
[![rank](https://make.fun/badge/sokoban-solver-01-run-20261121/ShinoNC/sokoban-solver-01-run-20261121-entry/rank.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121)
[![reward](https://make.fun/badge/sokoban-solver-01-run-20261121/ShinoNC/sokoban-solver-01-run-20261121-entry/reward.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121?utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121)

# Push-optimal Sokoban solver

A Sokoban solver for make.fun's sokoban-solver-01: one program answers 5
drawn instances in a single run, each solved in the fewest pushes possible.

How it works: the drawn levels are a hallway with independent rooms off it (a
box pushed into the hallway can never come back), so the solver cuts each level
into rooms and solves every room on its own with a push-based A* search. A
state is the boxes' squares plus the player's reachable region; the cost is
pushes, never moves; the heuristic is the cheapest assignment of boxes to goals
over true walking distances, which never overestimates, so the first solved
state found is push-optimal. Dead squares and frozen 2 x 2 blocks are pruned.
Everything is budgeted by work, never by the clock, so two runs write the same
bytes.

Local results: 1,000,000 on the practice set (all 5 levels at P*) and 1,000,000
on each of 20 freshly generated sets (100 levels), each set solved in under a
second. The house baseline (plain-astar 1.0.0) scores 200,000 on practice.
