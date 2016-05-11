Threats Risk Index (TRI)
------------------------

**Work in progress**

Threats Risk Index (TRI) is a different way to calculate risks in information security. As we have seen that a lot of risks model based on
generic cases, we wanted to create a risk evaluation which is based on current existing threats. The model of calculation is based on a simple way to sum the measures not implemented.

~~~~
Threats Risk Index = (Threat probability) * (1+SUM(recommendations not implemented))
~~~~

Threats
=======

Threats file is a list of known and seen threats in a specific region by a CSIRT or any organization with the capability of analysis for security incidents. The threat is defined by a simple description and id. Probability values are assigned per region (country-code) and defined on the overall probability of an incident to occur among the overall set of incidents seen. The probability value is a float (from 0 to 1). As the probability depends on the organization doing the analysis, it could be really scoped to their view on threats. Multiple threats and their respective probability can be combined from various sources in a sum. If a threat is no more seen or actively exploited by an attacker, it should be removed from the list.

[Current threats](./desc/threats.json)

recommendations
===============

Recommendations file is a list of known counter-measure implemented that should have at least one positive effect to limit one of the known threats. A recommendation is expressed in a description, a related question and an id.

[Current recommendations](./desc/recommendations.json)

counter-measures
================

Counter-measure file is a list of the combined recommendations for each known threat. An impact value is associated to each recommendations defining the level of impact if the recommendation is not implemented.

[Current counter-measures](./desc/counter-measures.json)


Example
-------

Cryptoransomware
================

~~~~
Backup = 3
Testing of backup = 4
Off-line backup = 4
Patching of browser extension = 2
~~~~

If none of the counter-measures are taken, the following risk can be calculated:

~~~~
(0.03) (1+3+4+4+2) = .42
~~~~

If backup are operational but the browser extensions are never patched:

~~~~
(0.03) (1+2) = .09
~~~~

