Extension 개발의 경우 다음의 가이드에서 쉽게 나와있습니다!

https://code.visualstudio.com/api/get-started/your-first-extension

node.js, git, yeoman, VS Code Extension generator를 깔아주고

yo code를 해주면 다음과 같이 귀여운 친구가 나옵니다.

<img width="952" alt="image" src="https://user-images.githubusercontent.com/57888020/174060826-fc3d21de-a06d-4345-89da-784d5458bcb8.png">

마지막에 code로 열껀지 물어보는데 저는 그러겠다고 했어요

그리고 F5를 입력해 실행해봅니다. 그러면 아마 vscode 새로운 창이 뜰거에요

여기서 Command+Shift+P 한 다음,

hello를 검색하면 다음과 같이 나옵니다.

![image](https://user-images.githubusercontent.com/57888020/174060875-b561e637-aa5c-4f95-9763-3a8e5398372e.png)

오른쪽 아래에 이렇게 뜨면 성공!

![image](https://user-images.githubusercontent.com/57888020/174060886-70c4eb6d-d3b9-404d-bc23-c863315c65d9.png)

프로젝트의 src/extension.js를 보면 다음과 같이 초기화되어 있습니다!

![image](https://user-images.githubusercontent.com/57888020/174060991-d625f9ef-f583-4afe-9b2a-30877c4548d4.png)

vscode.commands.registerCommand로 어떤 명령에 대해 설정하고

vscode.window.showInformationMessage 함수가 아까 그 문구를 나오게 한거네요

음 잘모르겠지만 여기에 이제 제가 원하는 것들을 넣으면 되겠죠

먼저 저는 언어에 따라 linter를 제공하고 싶기 때문에

저거랑 똑같이 넣어줬습니다.

![image](https://user-images.githubusercontent.com/57888020/174061057-320eb8d9-1dcd-4114-aa59-75c374cf2d4e.png)

그리고 이걸 package.json에서도 설정해줬어요

![image](https://user-images.githubusercontent.com/57888020/174061088-4e06e7d9-90be-44af-b5c2-20dab405ec65.png)

동일하게 실행후 검색 해보면 다음과 같이 잘 나오는 것을 볼 수 있습니다. 

![image](https://user-images.githubusercontent.com/57888020/174061143-f43b4bb3-a362-4ede-ad8c-9307b4601750.png)

![image](https://user-images.githubusercontent.com/57888020/174061155-89903745-f6de-4a24-ac0b-312b907ba9aa.png)
