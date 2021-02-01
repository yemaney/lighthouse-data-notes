# Gradient Descent
- The idea
    1. Plot several regression lines
    2. Plot their respective  sum of square residuals (Loss Function)
    3. The minimum of the loss function plot is where the error is the least, or where the regression is most accurate
    4. Gradient descent takes big steps when far away from minimum and smaller steps when near
---
### General work flow
- Define `loss function`
- Define `learning rate`
- Derive the  (`gradient`) of the loss function
1. Choose random `starting point`, 
2. Calculate the respective gradient (`slope`) at the point value
3. Plug the slope into the step size calculation
    - `Step size = slope x learning rate`
4. Calculate new position
    - `New position = old point - step size`
5. Repeat steps 2-4 unti; step size is very small
---
