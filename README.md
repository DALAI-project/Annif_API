You will need Python 3.8+ to install Annif 1.0.
The recommended way is to install Annif from PyPI into a virtual environment.
This one describes how to install Annif as it is in the arkkiivi backend. 
https://arkkiivi.fi/

>python -m venv annif-venv
>source annif-venv/bin/activate
>pip install annif


You will also need NLTK data files:
python -m nltk.downloader punkt

Test annif version 
> annif –version
As a result
> annif 1.0.0 

Download  yso-skos.ttl from https://github.com/NatLibFi/Finto-data/tree/master/vocabularies/yso/releases/2023.6.Hypatia

> annif load-vocab /path/to/yso-skos.ttl


Download latest models from  https://annif.org/download/models/finto-ai-2023-08/

Extract these files such that models and vocabs are in data folder in your annif-venv root
Using command 
>tree -d 

you have now: 5064 directories

At this point your data folder structure looks like

data
├── projects
│   ├── yso-bonsai-en
│   │   ├── omikuji-model
│   │   │   ├── settings.json
│   │   │   ├── tree0.cbor
│   │   │   ├── tree1.cbor
│   │   │   └── tree2.cbor
│   │   └── vectorizer
│   ├── yso-bonsai-fi
│   │   ├── omikuji-model
│   │   │   ├── settings.json
│   │   │   ├── tree0.cbor
│   │   │   ├── tree1.cbor
│   │   │   └── tree2.cbor
│   │   └── vectorizer
│   ├── yso-bonsai-sv
│   │   ├── omikuji-model
│   │   │   ├── settings.js  
            ├── tree0.cbor
│   │   │   ├── tree1.cbor
│   │   │   └── tree2.cbor
│   │   └── vectorizer
│   ├── yso-en
│   │   └── nn-model.keras
│   ├── yso-fasttext-en
│   │   └── fasttext-model
│   ├── yso-fasttext-fi
│   │   └── fasttext-model
│   ├── yso-fasttext-sv
│   │   └── fasttext-model
│   ├── yso-fi
│   │   └── nn-model.keras
│   ├── yso-mllm-en
│   │   └── mllm-model.gz
│   ├── yso-mllm-fi
│   │   └── mllm-model.gz
│   ├── yso-mllm-sv
│   │   └── mllm-model.gz
│   └── yso-sv
│       └── nn-model.keras
└── vocabs
    └── yso
        ├── subjects.csv
        ├── subjects.dump.gz
        └── subjects.ttl

18 directories, 27 files


copy projects.toml to your annif-venv root

Now you can test 

>annif show-projects



Project ID               Project Name                                 Language  Trained
---------------------------------------------------------------------------------------
yso-fi                   YSO suomi (2023.6.Hypatia)                   fi        None   
yso-sv                   ALLFO svenska (2023.6.Hypatia)               sv        None   
yso-en                   YSO English (2023.6.Hypatia)                 en        None   
yso-mllm-fi              YSO MLLM Finnish                             fi        True   
yso-mllm-en              YSO MLLM English                             en        True   
yso-mllm-sv              YSO MLLM Swedish                             sv        True   
yso-bonsai-fi            YSO Omikuji Bonsai Finnish                   fi        None   
yso-bonsai-sv            YSO Omikuji Bonsai Swedish                   sv        None   
yso-bonsai-en            YSO Omikuji Bonsai English                   en        None   
yso-fasttext-fi          YSO fastText Finnish                         fi        None   
yso-fasttext-sv          YSO fastText Swedish                         sv        None   
yso-fasttext-en          YSO fastText English                         en        
Then you need to install additional depencies:

Next

https://github.com/NatLibFi/Annif/wiki/Optional-features-and-dependencies

( Try without this first !) >sudo apt install libvoikko1 voikko-fi 

>pip install annif[voikko]

>pip install annif[fasttext]
 
>pip install annif[nn]

>pip install annif[omikuji]

>pip install annif[stwfsa]

Finally 

>annif run

And you should see.
* Debug mode: off
INFO:werkzeug:WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
INFO:werkzeug:Press CTRL+C to quit


Of course, at this point you can use annif from command line also

> annif
Usage: annif [OPTIONS] COMMAND [ARGS]...

Options:
  -e, --env-file FILE   Load environment variables from this file. python-
                        dotenv must be installed.
  -A, --app IMPORT      The Flask application or factory function to load, in
                        the form 'module:name'. Module can be a dotted import
                        or file path. Name is not required if it is 'app',
                        'application', 'create_app', or 'make_app', and can be
                        'name(args)' to pass arguments.
  --debug / --no-debug  Set debug mode.
  --version             Show the version and exit.
  --help                Show this message and exit.

Commands:
  clear          Initialize the project to its original, untrained state.
  completion     Generate the script for tab-key autocompletion for the...
  eval           Suggest subjects for documents and evaluate the results...
  hyperopt       Optimize the hyperparameters of a project using...
  index          Index a directory with documents, suggesting subjects...
  learn          Further train an existing project on a collection of...
  list-projects  List available projects.
  list-vocabs    List available vocabularies.
  load-vocab     Load a vocabulary from a subject file.
  optimize       Suggest subjects for documents, testing multiple limits...
  routes         Show the routes for the app.
  run            Run a development server.
  shell          Run a shell in the app context.
  show-project   Show information about a project.
  suggest        Suggest subjects for a single document from standard...
  train          Train a project on a collection of documents.


https://github.com/NatLibFi/Annif/wiki and have fun!







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
