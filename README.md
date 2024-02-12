# geoconnex-demonstration
A repository to demonstrate the end2end potential of the geoconnex system, including distributed source metadata formatted as JSON-LD, harvest into a centralized triple store (graph.geoconnex.us) via Geoconnex PID, and queried via RDF4J SPARQL API for interactive manipulation in R (and maybe python).

## project organization

* `test_data` includes code and output to serve as the desired end state for KG queries in the demonstration to validate agains
* `sparql` includes documentation of plain-language versions of desired queries and their SPARQL equivalents
* `demonstration` includes an interactive document (likely [quarto/webR](https://github.com/coatless/quarto-webr?tab=readme-ov-file))
