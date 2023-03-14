## mmcv 설치하기,,

이거 조금 고생했다 자꾸 install 이 안되길래 왜그런가 하다가 해당 라이브러리 깃헙에서 찾았다.

다음의 형식으로 설치할 수 있다.

pip install mmcv-full=={mmcv_version} -f https://download.openmmlab.com/mmcv/dist/{cu_version}/{torch_version}/index.html
나 처럼 그냥 설치, cpu사용, torch 버전 1.7.1인 경우 다음의 명령으로 설치할 수 있다. 

pip install mmcv-full -f https://download.openmmlab.com/mmcv/dist/cpu/torch1.7.1/index.html
 
https://github.com/open-mmlab/mmcv 