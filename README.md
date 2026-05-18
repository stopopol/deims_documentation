#  DEIMS documentation

build it using sphinx in a juypter/python environment

!pip install -U sphinx

!pip install sphinx sphinx-rtd-theme

cd into base folder
make html

import shutil

shutil.make_archive("deims_docs", "zip", "deims_docs")
