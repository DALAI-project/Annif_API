# Annif_API
Instructions and pretrained models for using annif software (annif.org) for automatic subject indexing as local server. It will used later under the repo DOCUMENT ANALYSIS.
This API contains models in finnish, english and swedish. It is based on the annif version 0.59, provided by National Library of Finland. 
* Install annif ( see annif.org for instructions)
* pip install annif[voikko]
* pip install annif[nn]
* pip install annif[omikuji]
* pip install annif[fasttext]
* pip install annif[pycld3]

* Download precompiled models from https://annif.org/download/models/ (use 2022-11 version)
* Remember to check projects.cfg and replace that file. Data folder must be placed into your virtual envoroment.
* On command line: annif run

  Annif API is now running on default address and port. You can change them following instructions given in annif pages.
  This will be used by Page_analysis_API, where the client is also given.
