# Automatic generation of DCAT-AP+
In order to build an extension of DCAT-AP, a faithful translation of DCAT-AP into a LinkML schema was provided first.
For this, the JSON-LD serialization of the official DCAT-AP 3.0.0 SHACL shapes ([dcat_ap_shacl.jsonld](src/dcat_ap_shacl.jsonld)) were used, 
which we downloaded from the DCAT-AP GitHub repository [3.0.0 release folder within the master branch](https://github.com/SEMICeu/DCAT-AP/tree/master/releases/3.0.0/shacl). 
These SHACL shapes were then processed by the 
[dcat_ap_shacl_2_linkml.py](https://github.com/nfdi-de/dcat-ap-plus/blob/main/src/dcat_ap_plus/dcat_ap_shacl_2_linkml.py) 
script to generate two LinkML schemas from it:

  * [dcat_ap_linkml.yaml](src/dcat_ap_plus/schema/dcat_ap_linkml.yaml) - an almost 1:1 translation of the DCAT-AP SHACL shapes to LinkML.
  * [dcat_ap_plus.yaml](src/dcat_ap_plus/schema/dcat_ap_plus.yaml) - the LinkML representation of DCAT-AP to which we added the additional constraints, 
  * classes and properties we need for our provenance based extension.

## Automatic Translation of DCAT-AP into LinkML
The `dcat_ap_shacl_2_linkml.py` module performs the translation by reading the DCAT-AP JSON-LD file and generating 
corresponding LinkML constructs. DCAT-AP's SHACL node shapes are mapped to either LinkML classes or datatypes depending 
on whether they target ontology classes or XSD types, with property shapes serving as the basis for class slots. To 
ensure the new model remains semantically identical to the source, the original term IRIs are retained verbatim in the 
`class_uri` and `slot_uri` fields, drawn from the SHACL `targetClass` and `path` attributes.

Regarding range definitions, we addressed union ranges differently based on type. Object class unions, such as 
`dcat:primaryTopic`, were managed using the LinkML 
[any_of](https://linkml.io/linkml/schemas/advanced.html#unions-as-ranges) feature. Conversely, due to the lack of 
stable support for datatype unions in LinkML ([see issue](https://github.com/linkml/linkml/issues/1813)), we enforced a 
stricter interpretation for date-related slots, restricting them to the XSD date datatype. This approach allows us to 
meet current project needs while expecting full datatype union support in upcoming updates.

To adhere to LinkML's naming convention, we also changed the names of the derived and added slots from camel case to 
snake case.

## Automatic Extension of DCAT-AP in LinkML
To produce the DCAT-AP+ extension, we used the same Python script to add the additional constraints, classes and 
properties we needed, which are described in more detail in the 
[Design Patterns and Decisions section](design-patterns.md). 
Consequently, any future changes to DCAT-AP+ must be made in the `dcat_ap_shacl_2_linkml.py` 
([L412-L991](https://github.com/nfdi-de/dcat-ap-plus/blob/main/src/dcat_ap_plus/dcat_ap_shacl_2_linkml.py#L412-L991)).
