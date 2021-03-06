# [WIP] Machine Learning Engineer Nanodegree
## Capstone Proposal
_(approx. 2-3 pages)_
_Alex Erfurt_  
_February 6th, 2020_
[Source of template](https://github.com/udacity/machine-learning/blob/master/projects/capstone/capstone_proposal_template.md)

### Domain Background
_(approx. 1-2 paragraphs)_

In this section, provide brief details on the background information of the domain from which the project is proposed. Historical information relevant to the project should be included. It should be clear how or why a problem in the domain can or should be solved. Related academic research should be appropriately cited in this section, including why that research is relevant. Additionally, a discussion of your personal motivation for investigating a particular problem in the domain is encouraged but not required.

DRAFT :
After some time of long and thoughtful research and considerations, I finally decided to build my capstone project in the domain of Reinforcement Learning. Reason is that I very much enjoyed the complexity & challenge of the previous project (Quadcopter), as much as I was also impressed by the results of creating an agent that actually learns in such a complex environment. Reinforcement Learning is clearly a crucial piece in the next wave of data science & machine learning. I knew I wanted to learn more about this field of AI, so I looked for resources to learn more (of which I can highly recommend [David Silver's lecture on RL](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html)) and ideas for hands-on practice incl. a capstone project topic. Due to my fascination of "solving" games through building intelligent agent that can reach super-human level, which is commonly used to train and test RL-algorithms on, I decided to try it myself and picked Connect4 (or sometimes called Four-in-A-Row) as a game that is challenging enough without being to simple either. Clearly, it's not like the game of Go considering the complexity, however, there are still more than [4.5 trillion game positions](https://medium.com/applied-data-science/how-to-build-your-own-alphazero-ai-using-python-and-keras-7f664945c188)! I believe that breaking down this sort of problem, learning various RL concepts more in depth and solving it to a certain degree will prepare you for various real-world problems that can be tackled with RL. Games are just a test environment that can help to understand learning algorithms and how they create abstract strategies without even knowing game rules. A real-world applications might be suprisingly similar to solve as some examples of Deepmind's world leading algorithms show - from making data centers more energy-efficient to predict protein folding faster and more accurate than any method before.
TODO: Include Deepmind research (paper)...

### Problem Statement
_(approx. 1 paragraph)_

In this section, clearly describe the problem that is to be solved. The problem described should be well defined and should have at least one relevant potential solution. Additionally, describe the problem thoroughly such that it is clear that the problem is quantifiable (the problem can be expressed in mathematical or logical terms) , measurable (the problem can be measured by some metric and clearly observed), and replicable (the problem can be reproduced and occurs more than once).

DRAFT:
In the game (environment) that we will use, our objective is to get a certain number of our checkers in a row horizontally, vertically, or diagonally on the game board before our opponent. When it's our turn, we “drop” one of our checkers into one of the columns at the top of the board. Then, let our opponent take their turn. This means each move may be trying to either score a win for us, or trying to stop our opponent from winning. The default number in Kaggle's environment is four-in-a-row, with the intent to have other options to come soon. However, for this work we are going to keep it at four.

With Kaggle's game environment it is possible to let two agent play against each other randomly, i.e. their moves (column to use) are picked completely randomly without any decision process and in disregard of the current game (state). If we let them play randomly for many games it will be ~50% of games won and lost. We want to change this! The problem that we solve is that our agent is not making decisions randomly but learns how to play the game without us explicitly stating the rules of the game. We will be able to measure that in the ration of how many games our smart agent wins against a randomly playing (i.e. not smart) opponent. We shall aim to achieve a ratio of >90% wins won out of at least a 100 games.

### Datasets and Inputs
_(approx. 2-3 paragraphs)_

In this section, the dataset(s) and/or input(s) being considered for the project should be thoroughly described, such as how they relate to the problem and why they should be used. Information such as how the dataset or input is (was) obtained, and the characteristics of the dataset or input, should be included with relevant references and citations as necessary It should be clear how the dataset(s) or input(s) will be used in the project and whether their use is appropriate given the context of the problem.

DRAFT:
For this particular problem there is no initial dataset used nor needed, since the agent uses Reinforcement Learning techniques to learn how to play Connect4.
The environment is provided by the Competitions' organizer Kaggle. More details around the environment rules can be found [here](https://www.kaggle.com/c/connectx/overview/environment-rules). Within the environment, an agent starts to interact with the game environment until the game is lost, won or a draw, which defines an episode. On a 6 (row) x 7 (column) game board, the episodes objective is to use the agent in order to get four of your checkers in a row horizontally, vertically, or diagonally before your opponent.
ToDo: Describe environment in more detail on its inputs and outpus (e.g. env.configuration...).

Deep Learning neural networks involved will be trained through data that is created through the agent's interaction with and exploration of the environment (self play). There, the environmental state after each step will be saved into a sort of memory for game experiences, a so called 'Replay Buffer'. This buffer will be used for training neural nets that learn to predict the moves that are most promising for maximising overall game rewards. ....

ToDo:
* add the [Connect4 Data Set](https://archive.ics.uci.edu/ml/datasets/Connect-4) from UC Irvine's Machine Learning Repository to test the DQN...

### Solution Statement
_(approx. 1 paragraph)_

In this section, clearly describe a solution to the problem. The solution should be applicable to the project domain and appropriate for the dataset(s) or input(s) given. Additionally, describe the solution thoroughly such that it is clear that the solution is quantifiable (the solution can be expressed in mathematical or logical terms) , measurable (the solution can be measured by some metric and clearly observed), and replicable (the solution can be reproduced and occurs more than once).

DRAFT:
* What techniques, what are their Inputs and Outputs...
In order to train the agent to play Connect4 successfully, we will use Reinforcement and Deep Learning techniques. To be more precise, Deep Q-Learning, a value-based Reinforcement Learning method will be used to identify actions an agent can take at each state. The underlying Deep Q-network (deep neural network) is going to learn to estimate not just any arbitrary action, but the best (optimal) action to take at certain states from within the environment in order to maximise overall rewards.

In a more formal way: we are going to build a DQN for a value-function approximation:
Q*(s,a)= maxQpi(....)...
Based on Bellman's Optimality Equation, this gives us the maximum sum of rewards by mapping states to actions.

### Benchmark Model
_(approximately 1-2 paragraphs)_

In this section, provide the details for a benchmark model or result that relates to the domain, problem statement, and intended solution. Ideally, the benchmark model or result contextualises existing methods or known information in the domain and problem given, which could then be objectively compared to the solution. Describe how the benchmark model or result is measurable (can be measured by some metric and clearly observed) with thorough detail.

DRAFT:
* Unlike the actual Competition on Kaggle, we are not going to enter into play against other people agents in order to get our agents strength assessed as this is an ongoing, active process within the competition (ladder game play against comparably strong agents in the ranking etc.). For this work, we are going to take the following approaches for benchmarking our agent:
* Performing against an algorithm who plays in an uniformly random manner. In the Kaggle environment this algorithm is called "random".
* A subsequent challenge, compete against an agent who plays according to the [Negamax](https://en.wikipedia.org/wiki/Negamax) search algorithm. The Kaggle environment provides an implementation for this algorithm as well called "negamax". TODO: explain negamax algorithm
* OPTIONAL: [Connect4 Data Set](https://archive.ics.uci.edu/ml/datasets/Connect-4) from UC Irvine's Machine Learning Repository...
* OPTIONAL: TicTacToe domination?

### Evaluation Metrics
_(approx. 1-2 paragraphs)_

In this section, propose at least one evaluation metric that can be used to quantify the performance of both the benchmark model and the solution model. The evaluation metric(s) you propose should be appropriate given the context of the data, the problem statement, and the intended solution. Describe how the evaluation metric(s) are derived and provide an example of their mathematical representations (if applicable). Complex evaluation metrics should be clearly defined and quantifiable (can be expressed in mathematical or logical terms).

DRAFT:
* Percentage of Won games against the Random (100%) as well as the Negamax Agent(>75%?)
* OPTIONAL: Predictive accuracy when compared with the Connect4 Data Set

### Project Design
_(approx. 1 page)_

In this final section, summarize a theoretical workflow for approaching a solution given the problem. Provide thorough discussion for what strategies you may consider employing, what analysis of the data might be required before being used, or which algorithms will be considered for your implementation. The workflow and discussion that you provide should align with the qualities of the previous sections. Additionally, you are encouraged to include small visualisations, pseudocode, or diagrams to aid in describing the project design, but it is not required. The discussion should clearly outline your intended workflow of the capstone project.

DRAFT:
1. The Programming Stack:
    * Python 3.7
    * Numpy
    * Keras / TF 2.1
2. The game environment specifications/ datasets:
    * Kaggle Environment - ToDo: Describe environment in more detail on its interface, inputs and outputs (e.g. env.configuration...).
    * Which classes are being used, e.g. Agent(), Game() etc..
3. The techniques and algorithms:
    * Reinforcement Learning algorithm:
    - Q-Learning, a model-free RL algorithm that doesn't require a model of the environment (hence the "model free"). Q-Learning is a value-based method, as such it can identify optimal state-action (Q) value pairs for any given state of a finite Markov Decision Process. The goal is to learn an optimal policy, which tells an agent in any current state which action to take in order to maximise the expected value of the total reward (Q-value) over all subsequent steps. The alternative implementation as "Double Q-Learning" is  considered an off-policy algorithm, i.e. the policy that is learned is a different one from the actual action selection policy. This solves the overestimation issue (for action values) which usually slows the learning.
    - Combining this with Deep Learning, we will get the Double Deep Q-Network algorithm which we are going to use in this work.
    TODO: show formula of DQN - Q(s,a) = expected total reward starting at current state (s)
    * Deep neural network (ConvNet?) as a representation of learned value function Q(s,a) and the approximation of the optimal/real Q-value
    * Basic RL nomenclatures: current state (s), state at the next step (s'), action (a), policy (p) and reward (r)...


4. Train & Evaluate:
    * Training through self-play, i.e. an agent that plays games against itself? (Possible with Kaggle??)
    * The target for model training is to approximate Q-value (Q(s,a)) = y^ and to update it through back propagation, for this a loss function L is introduced as:
      - L = (Q(s,a), y^)
    * This part is based on supervised learning. For that, Bellman Equation helps in finding the ground truth, i.e. the actual Q-value: Q(s,a) = max(r + Q(s',a)) --> if s is the terminal state, Q(s,a) = r
    * Model updates could be very unstable due to the target value changes each time the model is updated --> solution is to create a target network which is a copy of the training model at specific time step which leads to the advantage that the target model updates less frequently.
    * Another issue that we need to consider and check during training and evaluate is overfitting and the problematic effect of learning (false) correlation of time step t -> t+1 (temporal correlation). In order to counter balance that, we are going to use the experience replay buffer. This can store the values of hundreds of games and then can be used to select batches of game value tuples (s,a,r,s'), sampled at random, to train on and update the model.

5. Fine tuning etc.

### Sources:
* Kaggle (2020). _Simulation Competitions. Connect X - Connect your checkers in a row before your opponent!_. Retrieved from https://www.kaggle.com/c/connectx (February 6th, 2020).
* Kaggle (2020). _Connect X - Overview - Environmental Rules_. Retrieved from https://www.kaggle.com/c/connectx/overview/environment-rules (February 7th, 2020)
* Foster, David (2018). _How to build your own AlphaZero AI using Python and Keras_. Retrieved from https://medium.com/applied-data-science/how-to-build-your-own-alphazero-ai-using-python-and-keras-7f664945c188 (February 6th, 2020).
* Wikipedia (2020) - _Q-Learning_. Retrieved from https://en.wikipedia.org/wiki/Q-learning (February 13th, 2020)
* Siwei Xu (2019) - _ _ Retrieved from https://towardsdatascience.com/deep-reinforcement-learning-build-a-deep-q-network-dqn-to-play-cartpole-with-tensorflow-2-and-gym-8e105744b998 (February 5th, 2020)
-----------

**Before submitting your proposal, ask yourself. . .**

- Does the proposal you have written follow a well-organized structure similar to that of the project template?
- Is each section (particularly **Solution Statement** and **Project Design**) written in a clear, concise and specific fashion? Are there any ambiguous terms or phrases that need clarification?
- Would the intended audience of your project be able to understand your proposal?
- Have you properly proofread your proposal to assure there are minimal grammatical and spelling mistakes?
- Are all the resources used for this project correctly cited and referenced?
