
> ## 브랜치를 합치는 예의바른 방법 : 풀 리퀘스트
<br><br>

``풀 리퀘스트`` : "A브랜치로 B브랜치를 병합해도 되겠니? 수정사항은 다음과 같아" 라고 __협력자에게 브랜치 병합을 요청하는 메세지를 보내는 것.__<br>
GitHub의 풀 리퀘스트 버튼은 자동으로 이 메세지를 만들어준다.
<br><br>

## 풀 리퀘스트 만들기<br>
1. 새브랜치 [feature/comment] 생성<br>
2. VScode에서 comment.md 새파일 생성 후 텍스트 입력<br>
 ![image](https://user-images.githubusercontent.com/84025858/227704448-c5ef07a8-f0a0-4d53-a021-675f607d63e5.png)<br><br>
3. add 후 commit<br>
![image](https://user-images.githubusercontent.com/84025858/227704634-2bbc14e5-afa4-480f-9425-ac88fc0d065c.png)<br><br>
4.  ``Compare & pull request`` 버튼은 풀리퀘스트를 보낼 수 있는 버튼이다.<br>
💬 _'너가 최근에 이 브랜치에 코드를 업데이트했으니 협력자에게 풀 리퀘스트를 보내려고 한다면 이 버튼을 클릭하라'_  라는 의미이다. <br>
 ![image](https://user-images.githubusercontent.com/84025858/227704718-edf74e86-b127-47f9-b3b3-233102d8feab.png)<br>
 ⚠️ 이 초록색 버튼은 최근에 푸시한 브랜치가 있을때만 보여진다.<br>
 _다른 브랜치로 풀 리퀘스트를 보내고 싶거나 직접 설정을 변경하고 싶다면  ``New pull request`` 를 이용하면 된다._
 <br><br>
5. 이제 메세지를 작성해야하는데, __그에 앞서 먼저 설정해야할 건 base브랜치와 compare(비교)브랜치이다.__ <br>
  - ``base 브랜치`` -> 병합결과물이 올라갈, 즉 기준이 되는 브랜치 <br>
  - ``compare 브랜치`` -> 현재 기준 브랜치의 비교대상이 되는 브랜치 <br><br>
우측에 ``Reviewere``를 클릭하면 협력자를 지정할 수 있다. <br><br>
⚠️ 내가 추가한 커밋이 잘 들어갔는지, 파일에는 빠진것이 없는지 제대로 검토해야한다. <br>
검토가 끝나면 Create pull request
![image](https://user-images.githubusercontent.com/84025858/227704857-cb72fa4b-5786-4ef2-a10f-d6367e6edc5b.png)<br><br>

6. 이제 내가 보낸 풀리퀘스트가 보인다.<br>
협력자가 이 풀리퀘스트를 확인하고 새롭게 추가된 코드를 검토할 수 있다.<br> 
_코드의 라인마다 댓글을 달 수 있어 해당 코드가 왜 고쳐졌는지, 혹은 어떻게 개선할 수 있는지 풀리퀘스트 내부에서 토론을 진행할 수 있다.__ <br>
협력자는 이 풀리퀘스틑 수락할 수 있고(Accept), 수정을 요청할 수 있으며(Requset change), 병합할 수도 있다(Merge pull request).<br>
![image](https://user-images.githubusercontent.com/84025858/227704945-8cbd20d7-7f0c-493b-9641-16a981c34a9f.png)<br><br>
7. Merge pull request 버튼을 누르면 병합 커밋을 만들 수 있는 창이 보인다. 브랜치와 브랜치를 병합하는 과정과 같다<br>
![image](https://user-images.githubusercontent.com/84025858/227704967-cb93a05e-3369-4076-b57e-e0b2239a7e07.png)<br><br>
8. 풀리퀘스트가 성공적으로 병합된 후 닫혔다는 메세지가 뜬다. 병합이 완료됨. <br>
 ![image](https://user-images.githubusercontent.com/84025858/227704982-fb2cbe08-b355-480a-9013-bc661d0dc2e1.png)<br><br>
9. 닫혀진 풀리퀘스트는 [Pull requests]의 [Closed]탭에서 확인 가능<br>
 ![image](https://user-images.githubusercontent.com/84025858/227705012-001d0b8e-55c8-4317-b85e-c374a3123939.png)<br><br>

- 소스트리에 확인하기<br>
__위에서 만든 병합커밋이 로컬에는 반영되지 않았다.__ <br>
``패치`` : Git에서 새로운 이력을 업데이트 하는 명령어. (웹사이트에서 새로운 데이터를 보려면 새로고침을 하는 것과 비슷하다)<br>
![image](https://user-images.githubusercontent.com/84025858/227705078-cdc29811-f81b-4cf2-b9f5-042d2846b8aa.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227705100-09fe7be3-a4de-4ce5-b254-b116c6052297.png)<br>
로컬의 main 브랜치에도 이 새로운 커밋을 반영하기 위해 pull 진행.
![image](https://user-images.githubusercontent.com/84025858/227705116-db096c3f-52e4-4268-b2a6-152a93f9b5df.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227705125-cd480252-c7a7-44ad-a7af-78f945e99edf.png)<br>

<br>

---

<br>
<br>

>### 개발이 완료되었습니다. 출시하자 : 릴리즈(release)
<br>

- ``프로그램 버전(version)``이란<br>
프로그램을 출시 및 업그레이드를 할 때, 이를 만든 회사는 버전을 명시한다.<br>
의미 있는 특정 시점의 맥략을 말하는 것이다.<br>
버전을 올리는 것은 크게 메이저 업그레이드와 마이너 업그레이드로 나뉜다.<br>
메이저 : 사용자들이 크게 느낄 변화를 적용했을 때. v2.x -> v3.x <br>
마이너 : 작은 변화 등이 생겼을 때. v.2.3 -> v.2.4
<br><br>

- 특정 커밋에 포스트잇 붙이기 - 태그 (tag)<br>
__프로그램을 출시하는 것__ 을 ``릴리즈``라고 한다.<br>
A개발자와 B개발자는 병합을 마친 main브랜치를 서버에 올려 사용자들이 쓸 수 있도록 배포하고, 현재 코드 상태 버전을 v1.0.0 라고 기록하려고한다.<br>
이는 태그를 통해 간단히 표시할 수 있다. 특정 커밋에 포스트잇을 붙이는 느낌이다.
1. <br> ![image](https://user-images.githubusercontent.com/84025858/227705366-b0e54b9d-5107-4556-8ef5-2c726122f27e.png)<br><br>

2. <br>![image](https://user-images.githubusercontent.com/84025858/227705375-d9b579ef-a4c7-4519-acdc-17e368cdd6ee.png)<br><br>

3. ⚠️ 만든 태그는 푸시를 해줘야 원격에도 볼 수 있다 <br> ![image](https://user-images.githubusercontent.com/84025858/227705400-6f2b8636-acd9-41a9-a852-77e3abcd72a8.png)<br><br>

4. <br> ![image](https://user-images.githubusercontent.com/84025858/227705424-3235e655-dbee-4d1f-a586-c34c421780d0.png)
![image](https://user-images.githubusercontent.com/84025858/227705681-4356a8bb-3fc9-47d1-aa59-3ff7ba199780.png)<br>