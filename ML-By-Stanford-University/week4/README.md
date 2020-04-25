##  Neural Networks (NN)
  
  
###  Model representation

Let's examine how we will represent a hypothesis function using neural networks. At a very
simple level, neurons are basically computational units that take inputs (dendrites) as
electrical inputs (called "spikes") that are channeled to outputs (axons). In our model, our
dendrites are like the input features *x*<sub>1</sub>...*x*<sub>*n*</sub> , and the output is 
the result of our hypothesis function. In this model our *x*<sub>0</sub> input node is sometimes 
called the "bias unit." It is always equal to 1. In neural networks, we use the same logistic function 
as in classification, $frac{1}{1 + e^{-\theta^Tx}}$, yet we sometimes call it a sigmoid (logistic) 
activation function. In this situation, our "theta" parameters are sometimes called "weights".

Visually, a simplistic representation looks like:

$
\begin{bmatrix}
   x1 \\
   x2 \\
   x3
\end{bmatrix} \rarr \lbrack \rbrack h_theta(x)
$

Our input nodes (layer 1), also known as the "input layer", go into another node (layer 2), which finally outputs the hypothesis function, known as the "output layer".
We can have intermediate layers of nodes between the input and output layers called the "hidden layers."
In this example, we label these intermediate or "hidden" layer nodes $a_0^2...a_n^2$ and call them "activation units."

$a_i^(j) = "activation" of unit i in layer j_Θ^(j)=matrix of weights controlling function mapping from layer j to layer j+1$

$
\begin{bmatrix}
   x1 \\
   x2 \\
   x3
\end{bmatrix} \rarr \lbrack \rbrack h_theta(x)
$

$\begin{bmatrix}x_0 \newline x_1 \newline x_2 \newline x_3\end{bmatrix}\rightarrow\begin{bmatrix}a_1^{(2)} \newline a_2^{(2)} \newline a_3^{(2)} \newline \end{bmatrix}\rightarrow h_\theta(x)$

The values for each of the "activation" nodes is obtained as follows:

$
\begin{align*} a_1^{(2)} = g(\Theta_{10}^{(1)}x_0 + \Theta_{11}^{(1)}x_1 + \Theta_{12}^{(1)}x_2 + \Theta_{13}^{(1)}x_3) \newline a_2^{(2)} = g(\Theta_{20}^{(1)}x_0 + \Theta_{21}^{(1)}x_1 + \Theta_{22}^{(1)}x_2 + \Theta_{23}^{(1)}x_3) \newline a_3^{(2)} = g(\Theta_{30}^{(1)}x_0 + \Theta_{31}^{(1)}x_1 + \Theta_{32}^{(1)}x_2 + \Theta_{33}^{(1)}x_3) \newline h_\Theta(x) = a_1^{(3)} = g(\Theta_{10}^{(2)}a_0^{(2)} + \Theta_{11}^{(2)}a_1^{(2)} + \Theta_{12}^{(2)}a_2^{(2)} + \Theta_{13}^{(2)}a_3^{(2)}) \newline \end{align*}
$

This is saying that we compute our activation nodes by using a 3×4 matrix of parameters. We apply each row of the parameters to our inputs to obtain the value for one activation node. Our hypothesis output is the logistic function applied to the sum of the values of our activation nodes, which have been multiplied by yet another parameter matrix theta^(2)
containing the weights for our second layer of nodes.

Each layer gets its own matrix of weights, $theta^(j)$. 

The dimensions of these matrices of weights is determined as follows:
$
\text{If network has $s_j$ units in layer $j$ and $s_{j+1}$ units in layer $j+1$, then $\Theta^{(j)}$ will be of dimension $s_{j+1} \times (s_j + 1)$.}
$

The +1 comes from the addition in Θ(j) of the "bias nodes," *x*<sub>0</sub> and Θ<sub>0</sub><sup>(j)</sup>. In other words 
the output nodes will not include the bias nodes while the inputs will. The following image summarizes 
our model representation:

![](images/modelrepresentation.png)

### Multiclass Classification

To classify data into multiple classes, we let our hypothesis function return a vector of values. Say we wanted to classify our data into one of four categories. We will use the following example to see how this classification is done.
This algorithm takes as input an image and classifies it accordingly:

![](images/multiclass.png)

We can define our set of resulting classes as y:

![](images/yones.png)

Each $y^{(i)}$ represents a different image corresponding to either a car, pedestrian, truck, or motorcycle.
 The inner layers, each provide us with some new information which leads to our final hypothesis function. The setup looks like:
 
![](images/procedurehypothesisfunc.png)

Our resulting hypothesis for one set of inputs may look like:

$h_\Theta(x) =\begin{bmatrix}0 \newline 0 \newline 1 \newline 0 \newline\end{bmatrix}$

In which case our resulting class is the third one down, or $h_(Θ(x)_3)$, which represents the motorcycle.

