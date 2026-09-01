# Day 14 Progress: Deep Neural Network From Scratch

## What I Did Today

### Concept Quiz (Separate Chat)
- Quizzed on newest concepts (chunked session)

### Project 18: Deep Neural Network From Scratch
- Built deep feed-forward network in NumPy
- Multiple hidden layers with ReLU activation
- He initialization for ReLU
- Input normalization to prevent overflow
- Minibatch training with learning rate decay
- Trained on spiral classification (non-linear problem)
- Achieved 100% training accuracy after debugging

### Key Debugging Journey
- Tried sigmoid for hidden layers → vanishing gradient, stuck at 50%
- Tried ReLU → gradient explosion (NaN) because learning rate too high
- Fixed learning rate → dead neurons, stuck at 50%
- Added He initialization → still NaN because input data not normalized
- Added input normalization → finally learning
- Added minibatches + learning rate decay → smooth training, 100% accuracy

### Lessons Learned

1. **Sigmoid in deep networks fails** — vanishing gradients prevent learning
2. **ReLU works better** — no saturation for positive values
3. **He initialization is essential for ReLU** — prevents explosion
4. **Input normalization is critical** — large input values cause overflow
5. **Learning rate decay stabilizes convergence**
6. **Minibatches improve gradient estimates**
7. **Debugging deep networks is hard** — NaN, vanishing gradients, dead neurons all possible

### Key Concepts Reinforced
- ReLU vs sigmoid for hidden layers
- He initialization vs Xavier
- Input normalization
- Minibatch training
- Learning rate decay
- Vanishing/exploding gradients
- Cross-entropy loss with sigmoid output

## Updated Concept Counts

- Core concepts: 33 + ReLU, He init, input normalization, minibatch, LR decay = 38 core
- Supporting concepts: 18
- Total: 56 concepts

## Projects Now (18 total)

1. Email Generator
2. Support Agent
3. DocuBot
4. Nimbus Coffee Fine-Tune (LoRA)
5. Semantic DocuBot
6. Hybrid RAG
7. RAG Evaluation Harness
8. Nimbus Full Fine-Tune
9. Reranking RAG
10. Query Expansion RAG
11. Own Training Loop
12. Attention From Scratch
13. Tiny Transformer
14. Model Evaluation
15. FastAPI Model Serving
16. Synthetic Data Fine-Tuning
17. ANN From Scratch
18. Deep Neural Network From Scratch

## Next Steps

- Project 19: MNIST Classification
- Then full transformer training
- Then RLHF and reward models
- Continue daily concept quiz

## Key Milestones

1. First deep neural network from scratch
2. Learned to debug vanishing/exploding gradients
3. Achieved 100% accuracy on spiral classification
4. Understood importance of input normalization
5. Implemented minibatch training and learning rate decay
