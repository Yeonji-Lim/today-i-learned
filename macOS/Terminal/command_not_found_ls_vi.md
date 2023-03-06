```sh
zsh: command not found: ls
zsh: command not found: vi
```

이런 경우에

vscode로 .zshrc 들어가서 다음을 추가해주자

```sh
export PATH=%PATH:/bin:/usr/local/bin:/usr/bin
```
