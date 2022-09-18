# Overview

This is the source code for the site [fizzbuzz.ai](fizzbuzz.ai). It uses [Tensorflow JS](https://www.tensorflow.org/js) to train a simple model in the browser on the [Fizz Buzz problem](https://en.wikipedia.org/wiki/Fizz_buzz) when the user navigates to the page. When the model is finished training, the user can then enter a number  `N` (currently limited to 1024) and retrieve the model's fizzbuzz predictions on all numbers from `0:N`.

# Approach

The model is trained on 10-bit binary encoded representations of each number, and the output is a one-hot encoded vector which maps to the following:

| Vector      | Output |
| ----------- | ----------- |
| [1, 0, 0, 0]      | Original Number        |
| [0, 1, 0, 0 ]   | "Fizz" (n % 5 == 0)        |
| [0, 0, 1, 0 ]   | "Buzz" (n % 3 == 0)        |
| [0, 0, 0, 1 ]   | "FizzBuzz" (n % 3 == 0 && n % 5 == 0)        |

The approach was inspired by [this fantastic article](https://joelgrus.com/2016/05/23/fizz-buzz-in-tensorflow/) by Joel Grus.

The model is a simple dense network - single hidden layer with 100 units, all using ReLU.
# Improvements / TODO 
- Let the user specify the number of epochs to train the model?
   - This would also mean controlling when training starts/stops (maybe with a button)
- Write as a 3 class problem which permits multiple labels rather than having "FizzBuzz" be a separate class?

