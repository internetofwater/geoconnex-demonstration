# geoconnex-demonstration
A repository to demonstrate the end2end potential of the geoconnex system, including distributed source metadata formatted as JSON-LD, harvest into a centralized triple store (graph.geoconnex.us) via Geoconnex PID, and queried via RDF4J SPARQL API for interactive manipulation in R (and maybe python).

## project organization

* `test_data` includes code and output to serve as the desired end state for KG queries in the demonstration to validate agains
* `sparql` includes documentation of plain-language versions of desired queries and their SPARQL equivalents
* `demonstration` includes an interactive document (likely [quarto/webR](https://github.com/coatless/quarto-webr?tab=readme-ov-file))

## Use case

 Comprehensive Assessment of a Spill on the Animas River Using Geoconnex and NLDI**

**Primary Actor:** Environmental Analyst

**Stakeholders:**
- **Environmental Analyst (primary user):** requires detailed and dynamic information on the downstream impacts of the spill for response planning and monitoring.
- **Public Health Officials:** need access to water quality data to assess and mitigate risks to public health.
- **Water Resource Managers:** use data to manage water diversions and prioritize remediation efforts.
- **Local Communities:** depend on accurate and timely information for safety and economic impacts.

**Preconditions:**
- A chemical spill has occurred on the Animas River, potentially impacting water quality downstream.
- The Geoconnex system is operational, providing a comprehensive knowledge graph of water-related data sources.
- The Network Linked Data Index (NLDI) is available to trace downstream effects from the spill site.
- Users have access to a graphical user interface for querying both the Geoconnex knowledge graph and NLDI.

**Main Success Scenario:**
1. **Event Detection and Initial Site Identification:**
   - The Environmental Analyst is alerted about the spill and uses the GUI to enter the spill location into the NLDI to trace downstream sites including surface water diversions, points of use, and water quality monitoring stations.

2. **Querying the Geoconnex Knowledge Graph:**
   - Using the downstream points identified from NLDI, the Analyst queries the Geoconnex knowledge graph for associated data. They search based on the time of the spill for parameters including specific contaminants likely released during the incident.

3. **Data Filtering and Analysis:**
   - **Locating Points of Diversion and Use:**
     - The Analyst identifies all points of diversion within the affected downstream area.
     - For each diversion, associated points of use (such as irrigation channels, municipal water intakes) are located.
   - **Identifying Water Utilities and Boundaries:**
     - For each point of use, the relevant water utilities (geoconnex.us/ref/pws) are identified along with their service area boundaries.
   - **Assessing Water Quality Testing Data:**
     - Water quality testing data from these utilities (NMWDI SDWIS STA endpoint) is accessed to understand the pre-spill and post-spill water quality.
   - **Locating WQP and NWIS Sites:**
     - The Analyst finds all relevant Water Quality Portal (WQP) and National Water Information System (NWIS) locations within the potentially affected area.
   - **Filtering by Contaminant Measurement:**
     - The Analyst filters these sites to include only those that have recent measurements of the specific contaminants involved in the spill (need metadata in the graph).
   - **Differentiating by Water Source:**
     - The data is further categorized to differentiate impacts on surface water from those on groundwater, considering the different pathways and risks associated with each.

4. **Impact Assessment and Reporting:**
   - Utilizing GIS and analytical tools, the Analyst maps the contaminant spread and identifies impacted communities and ecosystems.
   - They compile a comprehensive report detailing the spill's impacts, suggested remediation strategies, and urgent public safety recommendations based on the analyzed data.

**Postconditions:**
- The Environmental Analyst has a detailed and actionable overview of the spill’s impact, leveraging data integrated through the Geoconnex knowledge graph and NLDI.
- Public health officials and water resource managers are equipped with the necessary information to initiate response and mitigation actions effectively.

**Special Considerations:**
- **Data Gaps:** In case of missing data, the Analyst may need to directly engage with specific data providers.
- **Real-time Updates:** The system should support the incorporation of real-time data updates to reflect changing conditions in a dynamic environmental event scenario.
