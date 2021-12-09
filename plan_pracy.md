### Working title
"Natural gas storage schedule cost optimization using quantum annealing"

### Recourses and time-frame
I am able to work on the thesis for two days/week. I'd like to finish the thesis around January (at latest).

### Thesis structure
1. Introduction
    * A brief history of QC
    * Gate QC
    * Quantum Annealing
        * Simulated annealing
        * Quantum annealing - simulated and hardware
        * Adiabatic quantum computation
2. How to use QA
    * Formulating problems
        * Ising model - how a physical design dictates the problem formulation
        * QUBO - how to describe non-binary world with a binary function
        * Embedding
    * Performance
        * Computational cost of QA
        * The search for a quantum speedup
3. Problem statement
4. Results
5. Summary

### Problem description
The task is to cost-optimise a schedule for a natural gas storages. The plant consists of two independent storages, each having unique characteristics. Each is able to accumulate and discharge natural gas to the system. The maximum rates of loading and unloading are not equal, differ for both storages and depend on respective storage fill levels $f_A$ and $f_B$. Also the cost of moving a unit of natural gas differs between the storages and depends on the fill levels.

##### Storage A
Uses empty depleted natural gas field, hence it has high capacity but uses porous structure. Its geology greatly limits the rate at which gas may be loaded and unloaded from the storage.
Parameters:
* $\dot{V}_{A\_in}(f_A)$ - maximal rate of loading $[m^3/h]$
* $\dot{V}_{A\_out}(f_A)$ - maximal rate of unloading $[m^3/h]$
* $C_A(f_A)$ - cost of loading/unloading a unit of gas $[\$/m^3]$

##### Storage B
Uses salt formation, a man-made cavern. The rate of loading and unloading is higher compared to storage A as the space is empty. As the cavern is man-made its storage capacity is substantially lower compared to storage A.
Parameters:
* $\dot{V}_{B\_in}(f_B)$ - maximal rate of loading $[m^3/h]$
* $\dot{V}_{B\_out}(f_B)$ - maximal rate of unloading $[m^3/h]$
* $C_B(f_B)$ - cost of loading/unloading a unit of gas $[\$/m^3]$
##### Inputs
The problem is described by an hourly schedule of gas volumes that have to be either stored or fed to the system. The schedule specifies a single value and it is up to the storage operator how to manage both storages.

##### Constraints
Both storages have maximum available rates for loading and unloading. Also, because of technological constraints, the change in operating mode - loading or unloading, takes certain time (3 hours) during which the storage is unavailable.

##### Goal
The goal of the optimization is to develop detailed schedule for both storages that realise the input schedule at minimum cost.

##### Simplifications
All three parameters describing the storage (maximum loading and unloading rates, unit cost) change with respective storage fill level. A loaded storage will have different characteristic than an empty one. This greatly complicates the task, as each step depends on all the previous. In first attempt, the loading, unloading rates and unit cost will be treated as being constant.

Another simplification relates to the type of variables. Pump capacity changes continuously in the range from $\dot{V}_{out}$ to $\dot{V}_{in}$. As the problem for a quantum annealer has to be formulated either as a QUBO or Ising model, only binary variables are allowed. Continuous range has to be transformed into a discrete one.
##### Changing the size of the problem
Current quantum annealers can calculate problems described by a limited set of variables. A handy problem formulation should allow for adjustment of the size. In the studied case, there are two areas that influence the size of the problem.
1. Granularity of the pump capacity - number of binary variables with which each pump is described. Eg. only two variables: load, unload vs. many eg. every 10%: 10%, 20%, 30% etc.
2. Time horizon of the optimization - eg. 12 hours vs. 72 hours.

Each of these areas linearly influences the problem size.



