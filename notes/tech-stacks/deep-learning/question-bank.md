# DL Concepts

### What are the various parameters to consider when tuning a specific deep learning model?
- Check with candidate how do they tune the neural network model, especially when it has a huge degree of freedom.
- Walk through the process of what parameters was fixed and what was tuned.

### Specific model's architecture
- Ask the candidate to walk through the process in determining a model's architecture, the specific inductive biases it introduces that makes it good for specific problems etc.

### What are activation functions?
- Can understand non-linearity and name a few functions. ReLu, TanH, Sigmoid, Softmax, etc.

### If you encounter exploding gradient convergence issues, how would you diagnose and deal with this?
- Diagnosis: NA loss. Understands the necessity to scale features between 0 and 1 or batch normalization.
- Other techniques would include gradient clipping. Weight initialization.

### If you encounter vanishing gradient convergence issues e.g. NA loss, how would you diagnose and deal with this?
- Diagnosis: lack of loss convergence / weight distribution skewed to 0.
- Solution: reduce number of layers, appropriate weight initialization.
- Adopt ReLu loss function. For sequential model, LSTM rather than RNN.
- Skip-connections sometimes helps with gradient flows as well.