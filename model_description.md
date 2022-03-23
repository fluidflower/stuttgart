_Please stick to the headings and their order. Don't modify the words in bold. Your input is required at each occurrence of "e.g." and "..."._<br>
_You may use https://tex-image-link-generator.herokuapp.com/ to render math formulas in Markdown, see the examples below._

## Physics

### PDEs

One mass balance per component water and CO2.

### Constitutive relations

#### Fluid-matrix interaction

* **Capillary pressure:**  Brooks-Corey
  ![p_c(S_{l}) = p_\text{entry}S_{le}^{-1/\lambda}](https://render.githubusercontent.com/render/math?math=%5Cdisplaystyle+p_c%28S_%7Bl%7D%29+%3D+p_%5Ctext%7Bentry%7DS_%7Ble%7D%5E%7B-1%2F%5Clambda%7D%0A)

* **Relative permeability:** Brooks-Corey with endpoints and residual saturations interpreted from the benchmark description

#### Phase composition: Applied equations of state

* **CO2 in liquid phase:**

* **Water in gas phase:**

The composition of the phases is calculated based on a set of relations according to Spycher and Pruess (2005), Duan and Sun (2003), and Spycher, Pruess and Ennis-King (2003)

#### Density

* **Liquid phase:** IAPWS

* **Gas phase:** Span and Wagner (1996)

#### Solubility limit

_Please provide the assumed solubility limit of CO2 in liquid phase at the tank bottom in kg/m<sup>3</sup>._

### Temperature

9.87°C (283K)

### Domain volume

_Please provide the assumed total volume of the computational domain in m<sup>3</sup>._

### Spatial parameters

_Please provide the relevant facies parameters as a csv file._<br>
The parameters we use are given in [stuttgart_materialData.csv](stuttgart_materialData.csv). Some of them are specific to our model and its regularizations for relPerms and capillary pressure relations.

## Numerics

### Coupling of flow and transport, temporal and spatial discretization

Fully coupled, fully implicit, cell-centered FV with TPFA.

### Linearization and Solvers

Newton with line search, umfpack for the linear systems.

### Primary Variables

Dependent on local phase composition: <br>
* Both phases present:
  [p_l, S_g](https://render.githubusercontent.com/render/math?math=%5Ctextstyle+p_l%2C+S_g%0A). <br>
Where only water phase is present, we use the concentration of CO2 in water as primary variable. A switching algorithm keeps track of changes in phase states.

### Computational Grid

structured grid with 26099 rectangular elements

### Performance

| Indicator                            |  Average |      Min |      Max |
|:-------------------------------------|---------:|---------:|---------:|
| time step size [s]                   |    20.44 |    0.021 |      600 |
| # nonlinear iterations per time step |      7.3 |        2 |       20 |
| # linear iterations per solve        |      -   |      -   |      -   |
