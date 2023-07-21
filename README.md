# Annif_API
Instructions for pretrained models for using annif software (annif.org) for automatic subject indexing as a local server. It will be used later under the repo DOCUMENT ANALYSIS.
This API contains models in finnish, english and swedish. It uses the annif version 0.59, provided by National Library of Finland. 
* Install annif https://github.com/NatLibFi/Annif/blob/main/README.md
* pip install annif[voikko]
* pip install annif[nn]
* pip install annif[omikuji]
* pip install annif[fasttext]
* pip install annif[pycld3]

* Download precompiled models from https://annif.org/download/models/ (use 2022-11 version)
* Extract the projects and vocabs under data folder.
* Place given project.cfg file to your venv root. 
* On command line: annif, if succesfull you have now command line features 
* On command line: annif run

  Annif API is now running on default address and port. You can change them following instructions given in annif pages.
  This will be used, where the client code is given.
