# Installation of Julia

This document contains step-by-step instructions to install the Julia language, together with the necessary additional tools / environments that we will use in the course.

Please follow the instructions carefully and one by one. You should be able to copy and paste from this document; otherwise you must be careful to use the correct capitalisation, e.g. `IJulia`, not `Ijulia` or `ijulia`.

## 1. Install Julia

1. Download the current stable version of Julia (1.4.0) from https://julialang.org/downloads corresponding to your operating system, and install it.

    - For Linux you should download the "generic binary" and note where you save it on your machine (i.e. in which directory).

    - You may instead use your operating system's package installer (e.g. `homebrew` on Mac) to install Julia, *provided* that the version installed is at least 1.4.

2. Make sure that Julia runs and execute `1 + 1`.

3. If you know how to do so, you probably want to set up some kind of link or alias so that you can run Julia from anywhere.

4. Browse through the [Julia home page](www.julialang.org), have a look at the [comprehensive Julia manual](https://docs.julialang.org/en/v1) and a [page with resources for learning the language](https://julialang.org/learning).


## 2. Install the Jupyter notebook

We will use the [Jupyter notebook](jupyter.org) computational environment. Install it as follows:

1. Run Julia.

2. At the Julia prompt `julia> `, type

```jl
julia> using Pkg
julia> Pkg.add("IJulia")
```

3. When that has finished, at the Julia prompt `julia> ` type

```jl
julia> using IJulia
julia> notebook()
```

4. Answer `y` when asked if you want to install the Jupyter notebook.

A good alternative is to use the more modern [JupyterLab](https://jupyterlab.readthedocs.io/en/stable). To do so, type `jupyterlab()` instead of `notebook()`.


5. Install interactive capabilities that we will use:

```jl
julia> Pkg.add("WebIO")
julia> using WebIO
julia> WebIO.install_jupyter_nbextension()
```

If you use JupyterLab, replace the last line with `julia> WebIO.install_jupyter_labextension()`.


## 3. Install packages we will need

1. At the Julia prompt, type

```jl
julia> using Pkg
julia> Pkg.add("Plots")
julia> Pkg.add("Interact")
```

## 4. Install the Juno IDE

We will also use the Juno IDE (Integrated Development Environment). This consists of a set of plugins for the modern editor Atom. You can use Atom for editing all kinds of documents, not just Julia code.


1. Download and install the Atom editor from https://atom.io.

2. Run Atom.

3. In the Atom menu, choose `Preferences -> Install` and install the Atom package named `uber-juno`. This will install the Juno IDE, which is a collection of packages for Atom as well as some Julia packages for communicating with Atom.

4. Save a file called `hello.jl` with the contents `1 + 1`.

5. Type `Shift-Enter` to run the code (with your cursor somewhere on the line containing `1 + 1`).

6. For more information about Juno, see the [Juno home page](https://junolab.org).
