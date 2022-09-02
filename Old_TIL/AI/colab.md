## vscode colab 연동후 conda 

-> 근데 이방법아닌듯 이거하면 연결 끊기는거 같음 

중간에 나오는 restart kernel 때문인듯

~~~
!pip install -q condacolab
~~~
~~~
import condacolab
condacolab.install()
~~~

여기서 부터는 vscode 터미널

~~~
which conda
~~~

vscode에서 colab 연동할 때 #@ 이런거 다 지우자.. 이것 때문에 실행이 안될 수 있음