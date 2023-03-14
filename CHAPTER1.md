GUI 환경에서 버전 관리 시작하기 
=============

<br>

#### 소스트리 : Git 사용을 도와주는 GUI 프로그램
<br>
<br>

> ### 로컬저장소를 소스트리에 불러오기
<br>

![image](https://user-images.githubusercontent.com/84025858/224543822-ede12254-1a4b-4524-82c8-bbe98403609c.png)


<table>
  <tr>
    <td>Clone</td>
    <td>원격저장소를 내 컴퓨터에 받아오고(로컬저장소 자동 생성됨), 소스트리에도 추가</td>
  </tr>
  <tr>
    <td>Add</td>
    <td>내 컴퓨터에서 이미 만든 로컬저장소를 소스트리에 추가</td>
  </tr>
  <tr>
    <td>Create</td>
    <td>내 컴퓨터의 폴더에 새로운 로컬저장소 생성하기 (git init)</td>
  </tr>
</table>

<br>
이번 편에서는 로컬저장소를 불러올 것이기때문에 Add 탭을 선택한다.
<br><br>

![image](https://user-images.githubusercontent.com/84025858/224543799-a9309697-57a4-4452-a7a7-5052e2ad969e.png)




![image](https://user-images.githubusercontent.com/84025858/224543877-81c6aadb-1089-49d8-9314-df3ffb95ef3b.png)
 [Git_GitHub_Study] 로컬저장소에서 버전 관리를 할 수 있는 새로운 탭이 열렸고,
전 파트에서 만들었던 세 개의 커밋이 보인다. 
<br>
<br>

#### 소스트리에서 로컬저장소 생성하기

[Create] 탭 사용
![](https://velog.velcdn.com/images/tlsghwn/post/3e39f7aa-3a96-4b69-8aec-732edbfc7cb3/image.png)

<br>

---

<br>

> ### 로컬저장소의 정체는 [.git] 폴더
- Git Bash 창에서 명령어로 수행했던 커밋들이 소스트리에서 보이는 이유? <br>
  -> [Git_GitHub_Study] 폴더 내부의 [.git]에 저장된 정보. 앞 글에서도 포스팅했지만 이 폴더가 바로 로컬저장소이다.<br>
     CLI 환경에서는 ``git init`` 명령어로, GUI 환경에서는 [Create]에서 폴더를 선택하면 만들어진다. 
     <br><br>
![](https://velog.velcdn.com/images/tlsghwn/post/cc763224-0841-4800-95a3-89128a89476f/image.png)

<br>

---

<br>

> ### 소스트리로 커밋 만들고 푸시하기 

- 작업하고 있는 폴더에 새파일이 생성되면 소스트리에 '커밋하지 않은 변경사항' 텍스트가 추가되고, 
하단의 [스테이지에 올라가지 않는 파일] 섹션에 새로 생성한 파일이 올라가 있다.<br>
기존 커밋에 비해 새로 만들었거나 수정, 삭제한 파일은 모두 이 곳에 보인다! 
![](https://velog.velcdn.com/images/tlsghwn/post/70448e13-6dfd-49b7-a8f9-7e336aa77cc0/image.png)

- 소스트리 상단의 [커밋] 아이콘을 부르면 뷰가 바뀐다. 아래 화면처럼 보이지 않는다면 [스테이지 뷰 나누기]를 누른다.
![](https://velog.velcdn.com/images/tlsghwn/post/8f8d201f-2ac5-43f7-8de7-df4cd3f6b2d2/image.png)


- 커밋할 파일을 +를 눌러 [스테이지에 올라간 파일]에 옮긴다 = ``git add feature-list.md``<br>
아래에 메세지를 입력하고 커밋 클릭 = ``git commit -m "티셔츠, 기능 리스트 추가"``
![](https://velog.velcdn.com/images/tlsghwn/post/44935ae2-608d-4913-99cc-357c32dd2623/image.png)

- 커밋을 완료했으면 History 탭에 커밋한 내용을 확인한다. 

<br>

---

<br>


> ### 커밋을 원격저장소에 푸시하기 

- 소스트리를 잘보면 [main] / [origin/main] 꼬리표가 있다

![](https://velog.velcdn.com/images/tlsghwn/post/5d039097-f795-41ef-bf6a-c0d6048de997/image.png)<br>

앞서 로컬저장소에서 원격저장소 주소를 알려주기 위해 아래 명령어를 입력했다. <br>
``git remote add origin 깃헙주소``<br>
이는 ``origin``이란 이름으로 원격저장소를 추가하라는 뜻이다.<br>
``origin``은 우리가 연결한 GitHub 원격저장소의 닉네임이며, 원격저장소의 현재 버전상태를 가리키는 커밋에 붙어있다.  

``main``은 우리가 커밋을 올리는 '줄기'의 이름이다. 
아래 소스트리의 [History]에서 그래프를 보면 커밋이 줄줄이 이어져있는 것을 볼 수 있다. <br>
![](https://velog.velcdn.com/images/tlsghwn/post/ad0f8cec-3561-40f7-b016-c49ba8732adf/image.png)<br>

즉 ``[main]``은 내 컴퓨터 로컬저장소 버전을,<br>
앞에 ``origin``이 붙은 ``[origin/main]``은 GitHub 원격저장소의 버전을 가리킨다<br>

__이를 통해, 내 컴퓨터의 로컬 버전과 원격 버전의 상태는 다른 것을 알 수 있다.__ 
<br><br>
- _로컬에서 커밋한 버전을 원격에서도 업로드 하기. push_<br>
![](https://velog.velcdn.com/images/tlsghwn/post/a47ea4c5-5390-4e1e-bc82-b42e73d6a3f2/image.png)<br>


위 작업이 완료되면 로컬의 [main]과 원격의 [orgin/main] 모두 최신 커밋을 가리키고 있는 것 확인할 수 있다. 
![](https://velog.velcdn.com/images/tlsghwn/post/14cb7819-7626-4be8-ab37-7c5bcab04be3/image.png)