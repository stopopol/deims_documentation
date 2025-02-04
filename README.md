#  DEIMS documentation

build it using sphinx in a python environment

!pip install -U sphinx
!pip install sphinx sphinx-rtd-theme

cd into base folder
make html

import shutil
shutil.make_archive("work/deims_docs", "zip", "work/deims_docs")
