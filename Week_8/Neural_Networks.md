# Neural Networks

### Basic architecture:
- Involves an input layer
    - where raw data after being converted into numeric data is inputed
- several hidden layers
    - each input node is connected to each node in the next layer
    - each node in the next layer takes a wighted sum of all the inputs from the previous layer nodes
        - w<sub>1</sub>a<sub>1</sub> + w<sub>2</sub>a<sub>2</sub> + ... w<sub>n</sub>a<sub>n</sub> + b
            - where `w` is the weight associated wth each node and `a` is each nodes value
            - `b` is the bias, a measure of how likely a node is to be active
    - then an activation function is applied on the sum to squish it into a value between 0 and 1
        - `sigmoid`(w<sub>1</sub>a<sub>1</sub> + w<sub>2</sub>a<sub>2</sub> + ... w<sub>n</sub>a<sub>n</sub> + b)  ---> [-1, 1]
        - `ReLu`(w<sub>1</sub>a<sub>1</sub> + w<sub>2</sub>a<sub>2</sub> + ... w<sub>n</sub>a<sub>n</sub> + b) ---> [0, +inf]
    - the value after applying the acitvation function is then fed to nodes in the enxt layer
    - this is done for each node for each layer
- output layer
    - softmax layer where probabilities are squished between 0 and 1 
---
- For tabular data, using traditional ML can bring the most value (even when DL outperforms ML).
- For unstructured data, such as images, speech, videos, or text, DL offers big improvements.
---

<img src="https://miro.medium.com/max/1804/1*f9XlMlruW7TMF3EHbPDfYg.png">

---

# Learning
### How a neural network learns.
- adjusting a neural network means to tweak the weights associated with the node connections
- the process of `learning` for a neural network is 
    - the iterative process of small adjustment to the weights 
    - in the direction that reduces the loss function (error)
    - until a local minimum to loss funciton is achieved
- This iterative process uses`gradient descent`
    - a cost (loss) function is defined
    - then the gradient (derivative) can be calculated
    - which will give the direction of steepest ascent, and it's magnitude
    - taking the negative will tell the fastest way to descend, ie reduce the cost function
### Backpropogation
- each output node 
    - has an error measuring how poorly it performs
    - the gradient tells us the `magnitude and direction` of the effect each node from the previous layer has on the output nodes error
- applying this to each output node
    - we can sum the weighted effect each node form the previous layer has on each node in the output layer
    - by minimizing this sum using gradient descent, we are minimizing the average error accross output nodes, to increase the models ability to generalize
- this process is done recursively
    - re-adjusting the weights in each hidden layer from the output node to the start of the network
    - and is done over all training data
        - increasing the models ability to generalize