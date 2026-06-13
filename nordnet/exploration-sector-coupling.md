# Exploration: Sector Coupling (System)

Use the [sector coupling notebook](./pypsa-sectors.ipynb) as a starting point for your own exploration.

Explore how the model reacts to changing assumptions and available technologies. Here are a few inspirations, but choose in any order according to your interests:

**Task 1:** Assume underground hydrogen storage is not geographically available. Increase the cost of hydrogen storage by factor 10. How does the model react? You can alter the costs with `n.stores.loc["StoreName", "capital_cost"] *= 10`.

**Task 2:** Add a ground-sourced heat pump with a constant COP function of 3.5 but double the investment costs. Would this technology get built? How low would the costs need to be? You can add the technology with `n.add("Link", "ground-sourced heat pump", bus0=..., bus1=..., efficiency=..., capital_cost=...)`.

**Task 3:** Limit green gas imports to 10 TWh or even zero. What does the model do in periods with persistent low wind and solar feed-in but high heating demand? You can alter the initial filling level of the gas store with `n.stores.loc["gas storage", "e_initial"] = 10e6`.
