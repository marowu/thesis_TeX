### Working title
"Natural gas storage schedule cost optimization using quantum annealing"

### Recourses and time-frame
I'm able to work on the thesis for two days/week. I'd like to finish the thesis around February.

### Problem description
The task is to cost-optimise a schedule for a natural gas storages. The plant consists of two independent storages, each having unique characteristics. Each is able to accumulate and discharge natural gas to the system. The maximum rates of loading and unloading are not equal and differ for both storages. Also the cost of moving a unit of natural gas differs between the storages.

##### Storage A
Uses empty depleted natural gas field, hence it has high capacity but uses porous structure. Its geology greatly limits the rate at which gas may be loaded and unloaded from the storage.
Parameters:
* $\dot{V}_{A\_in\_max}$ - maximal rate of loading $[m^3/h]$
* $\dot{V}_{A\_out\_max}$ - maximal rate of unloading $[m^3/h]$
* $C_A$ - cost of loading/unloading a unit of gas $[\$/m^3]$

##### Storage B
Uses salt formation, a man-made cavern. The rate of loading and unloading is higher compared to storage A as the space is empty. As the cavern is man-made its storage capacity is substantially lower compared to storage A.
Parameters:
* $\dot{V}_{B\_in\_max}$ - maximal rate of loading $[m^3/h]$
* $\dot{V}_{B\_out\_max}$ - maximal rate of unloading $[m^3/h]$
* $C_B$ - cost of loading/unloading a unit of gas $[\$/m^3]$
##### Inputs
The problem is described by an hourly schedule of gas volumes that have to be either stored or fed to the system. The schedule specifies a single value and it is up to the storage operator how to manage both storages.

##### Constraints
Both storages have maximum available rates for loading and unloading. Also, because of technological constraints, the change in operating mode - loading or unloading, takes certain time (3 hours) during which the storage is unavailable.

##### Goal
The goal of the optimization is to develop detailed schedule for both storages that realise the input schedule at minimum cost.

##### Simplifications
Some of the constraints for real storages are non-linear. This increases the complexity of the problem. In reality, all three parameters describing the storage (maximum loading and unloading rates, cost/unit) change with the storage loading. A loaded storage will have different characteristic than an empty one.


