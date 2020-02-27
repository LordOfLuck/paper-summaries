# On the Expressive Power of Deep Neural Networks [https://arxiv.org/abs/1606.05336](link)

Authors explore network expresivity by varying its input.
To do so, a trajectory $x(t), t \in [0, 1]$ between two input points $x_0, x_1$ is defined, such that $x(0)=x_0$ and $x(1)=x_1$.
A trajectory can be a line, a circle or pretty much any curve in the input space.
The expressivity is measured across a trajectory.

Neural network expressivity is measured with the following approaches:

1. Number of linear regions
    If ReLU is used, the resulting mapping is piecewise linear. 
    The input space is partitioned into convex polytopes, each of which corresponds to different linear function.
    The higher the number of linear regions, the more non-linear the maping is.
    A neuron transitions if it changes it's activation from 'on' to 'off'.
    
The number of neuron transitions during a trajectory traversal grows exponentially with depth. (at least for bounded activations. How about ReLU?)
In other words, small changes on input or in earlier layers cause larger changes in the final layers.
Authors explain this with trajectory length. The trajectory length grows exponentially with depth.
For example, if the trajectory on input is a circle, after the first layer the circle is transformed into a longer curve and so on.
[TODO: add image from paper]
Thus, the deeper the network, more versatile outputs we can get from a small input perturbation.
Authors also observe, that earlier layers have larger impact on the output quality.

Authors trained a convolutional network on CIFAR and measured trajectory length in different network layers.
The trajectory was a line between two CIFAR datapoints.
The trajectory length per layer increased during training.
The network gets higher expressivity during training, but becomes less robust.
Batch normalization can help to deal with this.
Authors also propose Trajectory normalization. The activations are scaled by factor $\lambda len(current_trajectory)/len(orig_trajectory)$
and observe similar regularization effect to BatchNorm.
