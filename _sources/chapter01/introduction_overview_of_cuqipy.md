#  Overview of CUQIpy



## Table of Contents:
* [What is CUQIpy?](#what-is-cuqipy)
* [Why CUQIpy?](#why-cuqipy)
* [CUQIpy modules](#cuqipy-modules)
* [CUQIpy plugins](#cuqipy-plugins)
* [CUQIpy design principles](#cuqipy-design-principles)
* [CUQIpy team](#cuqipy-team)
* [Role of CUQIpy in this course](#role-of-cuqipy-in-this-course)
* [Remarks](#remarks)
* [How to run the code and solve the coding exercises in this mini-book?](#running-the-code)
* [Additional links](#additional-links)


## Introduction <a class="anchor" id="introduction"></a>

**note: some of the details mentioned here will make more sense after going through the next notebook titled "Probably the simplest BIP in the world"**

### What is CUQIpy? <a class="anchor" id="what-is-cuqipy"></a>
* CUQIpy is a Python package.
* CUQIpy stands for **C**omputational **U**ncertainty **Q**uantification for **I**nverse **P**roblems in **Py**thon.
* CUQIpy provides a framework for solving inverse problems using Bayesian inference.
* The framework enables:
  * Modeling Bayesian inverse problems
  * Solving Bayesian inverse problems using classical and advanced numerical tools
  * Analyzing the solution of Bayesian inverse problems

![CUQIpy overview](images/cuqipy_diagram.png)


### Why CUQIpy? <a class="anchor" id="why-cuqipy"></a>
CUQIpy is built to address the need for:
  - A unified framework for solving Bayesian inverse problems across various scientific and engineering applications
  - A platform for modeling, solving and analyzing the solution of Bayesian inverse problems
  - A tool that can be used for both research and teaching
  - A tool that can be used by both beginners and advanced users
  - A tool that combines classical and advanced and scalable numerical methods for solving Bayesian inverse problems
  - A tool that is implemented purely in Python with minimal dependencies and can be easily maintained and integrated with other tools


### CUQIpy modules <a class="anchor" id="cuqipy-modules"></a>
* CUQIpy consists of many modules for modeling, solving, and analyzing Bayesian inverse problems.
* These modules mostly correspond to typical steps/components in a Bayesian inverse problem.
* Each module contains classes and functions that are used to perform specific tasks.
* click [here](https://cuqi-dtu.github.io/CUQIpy/api/index.html) for an overview of the modules available in CUQIpy.

![CUQIpy modules](../images/cuqipy_modules.png)

### CUQIpy plugins <a class="anchor" id="cuqipy-plugins"></a>

* In addition to the CUQIpy modules, CUQIpy also has plugins that extend the functionality of the framework. 
* These plugins allow integration of third-party software and tools with CUQIpy.
* click [here](https://cuqi-dtu.github.io/CUQIpy/#cuqipy-plugins) to see the list of plugins available in CUQIpy.

![CUQIpy plugins](../images/cuqipy_modules_plugin.png)


### CUQIpy design principles <a class="anchor" id="cuqipy-design-principles"></a>
* Provide simple and intuitive interface for users
* Design for flexibility, extensibility, modularity, and maintainability
* Accommodate both beginners and advanced users. e.g.,
  - Provide a set of test problems to use for experimentation and prototyping
  - Automatic sampler selection for a range of problems
  - Enable advanced customization of the problem setup and solution
* Aligning the modeling code with the mathematical formulation of the problem, e.g.,
 
Bayesian model:

$$
\begin{align*}
d &\sim \text{Gamma}(1, 10^{-4})\\
s &\sim \text{Gamma}(1, 10^{-4})\\
x &\sim \text{LMRF}(d^{-1})\\
y &\sim \text{Gaussian}(\mathbf{A}\mathbf{x}, s^{-1}\mathbf{I})\\
p(d,s,x,y) &= p(d)p(s)p(x|d)p(y|x,s)
\end{align*}
$$

where $d^{-1}$ and $s$ are the precision parameters of the prior (the LMRF) and the data distribution (the Gaussian), respectively, $x$ is the model parameter, and $y$ is the data. $\mathbf{A}$ is the forward operator.

Bayesian model in CUQIpy:
```python
d = Gamma(1, 1e-4)
s = Gamma(1, 1e-4)
x = LMRF(1/d)
y = Gaussian(A@x, 1/s)
joint = JointDistribution(d, s, x, y)
```

See setting up a Bayesian model in CUQIpy in 4 steps [here](https://cuqi-dtu.github.io/CUQIpy/).

### CUQIpy team <a class="anchor" id="cuqipy-team"></a>
- [Jakob Sauer Jørgensen](https://orbit.dtu.dk/en/persons/jakob-sauer-j%C3%B8rgensen-2)
- [Nicolai André Brogaard Riis](https://orbit.dtu.dk/en/persons/nicolai-andre-brogaard-riis)

- [Amal Mohammed A Alghamdi](https://orbit.dtu.dk/en/persons/amal-mohammed-a-alghamdi)

- [Chao Zhang (Charlie)](https://www.dtu.dk/english/person/chao-zhang?id=207508&entity=profile)


### Role of CUQIpy in this course <a class="anchor" id="role-of-cuqipy-in-this-course"></a>
* The course "02975: Introduction to uncertainty quantification for inverse problems" covers various concepts in uncertainty quantification in inverse problems including:
  - Theory
  - Modeling
  - Numerical methods
  - Analysis
  - Coding

* This course is not specificly for learning CUQIpy, however, CUQIpy is used as a tool for demonstration, prototyping, and exploring ideas

* Although CUQIpy provides many methods for solving Bayesian inverse problems, the students will be asked in various assignments to implement some of the methods themselves to understand the underlying principles.

* The CUQIpy component of the course is covered in about 14 hours of lectures, exercises and a guest lecture by Jakob Sauer Jørgensen.


### Remarks <a class="anchor" id="remarks"></a>
- This is first time we offer the CUQIpy component of the course.
- We are excited about this component and hope you will find it useful.
- I am here to facilitate your learning of this component.
- Feel free to ask questions anytime.
- Feel free to provide feedback anytime and help us improve.
- There will be a lot of hands-on exercises and examples to help you understand the concepts.
- You are encouraged to work in pairs or groups of 3 to discuss and solve the exercises.
- Disclaimer: keep in mind that notation may vary among different course components.
- Throughout we will introduce many tools in CUQIpy and discuss 
    - how to use them
    - for what purpose
    - and identifying the right tool
- Throughout all the course components, including CUQIpy, you will end up with more tools in your BIP toolbox!
![toolbox](../images/toolbox3.jpeg)


### How to run the code and solve the coding exercises in this mini-book? <a class="anchor" id="running-the-code"></a>
- For now, it is not possible to run the code interactively in this online mini-book (plans to enable this in the future).
- We suggest the following options:
    - Running on your local machine (preferred)
    - Running on learnmore (if you have access)

#### Option 1: Running on your local machine
- You can download each notebook from the top right download button and run it on your local machine.
- Alternatively, you can clone the course repository and run the notebooks on your local machine. In a terminal, run the following command inside the directory where you want to clone the repository:
```bash
git clone https://github.com/CUQI-DTU/CUQI-Book.git
```
- To run the notebook, you will need to install CUQIpy and other dependencies, including Jupyter notebook, numpy, matplotlib, etc.

- The instructions for installing CUQIpy can be found [here](https://cuqi-dtu.github.io/CUQIpy/user/getting_started.html).

#### Option 2: Running on learnmore
- If you have access to learnmore, you can run the notebooks there.
- Login to [learnmore](https://learnmore2.compute.dtu.dk)
- Open the terminal (through the terminal icon at the bottom)
- Create a directory for the course and navigate to it, for example:
```bash
mkdir uqcourse2024
cd uqcourse2024
```
- Clone the course repository of the book inside the directory as explained above.
- Use the file browser on the left to navigate to the course directory and open the notebooks.
- To run the notebook, you need to select a kernel, two kernels are recommended for now (since they both have the latest version of CUQIpy):
    - `cuqipy-fenics`.
    - `cuqipy-CIL23.1.0`.

- Now you are ready to run the notebook, tip: use shift+(enter/return) to run a cell.


### Additional links <a class="anchor" id="additional-links"></a>
- Some of the exercises answers will be available in this hackmd page: https://tinyurl.com/uqcourse2024.