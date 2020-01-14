# Deep Dyna-Q: Integrating Planning for Task-Completion Dialogue Policy Learning

### ACL 2018
Baolin Peng, Xiujun Li, Jianfeng Gao, Jingjing Liu, Kam-Fai Wong, Shang-Yu Su

## Core Ideas:
- DDQ: Dialogue Policy Learning via Deep Dyna-Q
  - An LSTM-Based NLU module and a state tracker for tracking the dialogue states.
  - A dialogue policy which selects the next action based on the current state. (RL)
  - Convert the dialogue actions to neural language response by a model-based NLG module.
  - A world model for generating simulated user actions and simulated rewards.
- Task-oriented, slot-filling, dialogues
  - Domain Knowledge: Movie, Restaurant, Dialogues

## Training 
3 Stage training:   
- Direct Reinforcement Learning
- World Model Learning
- Planning
!(https://github.com/peterzheng98/paper-reading/blob/master/NLP/pictures/a1.png?raw=true)