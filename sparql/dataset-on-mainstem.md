Copied from https://

The following SPARQL query would with precision identify datasets about streamflow, from a larger universe of data for a variety of variables from many monitoring locations that are within in the initial area of interest, within a time period of interest.

TODO:

- [ ] Add filter for mainstem

```sparql
PREFIX hyf: <https://www.opengis.net/def/schema/hy_features/hyf/>
PREFIX qudt: <http://qudt.org/schema/qudt/>
PREFIX qudt-quantkinds: <http://qudt.org/vocab/quantitykind/>
PREFIX ssn: <http://www.w3.org/ns/ssn/>
PREFIX schema: <https://schema.org/>

SELECT ?dataset ?dataDownloadURL ?measurementTechnique ?measurementMethodURL ?dataProvider ?dataProviderURL ?timeRangeStart ?timeRangeEnd
WHERE {
    ?dataset a schema:Dataset ;
             schema:variableMeasured ?variable ;
             schema:temporalCoverage ?temporalCoverage ;
             schema:provider ?dataProviderNode ;
             schema:distribution ?distribution .
             
    ?distribution schema:contentUrl ?dataDownloadURL ;
                  schema:encodingFormat ?encodingFormat .
                  
    ?variable qudt:hasQuantityKind qudt-quantkinds:VolumeFlowRate ;
              ssn:measurementTechnique ?measurementTechnique ;
              ssn:measurementMethod ?measurementMethod .
              
    ?measurementMethod schema:url ?measurementMethodURL .
              
    ?temporalCoverage schema:startDate ?timeRangeStart ;
                      schema:endDate ?timeRangeEnd .
                      
    ?dataProviderNode schema:name ?dataProvider ;
                      schema:url ?dataProviderURL .
                      
    FILTER (
        str(?measurementTechnique) = "model" || str(?measurementTechnique) = "observation"
    )
    
    FILTER (
        str(?timeRangeStart) <= "2023-09-01"^^xsd:date &&
        str(?timeRangeEnd) >= "2016-06-30"^^xsd:date
    )
}
```
