> ## 둘이 똑같은 코드를 고쳐버렸다 : 충돌(conflict) 해결하기
<br>

## 병합 커밋 및 충돌 해결

- base브랜치에서 merge하기 전에 __충돌 방지를 위해 내 브랜치(cart)에서 merge를 시도해본다.__ <br>
✅ main브랜치를 땡겨와서 내 브랜치에서 병합하면 된다 
![image](https://user-images.githubusercontent.com/84025858/227702743-41571944-1c8c-4435-89b5-fb88ee28bc5d.png)<br><br>
내 브랜치에서 병합된 커밋이 문제가 없는 것을 확인하면 base 브랜치에 반영한다.<br>
✅ cart브랜치에서 병합한 병합커밋을 main브랜치에 반영
![image](https://user-images.githubusercontent.com/84025858/227702811-5d5ac0e1-b595-42f5-9d98-618a01358bfe.png)<br><br>
- 소스트리 (detail-page 브랜치를 cart 브랜치에 병합)<br>
![image](https://user-images.githubusercontent.com/84025858/227703005-80f03e8c-e3d7-4e4e-9762-f689b3d666cd.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227703062-cd498480-d824-42d0-bbf6-bed4d36cfab6.png)<br>
feature-list.md 파일이 스테이지 아래에 있는 이유는 이 파일에서 충돌이 일어났기 때문이다. 이 파일을 고치면 병합을 진행할 수 있다.<br><br>
![image](https://user-images.githubusercontent.com/84025858/227703096-afe662f2-26e7-487f-a4cd-c9124025847d.png)<br>
VSCode에서 해당파일을 열어보면 git충돌이 난 코드를 자동으로 마크한 것이 확인된다.<br>
⚠️ `` 6라인의 ===을 기준으로 위는 cart브랜치, 아래는 detail브랜치 ``<br><br>
이렇게 해석할 수 있다 <br>
💬 _"둘 다 3번에 새로운 기능을 추가하고 싶었구나. 그렇다면 두 코드 모두 살려주고 뒤의 3번을 4번으로 고치자 "_ <br><br>
![image](https://user-images.githubusercontent.com/84025858/227703341-4f6db775-451a-4d0f-b2d5-a20eee87ba4c.png)<br>
충돌이 난 부분을 변경해서 정리.<br><br>
(소스트리에서 병합 재개)<br>
![image](https://user-images.githubusercontent.com/84025858/227703461-6cf13670-1554-4420-830f-9ae3b1e5b95b.png)<br>
수정한 파일 add진행<br><br>
- 1단계 : [detail-page] 브랜치를 땡겨와서 [cart]브랜치에서 병합
![image](https://user-images.githubusercontent.com/84025858/227703690-05932e34-8da2-471a-86b4-42f566096229.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227703741-124ada12-cfa4-4b81-9855-2417f382e03a.png)<br>
충돌해결.<br><br>
![image](https://user-images.githubusercontent.com/84025858/227703755-16bc43e6-5b41-4c2c-944e-ff093832731b.png)<br>
원격에 push까지 진행 <br><br>

- 2단계 :  [cart]브랜치에서 병합한 병합커밋을 [main]브랜치에 반영 
![image](https://user-images.githubusercontent.com/84025858/227703811-89402478-6080-4478-a65b-a5651e591c19.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227703847-b617e7c4-cba9-47a9-859b-0437879f29a1.png)<br>
__[main] 브랜치의 포인터가 최신 커밋인 ``mergee branch ..``로 온 것을 확인.__<br><br>
![image](https://user-images.githubusercontent.com/84025858/227703864-7349a962-7776-4adc-92c9-aeabef3f2601.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227703884-2f7cee61-0236-4299-9a6d-9d1e7e04d156.png)<br>
원격에 push.<br><br>
![image](https://user-images.githubusercontent.com/84025858/227703919-a21ac7b0-3f2c-466d-a813-b46156a88685.png)<br>
원격에서 병합이 이루어진 feature-list.md 파일 확인