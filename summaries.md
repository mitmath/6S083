# Lecture 1 (Mar 30)

We started off with a few words about the Jupyter notebook, the computational
environment we are using. Then we discussed Julia packages (libraries), which need to be
installed once (when you download the code they contain from the internet)
using e.g. `Pkg.add("Plots")`,
but loaded in each Julia session, with `using Plots`.

We saw how to download a data set in CSV (Comma-Separated Values) format
and load it into Julia using the `CSV.jl` package, which gives a `DataFrame`
object from the `DataFrames.jl` package.

We saw how to process the data frame to extract the data of interest, and in
doing so got a feel for some of Julia's data types, such as `String`, `Int64`
and `Float64`.

Then we saw how to plot the data using the `Plots.jl` package and how to
use a logarithmic (log) scale to observe the frightening exponential growth
of the COVID-19 pandemic.

# Lecture 2 (April 1)

We started our discussion of mathematical and computational modelling by asking
what a model is and isn't and what it is useful for, emphasising that models should
start off simple and then be made more complicated later.

As a simple model of infection, we used a deterministic model in which there is
a constant growth rate at each step, giving rise to exponential growth.
We saw how to implement this in Julia using a for loop inside a function, and
storing the generated data in a `Vector`.

We saw how to plot this and turn it into an interactive visualization using
the `@manipulate` macro from `Interact.jl`.

We then made the model more realistic by allowing people to be infected only
if they are not already. This led to a nonlinear equation that exhibits logistic
growth with a sigmoid (S)-shaped curve.

# Lecture 3 (April 6)

We began to discuss the need for **randomness** (or **stochasticity**) in models,
and saw that we could think of it as representing or modelling unknown information.

As an example, we discussed a simple model of recovery from an infection, in which
a patient has a probability $p$ to recover each day.

We saw how to generate events with probability $p$, i.e. Bernoulli trials,
and how to build up computational experiments in which we run a simulation many times,
i.e. Monte Carlo methods.

We discussed the concept of **random variable**, i.e. a quantity which has a different
outcome in each experiment. We then discussed the concepts of frequency and relative frequency,
leading to the concept of a **probability distribution**, which tells us how often
each outcome occurs.

# Lecture 4 (April 8)

In order to head towards a more realistic model, we need to allow individuals
to move around in space. So we introduced the simplest model of random motion in
space, namely a **random walk**, in which a particle jumps a distance $1$ either
left or right at each time step.

We saw how to build up functions to simulate and plot a trajectory of 1 or several random
walkers.  

Then we discussed the need to pregenerate data in the context of a random simulation,
and we saw that a suitable data structure is a `Vector` of `Vector`s, in which
each element of the outer `Vector` is itself a `Vector`, namely the trajectory of a
walker. We saw how we could then transform this into a `Matrix`, i.e. a true 2-dimensional
array.


# Lecture 5 (April 13)

We looked at **variability** of the probability distribution of a random variable.

If we plot a probability distribution, the first thing we notice is that it usually clusters around a central value. A common way to find this is by taking the **mean** of the sample.

We are then interested in the **spread** of the distribution away from the mean, i.e. some measure of the width of the distribution. We start by centering the data by subtracting the mean. We can calculate a positive distance either by taking the absolute value of the centered / de-meaned data, or by squaring it. Then we take the mean of the result.

If we use the squaring option, we get something with the "wrong units", e.g. metres squared instead of metres; this is the **variance**. To get a measure of the width of the distribution we must then take the square root of this to give the **standard deviation**, $\sigma$.

We saw empirically that often, for distributions that look like a normal distribution, about 70% of the data falls within a distance of $1 \sigma$ from the mean, while 95% falls within a distance $2 \sigma$.

Then we started discussing generic programming. We defined random walkers with different behaviours -- a discrete random walker and a continuous random walker. We saw that we could write code to evolve them in time that was **generic** -- i.e., it can be reused for both types of walker, without copying and pasting. To so, we defined a jump function for each type of walker and then **passed that function as an argument to the other function**, such that when we call the function that we passed as an argument, it calls the correct version.

Finally we started to introduce defining our own types in Julia.


# Lecture 6 (April 15)

We saw that in the case of different types of walker we need not only a special version of a `jump` function, but also the information about whether the position should be an integer or a floating-point number. Whenever we have different pieces of information that belong together, we should **build a new type**.

We build a new type using `struct` or `mutable struct`, the difference being whether or not the resulting objects can be modified or not after they are created. `struct`s collect together, or **encapsulate**, different pieces of information into a single conceptual whole, and allow us to give a *name* to that collection of data.

If we create a new type called, say, `MyType`, then Julia automatically creates **constructor functions** with the same name as the type. These are functions which, when called, **construct** objects of that type, i.e. with the internal structure (collection of data) that we specified. If we create an object of that type as `x = MyType(10)` then the internal data can be accessed as `x.data`, where `data` is the name of the internal field.

We can create our own constructors, for example to specify default values for the fields, by just writing a new **method** (version) for the function.

We saw that it is common in Julia to write lots of small functions to build up functionality that is reusable.

One way to make code reusable, i.e. **generic**, is to collect related types by defining them to be **subtypes** of an **abstract type**. We can then define functions that accept arguments only of that abstract type.
