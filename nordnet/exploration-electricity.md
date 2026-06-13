# Exploration: Electricity Systems

Use the[capacity expansion notebook](./pypsa-investment.ipynb) as a starting point for your own adventure.

Below you can find some ideas for sensitivities to explore and metrics to look at.

## Metrics

- Total annual system **costs** and breakdown by technology (billion €/a and % of total cost). This can be built from `n.statistics.opex()` and `n.statistics.capex()`.

- Installed **capacities** of the different technologies (fossil gas, wind, solar, battery, hydrogen storage, etc.). This can be accessed from `n.statistics.optimal_capacity()`.

- **Energy mix** and balances of different carrier as time series. This can be accessed from `n.statistics.energy_balance(groupby=["bus", "carrier"])` and plotted interactively with `n.statistics.energy_balance.iplot.area(bus_carrier="AC")`.

- Electricity **prices** (average and duration curve). These can be accessed under `n.buses_t.marginal_price`.

- Level of CO2 **emissions**. This can be calculated using `n.generators_t.p / n.generators.efficiency * n.generators.carrier.map(n.carriers.co2_emissions)`.

- Storage **filling levels** per technology over time. This can be accessed from `n.storage_units_t.state_of_charge`.

## Sensitivities

- **Optimistic Costs** Rerun the model with cost assumptions for 2050. You can change the year when loading the technology data.

- **Storage Constraints** What if either hydrogen or battery storage cannot be expanded? You can remove components with `n.remove("StorageUnit", "ComponentName")`.

- **Optimal energy-to-power ratios** Vary the energy-to-power ratio of storage technologies (e.g. 4h, 10h, 100h) and observe how this affects the optimal mix of storage and generation technologies. You can also add multiple storage setups with different energy-to-power ratios and see which one is chosen in the optimal mix.

- **Renewable Constraints** What if you can either only build solar or only build wind? You can remove components with `n.remove("Generator", "ComponentName")`.

- **Nuclear** Add nuclear as another dispatchable low-emission generator (modelled similarly to the OCGT generator). Perform a sensitivity analysis trying to answer how low the capital cost of a nuclear plant would need to be to be chosen in the cost-optimal mix.

- **Fossil Fuel Crisis** Observe how the total system cost and composition of technologies changes with increasing gas prices (which could be a result of an energy crisis or carbon pricing). You can change the gas price by adjusting the `marginal_cost` of the OCGT generator.

- **Emission Limit:** Successively constrain or relax the emission limit. This can be done by modifying the constant in `n.global_constraints`. The endogenous CO2 price can be found under `n.global_constraints.mu` (negative).

- **Storage Technology** Add a new storage technology with cost, efficiency and loss parameters. You could look, for instance, at a 100-hour iron-air battery.  This can be done with `n.add("StorageUnit", ...)`. Follow the same principle as for batteries and for techno-economic parameters look in the technology data file.

- **Renewable Profiles** Choose a different country for the renewable profiles (e.g. Spain instead of Germany) and observe how the optimal mix changes. You can retrieve the alternative wind and solar profiles from [model.energy](https://model.energy/).

**Feel free to explore other ideas as well!**

:::{note}
**Not enough?** Have a look at the [3-node investment model](https://docs.pypsa.org/latest/examples/3-node-cem/) in the PyPSA documentation for more inspiration.
:::
