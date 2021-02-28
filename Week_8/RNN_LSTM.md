# Recurrent Neural Networks (RNN) 

RNN's behave like neural networks, except for the fact that they use previous outputs as an inputs for new predictions
- this is important because the past can be informative about the future
    - now each neuron has two (inputs)
        - the current data 
        - and the data from the immediate past
    - because of the two inputs, optimizing the model requires 
        - backpropgation on the weights of the network and the wieghts of the reccurent data


<img src="https://miro.medium.com/max/1562/1*L2yBwou6sFVuzuG4cJe7YQ.png">

---
# Long Short-Term Memory (LSTM)

LSTM are a more complicated versoin of RNN's
- includes actual memory so it remembers data from farther back in time

### Forget gate
#### Motivation: A reccurent model needs to know what to remember and what to forget
- takes last output and current input
    - concatenates then linear tranformations
    - applies sigmoid to squish between 0 and 1
- this is multiplied by the internal state
    - if 0 then previous internal sate completely forgotten
    - if 1 then it will be passed through
### Input gate
- take previous output and new inputs
    - apply sigmoid 
    - multiply output with candidate layer
- candidate layer:
    - applies a hyperbolic tangent (tanh) to the mix of input and previous output
    - gives a candidate vector to be added to the internal state
- The previous state is multiplied by the forget gate 
    - and then added to the fraction of the new candidate allowed by the output gate.
### Output gate
- controls how much of the internal state is passed to the output

---
[credit](https://medium.com/@rajan5787/recurrent-neural-networks-and-lstm-903862adb01)