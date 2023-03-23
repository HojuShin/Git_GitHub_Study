CHAPTER3. 여러 명이 함께 Git으로 협업하기
=============
<br>

> ### 원격저장소에서 협업하기 : 브랜치(Branch)

Git이 커밋을 관리하는 방식 : 시간 순으로 줄줄이 기차처럼 병렬로 연결<br><br>
만약 두 명 이상이 협업을 한다면 어떻게 될까?<br>
A개발자와 B개발가 각각 파일을 수정해 커밋을 해야한다고 가정해보자.<br>
새로운 커밋 모두가 기준 커밋(커밋3)과 연결되기 때문에 자연스레 두 갈래로 나뉘게 된다. <br>
![image](https://user-images.githubusercontent.com/84025858/226162549-86602443-b743-4c07-bac1-2a2a1a4da627.png)<br>
이렇게 특정 기준에서 줄기를 나누어 작업할 수 는 기능을 ``브랜치`` 라고 한다.<br><br>
⚠️새로운 가지로 커밋을 만들려면 반드시 브랜치를 먼저 만들어야한다. <br>
브랜치를 만들지 않고 협업을 하면, 원격저장소에서 먼저 푸시한 커밋은 정상적으로 올라가고 나중에 푸시한 다른 커밋은 ``'너는 낡은 코드에 푸시를 하는 것이다. 최신 코드에 푸시하라'``는 오류가 난다.
<br>
<br>
>### 브랜치, 정체를 밝혀라!<br>
브랜치에 커밋을 '올린다'라고 하지 않고 '가리킨다'라고 표현하는 이유? <br>
- 브랜치가 나뭇가지처럼 ~~물리적으로 '길'이 존재해서 그 길에 올리는 것이 아니라~~ 단순한 __'포인터' (가리키는 것)__ 이기 때문이다. <br> 컴퓨터 마우스의 커서(포인터)를 생각하면 된다. <br>
만약 브랜치가 물리적이고 독립적인 길이라면 브랜치마다 커밋을 새로 올릴것이다.<br>__그러나 브랜치가 포인터라는 것은 그저 커밋을 가리키는 것만으로도 분기를 만들 수 있다는 장점이 있다.__
분기를 만들려면 프로젝트를 통째로 복사해야 해서 무겁고 시간이 많이 걸리는 SVN과 같은 버전 관리 툴과 달리 Git은 가볍고 빠르다. <br>
![image](https://user-images.githubusercontent.com/84025858/226171928-5e881b46-cef3-4da2-aa71-f95d303ff773.png)<br>
A브랜치에 커밋을 추가 하면 아래 그림 처럼 A브랜치가 master브랜치보다 커밋 하나만큼 앞서게 된다. 
![image](https://user-images.githubusercontent.com/84025858/226171961-a2469ef8-cfe3-4769-8b78-e7c9dd62d095.png)<br>
그 상태에서 master브랜치로 이동해 커밋을 하나 더 하면, A브랜치와 master 브랜치의 버전이 갈라지게 된다. <br>커밋3을 기준으로 두 가지 버전이 생긴 것이다. <br>
![image](https://user-images.githubusercontent.com/84025858/226172530-4a9466e7-3bdc-4829-99df-4c8c1f1f807a.png)<br> <br>
#### _내 컴퓨터에서 A브랜치와 master 브랜치 사이를 넘나들 수 있을까?_ <br>
-  ``[HEAD]``라는 특수 포인터가 그 비법인데, 브랜치 또는 커밋을 가리키는 포인이다.<br>
앞 글에서 말했던 '타임머신'의 역할이라고 볼 수 있다.  [HEAD]를 통해 브랜치 사이를 마음대로 넘나들 수 있다. <br>
아래 그림에서 [HEAD]포인터는 커밋5 [master]브랜치를 가리키고 있어, 커밋5의 상태를 보여주고 있을 것이다. <br>
![image](https://user-images.githubusercontent.com/84025858/226172821-e1dbc91a-6fbe-4770-b478-11547a2c2731.png)<br>
최신 커밋 뿐 아니라 과거 커밋으로도 [HEAD]를 이동시킬 수 있다.<br> 아래그림처럼 커밋2를 가리키면 커밋2 버전을 보여줄 것이다. <br>
다만, 이 경우에는 master브랜치의 포인터와 [HEAD]가 떨어져있기 때문에 ``'분리된 HEAD(Detached HEAD)'``상태가 된다. <br>
![image](https://user-images.githubusercontent.com/84025858/226172910-9d62d37a-c2f0-48fe-8d7e-1f8322a22390.png)<br>

---
<br>

> ### 브랜치 실습 기본 : 만들고, 이동한다.
<br>

<pre><code>💻 협업을 위한 브랜치 사용법<br>
1. 개발자들은 커밋을 올릴 브랜치를 각각 만들고,<br>
2. 자신이 만든 브랜치로 이동한 다음,<br>
3. 브랜치에 커밋을 올리고,<br>
4. 코딩이 완료되면 브랜치를 합친다, <br>
</code></pre>

<br>

### _새 브랜치 만들기_
__버전이 꼬일 경우를 대비해 보통 하나의 개발 브랜치에는 한 사람만 작업해서 올리는 것이 바람직 하다.__ <br><br>
여러 사람이 작업하는 원격에는 미리 브랜치 규칙을 정하는 것이 일반적이다. <br>
책에서는 아래 규칙을 설정하였다 <br>
<pre><code>1. [master] 브랜치에는 직접 커밋을 올리지 않는다 (동시에 작업하다 꼬일 수 있으므로)
2. 기능 개발을 하기 전에 [master] 브랜치를 기준으로 새로운 브랜치를 만든다.
3. 이 브랜치 이름은 각자 [feature/기능이름]형식으로 하고 한 명만 커밋을 올린다.
4. [feature/기능이름] 브랜치에서 기능 개발이 끝나면 [master]브랜치에 이를 합친다.
</code></pre>
이렇게 하면 각자 브랜치에서 작업한 모든 코드가 [master]브랜치에 합쳐지게 된다.
<br><br>

![image](https://user-images.githubusercontent.com/84025858/226340352-92a56ea7-757d-4d42-9334-e994bdef7e31.png)
``체크아웃``은 브랜치를 이동하는 명령어이다. [새 브랜치 체크아웃]를 선택하면 새 브랜치를 만듦과 동시에 __그 브랜치로 이동하게 된다__ <br><br>

![image](https://user-images.githubusercontent.com/84025858/226676326-c6cbe2e3-875f-4459-a3a9-b3b46f1f10ce.png)
소스트리 좌측 [브랜치]를 보면 [feature]아래의 [detail-page] 가 표시되어 있다.<br>
소스트리의 편의기능인데,  브랜치 이름에 '/'을 넣으면 앞에 적은 텍스트'feature'가 마치 폴더처럼 구분되어 보여진다.<br><br>

VScode에서 새 detail-page.md파일을 추가하고 소스트리로 돌아와 해당 파일을 스테이지 위로 올리고 커밋메세지까지 추가한 후 커밋 지시
![image](https://user-images.githubusercontent.com/84025858/226678799-97311991-585d-4322-8cb9-cd0007e76410.png)<br>
커밋이 정상적으로 실행되었는지 [History]에서 확인. [feature/detail-page] 브랜치가 해당 커밋을 가르키고 있어야한다. <br><br>

커밋 추가를 위해, 기존에 있던 feature-list.md 파일의 4라인에 새로운 텍스트를 추가.<br>
![image](https://user-images.githubusercontent.com/84025858/226687968-898e5053-f5b2-43ad-842b-8e9fc224b0b7.png)<br><br>

![image](https://user-images.githubusercontent.com/84025858/226681445-bce0a980-2d1f-47e1-9401-92082a7df5a7.png)<br>
소스트리에서 변경한 feature-list.md 파일을 스테이지에 올리고 커밋메세지를 작성한다.<br>
이때 ``-에 바뀐 내용 즉시 푸시`` 체크박스를 선택하고 커밋을 지시하면 __현재 브랜치__ 인 [feature/detail-page]에 푸시까지 해준다. <br><br>

![image](https://user-images.githubusercontent.com/84025858/226681572-46391e3e-408f-43bd-aba1-5071f1394320.png)<br>
[origin/]이 붙은 것으로 봐서 원격에도 잘 올라갔다는 것 알 수 있다. <br><br>
GitHub에서 확인해보자<br>
![image](https://user-images.githubusercontent.com/84025858/226681887-205ac0f6-2299-4952-9e93-f6696721e1cd.png)<br>
[feature/detail-page] 브랜치와 브랜치에 추가한 커밋이 정상적으로 올라왔다.

<br>

---

<br>

> ### 브랜치 이동하기 : 체크아웃(checkout)
만약 B개발자가 장바구니를 기능을 만든다는 경우를 가정.<br>
B개발자도 병렬로 커밋을 올리기 위해서는 브랜치를 만들어야 한다. [main]브랜치로 돌아가서 새로운 브랜치를 생성하려한다.<br><br>

<pre><code>⚠️
[main]브랜치로 이동하지 않고 [feature/detail-page]에 남아 브랜치를 만들면 A개발자의 수정본까지 모두 반영이 되는 불상사가 발생한다.<br>
브랜치를 만들 때는 base 브랜치를 잘 설정해야한다 
</code></pre>
<br>

![image](https://user-images.githubusercontent.com/84025858/226686928-faa7724c-0631-4121-bed1-1d5e599f6289.png)<br>
호텔에서 나갈때 접수하는 것을 체크아웃이라고 하는 것처럼 브랜치를 이동하는 명령은 체크아웃이다.<br><br>

![image](https://user-images.githubusercontent.com/84025858/226687312-1e0498f3-4439-451e-ba76-d09805abd672.png)<br>
좌측 탭에 [main] 브랜치가 굵은 글씨로 확인되면 체크아웃 성공<br><br>

![image](https://user-images.githubusercontent.com/84025858/226687605-f0b789b4-b1b7-4a51-bb25-7af1d2d1b473.png)<br>
상단의 브랜치 탭에서 새브랜치를 생성해보자.<br>
__현재 브랜치가 [main]이 맞는지 확인 필수!__<br>
새브랜치명을 입력해주고 생성해준다. <br>
현재 브랜치는 [feature/cart]이다.<br><br>

![image](https://user-images.githubusercontent.com/84025858/226688030-39cd17e7-ff96-4632-a425-a6579951f112.png)<br>
feature-lis.md 파일을 보면  <br>
방금 [feature/detail-page] 브랜치에서 커밋했던 '3.디테일 페이지 보여주기' 텍스트가 보이지 않는다. <br>
그 이유는 텍스트를 추가하기 이전 버전으로 돌아왔기 때문이다.  <br>

![image](https://user-images.githubusercontent.com/84025858/226688190-0b7c104a-b542-4050-af32-5c96bb8002a0.png)<br>
[feature/cart] 브랜치는 이전 커밋 내용을 모른채 마지막 라인에 '3. 장바구니 담기' 텍스트를 추가했다.<br><br>

![image](https://user-images.githubusercontent.com/84025858/226688663-9f80260a-2ed2-40cf-900e-6677be471c34.png)<br>
새로 작성한 cart.md 파일과 feature-lis.md 파일을 모두 스테이지로 올리고 커밋메세지 작성 후 ``-에 바뀐 내용 즉시 푸시`` 선택 하여 푸시까지 한번에 작업해준다. <br>
![image](https://user-images.githubusercontent.com/84025858/227006059-bbc1a1cb-4340-426b-a5cf-c0a402afee39.png)수정한 파일 / 
 ![image](https://user-images.githubusercontent.com/84025858/227005915-924815a4-80eb-407a-bcb1-1b893a259c93.png) 새로 추가된 파일
<br><br>

![image](https://user-images.githubusercontent.com/84025858/226688831-d741bb95-ef64-4fa3-a733-6de1550038bf.png)<br>
![image](https://user-images.githubusercontent.com/84025858/226691482-8fb4d0e2-ee6a-4fe3-bb55-5c29932fcada.png)<br>
이렇게 각자 브랜치에서 개발하다가 각자 개발이 완료되면 [main]브랜치에 내 브랜치 작업물을 합치면 된다, 
<br>

---

<br>

> ### 요약
- 브랜치는 물리적인 '길'이 아니라 커밋을 가리키는 '포인터'이다.
- 개발자 각자 브랜치를 만들 때는 메인 브랜치에서 생성해야 한다.
- base 브랜치에서 새 브랜치를 생성해야한다는 것 주의.
- ``체크아웃``이란 현재 브랜치를 이동하는 명령어.
- ``[HEAD]``를 통해 브랜치를 넘나든다. 