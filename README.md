### DEVELOPED BY : SANJAY T
### REG NO :  212222110039
### DATE : 

# MDP REPRESENTATION

## AIM:
To represent any one real-world problem in MDP form.

## PROBLEM STATEMENT:

### Problem Description
Design a strategy for a volleyball team to maximize their chances of winning a match. The goal is to optimize team positioning, actions (like serving, spiking, blocking), and decision-making based on the opposing team’s strategy.

### State Space
Define the state space, representing all possible configurations of the game, including player positions, ball location, and score.

### Sample State
1 . Player positions: Player A at front left, Player B at front center, etc.

2 . Ball position: Mid-court, in the air after an opponent's spike.

3 . Score: 15-12 in favor of the opposing team.

### Action Space
The action space consists of the following actions:

1 . Serve to a specific area of the opponent’s court.

2 . Spike the ball.

3 . Block an opponent’s spike.

4 . Rotate positions on the court.

### Sample Action
A sample action could be :

Player A spikes the ball to the back right corner of the opponent’s court.
### Reward Function
The reward function might be:

1 . 1 point for scoring a point.

2 . 0 point for losing a point.

### Graphical Representation

![WhatsApp Image 2024-09-03 at 16 07 54_7da8e8f5](https://github.com/user-attachments/assets/3c3b911e-f63c-4ecb-952f-d7a55fbfee95)



## PYTHON REPRESENTATION:

mdp = {
    # State 0: Initial state, game is at 15-12, team is receiving a serve
     0:{  
        # Action 1: Attempt a block on opponent's spike
        1: [(0.7, 1, 1.0, False),  # 70% chance to successfully block and move to state 1
            (0.3, 2, 0.0, False)], # 30% chance to fail the block, opponent scores, move to state 2

        # Action 0: Attempt a dig (defensive play) to return the spike
        0: [(0.8, 3, 0.0, False),  # 80% chance to successfully dig and return the ball, move to state 3
            (0.2, 2, 0.0, False)]  # 20% chance to miss the dig, opponent scores, move to state 2
    },
     1:{  
        # Action 1: Attempt to spike the ball
        1: [(0.7, 1, 1.0, False),  # 70% chance to spike successfully and score, move to state 1
            (0.3, 2, 0.0, False)], # 30% chance of a spike failure, opponent scores, move to state 2

        # Action 0: Set up for another attack
        0: [(1.0, 3, 0.0, False)]  # 100% chance to stay in the current rally state (more conservative play)
    },
    2:{  
        1: [(1.0, 7, 1.0, True)],  # Terminal state: match over, win
        0: [(1.0, 7, 0.0, True)]   # Terminal state: match over, win
    }
}


## OUTPUT:
![image](https://github.com/user-attachments/assets/9e3e117c-7f5e-4c52-bd6e-bc456a97f18a)


## RESULT:
Thus the given real world problem is successfully represented in a MDP form.
