## The Gradient Descent
- **Field**: Unconstrained continuous optimization
- **First-order Method**
<p align="center" width="100%">
    <img align="center" src="Img/true_gradient_descent.png" width="450" />
</p>

---
### **Concept**
The Concept of Gradient Descent is that "Gradient" (derivative for single variable function) provides a direction to "Descent" (optimize the function). 
```math
\min_{w\in \mathbb{R}} f(w) \;\;\;\;(Single\:Variable)
```
```math
\min_{w\in \mathbb{R^n}} f(w) \;\;\;\;(Multiple\:Variables)
```
So there're two important features to consider:

1. **Descent direction**
2. **Learning Rate $\alpha$**


```math
w_{n+1} = w_n - \alpha f'(w_n) \;\;\;\;(Update\:Rule\:for\:f\;of\:one\:Variable)
```
```math
(w_{n+1},\:f(w_{n+1})) \;\;\;\;(New\:pair\:for\:better\:choice\;of\:extrema\:value\:for\:f)
```
#### **- Linear Regression Single Neuron Model**
Recall the lec3, but the target function $f$ is set to be a linear function. Also the activation function is set to be the linear one.
<p align="center" width="100%">
    <img align="center" src="Img/the_single_neuron_linear_regression_model.jpg" width="600" />
</p>

#### **- Neuron Cost Function and Model Update Rule**
The cost function here we choose the **mean-squared error cost function**.
<p align="center" width="100%">
    <img align="center" src="Img\mean_squared_error_cost_function.jpg" width="600" />
</p>

#### **- Different Methods for Calculating the Full Partial Derivatives**
- <ins>**Batch Gradient Descent Algiorithm**</ins>

For each epoch:
1.  Caluculate the full gradient by
```math
\frac{\partial C(w_1, b; \mathbf{X}, y)}{\partial w_1} = \frac{1}{N}\sum_{i=1}^{N}\Big(\hat{y}^{(i)} - y^{(i)}\Big)x^{(i)}
``` 
```math
\frac{\partial C(w_1, b; \mathbf{X}, y)}{\partial b} = \frac{1}{N}\sum_{i=1}^{N}\Big(\hat{y}^{(i)} - y^{(i)}\Big)
``` 
2.  Then update $w$ and $b$ via the update rule

```math
w \leftarrow w - \alpha \frac{\partial C(w_1, b; \mathbf{X}, y)}{\partial w_1}
```
```math
b \leftarrow b - \alpha \frac{\partial C(w_1, b; \mathbf{X}, y)}{\partial b}
```
- <ins>**Stochastic Gradient Descent Algorithm**</ins> (**Common** and **Necessary** to find local minima.)

For each epoch, for each $i = 1, ..., N$:
1.  Caluculate the full gradient by
```math
\frac{\partial C(w_1, b; \mathbf{x}^{(i)}, y^{(i)})}{\partial w_1} = (\hat{y}^{(i)} - y^{(i)})x^{(i)}
``` 
```math
\frac{\partial C(w_1, b; \mathbf{x}^{(i)}, y^{(i)})}{\partial b} = (\hat{y}^{(i)} - y^{(i)})
``` 
2.  Then update $w$ and $b$ via the update rule

```math
w \leftarrow w - \alpha \frac{\partial C(w_1, b; \mathbf{x}^{(i)}, y^{(i)})}{\partial w_1}
```
```math
b \leftarrow b - \alpha \frac{\partial C(w_1, b; \mathbf{x}^{(i)}, y^{(i)})}{\partial b}
```
---

### **Implementation**

#### **- Dataset Description**
In the impletation the dataset **Palmer Penguins Dataset** being used.

Since the gradient descent here focus on linear regression, we are implement the method under these 4 numeric parameters:
- bill_length_mm
- bill_depth_mm
- flipper_length_mm
- body_mass_g

Target: Using The Gradient Descent to perform regression on relationships between numeric parameters of a specific species.
