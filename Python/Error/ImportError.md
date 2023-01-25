# ImportError: cannot import name 'imresize' from 'scipy.misc' 해결

scipy에 imresize가 없어졌다고 한다 

그래서 생기는 문제였음

https://github.com/raghakot/keras-vis/issues/209

# ImportError: attempted relative import with no known parent package

**python interpreter**는 **relative import의 module 위치를 정할 때** == **기준이 되는 모듈의 위치를 정할 때** 

**__name__속성에 의해 결정된다.**