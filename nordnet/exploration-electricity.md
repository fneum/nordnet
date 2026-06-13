# Exploration: Electricity Systems

Use the [capacity expansion notebook](./pypsa-investment.ipynb) as a starting point for your own exploration.

Explore the model by changing the assumptions and available technologies. Here are a few inspirations, which you do not have to follow in order:

**Task 1: Optimistic Costs** Rerun the model with cost assumptions for 2050. You can change the year when loading the technology data.

**Task 2: Storage Constraints** What if either hydrogen or battery storage cannot be expanded? You can remove components with `n.remove("StorageUnit", "ComponentName")`.

**Task 3: Renewable Constraints** What if you can either only build solar or only build wind? You can remove components with `n.remove("Generator", "ComponentName")`.

**Task 4: Nuclear** Add nuclear as another dispatchable low-emission generator (modelled similarly to the OCGT generator). Perform a sensitivity analysis trying to answer how low the capital cost of a nuclear plant would need to be to be chosen in the cost-optimal mix.

**Task 5: Fossil Fuel Crisis** Observe how the total system cost and composition of technologies changes with increasing gas prices (which could be a result of an energy crisis or carbon pricing). You can change the gas price by adjusting the `marginal_cost` of the OCGT generator.
