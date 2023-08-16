# Annif_API
Instructions for pretrained models for using [Annif software](https://annif.org/) for automatic subject indexing as a local server. It is used also in the [Document-analysis_API](https://github.com/DALAI-project/Document-analysis_API) repository.
This API contains models in Finnish, English and Swedish. It uses the Annif version 0.59, provided by National Library of Finland. 
- Install basic Annif following the instructions at https://github.com/NatLibFi/Annif/blob/main/README.md
- Install dependencies:
  - pip install annif[voikko]
  - pip install annif[nn]
  - pip install annif[omikuji]
  - pip install annif[fasttext]
  - pip install annif[pycld3]
- Download precompiled models from https://annif.org/download/models/ (use the versions in folder `finto-ai-2022-11/`)
- Extract the projects and vocabs under `data` folder.
- Place the given `projects.toml` file to your venv root. You should now have the following folder structure:
```
├──annif-venv 
      ├──projects.toml
      ├──data
      |   ├──projects
      |   └──vocabs
      ├──bin
      ├──include
      ├──lib
      └──lib64
```
- On command line type `annif`: if installation was succesfull, you have now access to the Annif command line features.
- On command line type `annif run`

  Annif API is now running on default address and port. You can change them following instructions given in Annif pages.
  This will be used by [Document-analysis_API](https://github.com/DALAI-project/Document-analysis_API). In that repo client code is also given.
