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
