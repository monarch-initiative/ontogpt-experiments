# Example Metadata Extraction for D4D

* `huggingface_urls.txt` contains one URL per line. Each corresponds to a single set of metadata describing a dataset on the HuggingFace platform.

The goal here is to:

1. Assemble sets of viable dataset metadata or cards
2. Use OntoGPT/SPIRES to extract metadata in schema-compatible structure
3. Ensure these examples translate to the primary D4D schema
4. Use examples as part of CurateGPT process for curating further metadata individually
