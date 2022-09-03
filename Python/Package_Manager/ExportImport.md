# Package List Export, Import

conda 저장 Export
~~~
conda list --export > packagelist.txt
~~~
conda 로드 Import
~~~
conda install --file packagelist.txt
~~~
pip 저장 Export
~~~
pip freeze > requirements.txt
~~~
pip 로드 Import
~~~
pip install -r requirements.txt
~~~
