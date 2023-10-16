# MaXO extraction test cases: from manual annotations

In this set of test cases, all grounded entities and relations are those defined within the set of MaXO annotations (see https://github.com/monarch-initiative/maxo-annotations/blob/master/annotations/maxo-annotations.tsv).

Only the identifiers and relations specified within the available annotations are included for each test case.

For example, if the following is the only annotation available for a test case:
```
disease_id	disease_name	citation	maxo_id	maxo_label	hpo_id	maxo_relation	evidence_code	extension_id	extension_label	attribute	creator	last_update	created_on
...
MONDO:0009367	Mckusick-kaufman Syndrome	PMID:20301675	MAXO:0000004	surgical procedure	HP:0030010	TREATS	TAS				ORCID:0000-0001-5208-3432	2023-01-31	2022-02-10
```

then the test case should include only the following:
* For `input_text`, approximately one paragraph containing the disease, action, and phenotype entities specified in the annotation. These may not be perfect lexical matches to any ontology term's label.
    * The text may be assembled from multiple non-consecutive selections of the source document. 
* For each of the `named_entities`, the CURIE specified in the annotation and the text within `input_text` corresponding to that identifier.
    * If the text from the source document does not explicitly mention the entitiy, use the corresponding ontology's label (this may be found on OLS - see https://www.ebi.ac.uk/ols4/). 
* Add a relation under `extracted_object` for each annotation. In this case, the relation will be:

  ```yaml
  extracted_object:
    action_to_symptom:
      - subject: MAXO:0000004
        predicate: TREATS
        object:
          - HP:0030010
  ```
  
  If the same MaXO term corresponds to multiple objects (e.g., MAXO:0000448 -> HP:0011781 and MAXO:0000448 -> HP:0002897 are both existing annotations), provide the objects in a list as follows:

  ```yaml
    extracted_object:
    action_to_symptom:
      - subject: MAXO:0000448
        predicate: TREATS
        object:
          - HP:0011781
          - HP:0002897
  ```
