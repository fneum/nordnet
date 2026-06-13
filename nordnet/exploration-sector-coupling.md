# Exploration: Sector Coupling (System)

Use the [sector coupling notebook](./pypsa-sectors.ipynb) as a starting point for your own adventure.

## Metrics

- Total annual system **costs** and breakdown by technology (billion €/a and % of total cost). This can be built from `n.statistics.opex()` and `n.statistics.capex()`.

- Installed **capacities** of the different technologies (fossil gas, wind, solar, battery, electrolysis, hydrogen storage, heat pumps, CHPs, etc.). This can be accessed from `n.statistics.optimal_capacity()`.

- **Energy mix** and balances of different carrier as time series. This can be accessed from `n.statistics.energy_balance()` and plotted interactively with `n.statistics.energy_balance.iplot.area(bus_carrier="electricity")`.

- Electricity, hydrogen and heat prices **prices** (average and duration curve). These can be accessed under `n.buses_t.marginal_price`.

- Storage **filling levels** per technology over time. This can be accessed from `n.stores_t.e`.

## Sensitivities

- **Steel Tank Hydrogen Storage** Assume underground hydrogen storage is not geographically available. Increase the cost of hydrogen storage by factor 10. How does the model react? You can alter the costs with `n.stores.loc["StoreName", "capital_cost"] *= 10`.

- **Ground-Sourced Heat Pump** Add a ground-sourced heat pump with a constant COP function of 3.5 but double the investment costs. Would this technology get built? You can add the technology with `n.add("Link", "ground-sourced heat pump", bus0=..., bus1=..., efficiency=..., capital_cost=...)`.

- **Green Gas Imports** Limit green gas imports to 10 TWh or even zero. What does the model do in periods with persistent low wind and solar feed-in but high heating demand? You can alter the initial filling level of the gas store with `n.stores.loc["gas storage", "e_initial"] = 10e6`.

- **Hydrogen Demand** Vary the industrial hydrogen demand and observe how this affects the optimal mix of generation and storage technologies. You can alter the demand by changing the `p_set` attribute of the load at the hydrogen bus.

- **Electrolyser Flexibility** Restrict the flexibility of the electrolyser by adding a minimum load constraint that enforces high full load hours (e.g. 80% of its capacity using `p_min_pu`). This can be done by changing `n.links.loc["electrolyser", "p_min_pu"] = 0.8`.

- **No CHP** Remove the CHP (`n.remove("Link", "CHP")`) and observe how the system compensates. Does it build more heat pumps, more resistive heaters, more gas boilers? What if all heat demand needs to be met with heat pumps?

- **Biomass CHP:** Add a biomass CHP technology with the following parameters:

- Maximum production: 50 TWh/a of electricity
- Fuel cost: 15 €/MWh of biomass
- Electrical efficiency: 30%
- Heat efficiency: 70%
- Overnight  investment cost: 3500 €/kW of electrical capacity
- Lifetime: 30 years
- Discount rate: 7%

You can use the attribute `e_sum_max` for specifying the maximum production.

**Feel free to explore other ideas as well!**

:::{note}
**Not enough?** Have a look at the [islanded green methanol production example](https://docs.pypsa.org/latest/examples/islanded-methanol-production/) in the PyPSA documentation for more inspiration.
:::
