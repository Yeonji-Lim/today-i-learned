## C++ 개발환경 구축

```shell
$ lldb --version
$ clang --version
```

plugin 설치
1. C/C++
2. Code Runner
   ![[Pasted image 20220830123429.png]]

[[set_settings.json]]
```json
"code-runner.executorMap": {
	"cpp": "cd $dir && clang++ -std=c++17 $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"
}
```

task.json, launch.json 같은 것 잘 확인하자.. [[spawn_binsh_ENOENT]]