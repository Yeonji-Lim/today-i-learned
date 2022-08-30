# spawn /bin/sh ENOENT

vscode에서 디버깅하려는데 이런 에러가 나면 task.json을 살펴보자

사례..

```json
{
	"type": "cppbuild",
	"label": "C/C++: g++ 활성 파일 빌드",
	"command": "/usr/bin/g++",
	"args": [
		"-g",
		"-std=c++14",
		"${file}",
		"-o",
		"${fileDirname}/${fileBasenameNoExtension}"
	],
	"options": {
		"cwd": "/usr/bin" // <- 이 놈 앞에 $가 들어가 있었다..
	},
	"problemMatcher": [
		"$gcc"
	],
	"group": "build",
	"detail": "디버거에서 생성된 작업입니다."
},
```

launch.json이나 settings.json도 잘 살펴보자..