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
- NB! If you encounter a following error: `RuntimeError: Unsupported compiler -- at least C++11 support is needed!`. Then you need to install c++11 library. This can be done on ubuntu by running a command `sudo apt install g++`
- Download precompiled models from https://annif.org/download/models/ (use the versions in folder `finto-ai-2022-11/`) into the created virtual environment folder. 
- Extract the projects and vocabs under `data` folder in the created virtual environment. Note that during extraction in the `data/vocabs/` folder, the vocabularies are all named `yso` between all the models. This will launch a question during extraction process, that asks whether to overwrite the files. As the files in the `yso` folder are the same, you can overwrite them.
- After the extraction, you need to copy and rename the folders as presented in the folder tree below. 
- Place the `projects.cfg` file included in this repository to your venv root. You should now have the following folder structure:
```
├──annif-venv 
      ├──projects.cfg
      ├──data
      |   ├──projects
      |   |  ├──yso-en
      |   |  ├──yso-fi
      |   |  ├──yso-sv
      |   |  ├──yso-bonsai-en
      |   |  ├──yso-bonsai-fi
      |   |  ├──yso-bonsai-sv
      |   |  ├──yso-fasttext-en
      |   |  ├──yso-fasttext-fi
      |   |  ├──yso-fasttext-sv
      |   |  ├──yso-mllm-en
      |   |  ├──yso-mllm-fi
      |   |  └──yso-mllm-sv
      |   └──vocabs
      |      ├──yso-en
      |      ├──yso-fi
      |      └──yso-sv
      ├──bin
      ...
```
- On command line type `annif`: if installation was succesfull, you have now access to the Annif command line features.
- On command line type `annif run`
- Annif API is now running on default address and port. You can change them following instructions given in Annif pages.
- You can test the API
  - by using the command line and a text file containing the input. If the file name is `document.txt` and the used model is `yso-fi`, you can type `cat document.txt | annif suggest yso-fi` in the command line.
  - by using the web user interface which is running by default at http://localhost:5000/ 

  This API will be used by the [Document-analysis_API](https://github.com/DALAI-project/Document-analysis_API). In that repository, client code for accessing the API is also given.
