# Sfc4q classes

*Space-filling curves*  (SFCs) can be used to index discrete grids, including the [Geospatial ones](http://docs.opengeospatial.org/as/15-104r5/15-104r5.html). Each cell in the grid is associated with an index, which can be produced by an SFC.  In this project, we are particularly interested in hierarchical grids with a recurring ​partition of quadrilateral cells in 4 regions​:

![](docs/assets/quadrilateral-refinementRatio4.png)

Therefore, we are interested in any SFC that is valid for indexing hierarchical grid of refinement-ratio-4 quadrilateral cells, abbreviated **SFC-4q**, or *Sfc4q* as adopted in the project's name and classes names.

In this project we are also interested in [geocodes](https://en.wikipedia.org/wiki/Geocode) obtained by labeling the SFC indexes,  expressing it in human-readable **hierarchical codes**. The hierarchy of the code is illustrated above as the commom prefix (e.g. `2` in `20` and `23`) that emerges in with the base4 representation.

## Framework organization

The framework can be used as simple standard interface for a set of SFC algorithms, like Hilbert, Morton or other.

![](docs/assets/umlClass01-intro.png)

The algorithms themselves are "concrete classes". But the standardization of basic methods, such as *endode()* and *decode()*, is not the issue, there are a lot of generic and reusable methods, so the best way is to extend a generic class with these reusable methods, and implement the concrete algorithm  as specialization. This project is a set of abstract and concrete classes.

Other important issue for SFC-4q is the generalization for "half levels" described in [this PDF article](http://osm.codes/_foundations/art3.pdf). It is also independent of the concrete algorithms. The illustration bellou is hou these classes uas implemented:

![](docs/assets/umlClass02-Sfc4q.png)

* [**GSfc4q**](https://ppkrauss.github.io/Sfc4q/docs/jsDocs/GSfc4q.html): the "Generalized Sfc4q" class.

* [**GSfc4qLbl**](https://ppkrauss.github.io/Sfc4q/docs/jsDocs/GSfc4qLbl.html): a generaliation of GSfc4q,  to translate *key*, *bkey* and cell identifiers (cell IDs) into human-readable labels (lbl). To preserve hierarchy, this translation uses the concept of [Sized Natural number](http://osm.codes/_foundations/art1.pdf), implemented in Javascript by the class SizedBigInt.

* **GSfc4qLbl_Hilbert**: the "concrete class" that implements the [Hilbert curve](https://en.wikipedia.org/wiki/Hilbert_curve).

* **GSfc4qLbl_Morton**:the "concrete class" that implements the [Morton curve](https://en.wikipedia.org/wiki/Z-order_curve) (also  Z-order curve).

* [**SizedBigInt**](https://ppkrauss.github.io/Sfc4q/docs/jsDocs/SizedBigInt.html): it is a complementar tool for use BigInt (mainly 64 bits unsigned integers) as hierarchical indexes and obtain its string representations.

See [classes documentation](https://ppkrauss.github.io/Sfc4q/docs/jsDocs).

## The grid and D3 peparation classes

* [**GridOfCurve**](https://ppkrauss.github.io/Sfc4q/docs/jsDocs/GridOfCurve.html)

* [**GridOfCurve_D3**](https://ppkrauss.github.io/Sfc4q/docs/jsDocs/GridOfCurve_D3.html)
