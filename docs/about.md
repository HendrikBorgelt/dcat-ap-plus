# About DCAT-AP+

Funded by the German Research Foundantion (DFG) as part of the German National Research Data Infrastucture (NFDI) 
initiative under the grant numbers [441926934](https://gepris.dfg.de/gepris/projekt/441926934) and [441958208](https://gepris.dfg.de/gepris/projekt/441958208), 
DCAT-AP+ is being developed in close collaboration between the German research 
infrastructure projects [NFDI4Chem](https://nfdi4chem.de) and [NFDI4Cat](https://nfdi4cat.org/). 

To allow more fine-grained and semantic searches within their data repositories, 
both projects had to address the need to also provide detailed chemistry-specific metadata for the research data output
of their communities. Due to the disciplinary overlap of both projects, their previous collaboration was thus intensified 
to produce a common metadata schema called [ChemDCAT-AP](nfdi-de.github.io/chem-dcat-ap/), an extension of the 
[DCAT Application Profile](https://semiceu.github.io/DCAT-AP/releases/3.0.0/) that is based mostly on 
the [Starting Point Terms](https://www.w3.org/TR/prov-o/#description-starting-point-terms) of the W3C standard the Provenance Ontology (PROV-O). With ChemDCAT-AP, the chemical 
substances, entities and reactions covered by a dataset as well as the processes, 
tools and devices that were involved its creation can be described in a semantically uniform way that allows further 
use-case specific extension.
This work will be published and presented at the 19th International Conference on Metadata and Semantics Research 
([MTSR](https://www.mtsr-conf.org/home)) Thessaloniki, Greece, 15 - 19 December 2025. 

Since the underlying basic design patterns of ChemDCAT-AP are domain-agnostic and thus applicable to a much wider 
range of use cases, the core layer of ChemDCAT-AP, called DCAT-AP+, was decided to be outsourced into its own repository.

## Next Steps
Within the [NFDI Section Metadata Working Group Ontology Harmonization and Mapping](https://www.nfdi.de/section-metadata/),
we started to test and discuss the applicability of DCAT-AP+ for the whole NFDI community. Additionally, we currently 
investigate the feasibility of providing more semantic depth and interoperability by mapping the DCAT-AP+ schema 
elements to the [NFDIcore ontology](https://nfdi.fiz-karlsruhe.de/ontology/) instead of the PROV-O and DCTerms 
whenever appropriate.
