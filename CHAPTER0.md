CHAPTER0. 빠른 실습으로 Git, GitHub 감 익히기
=============
  <br>
  
> ### 용어
1. ``Git`` : 버전 관리 시스템
2. ``GitHub`` : Git으로 관리하는 프로젝트를 업로드 하는 사이트
3. ``GUI`` : 그래픽 유저 인터페이스, 마우스로 클릭해서 사용하는 방식
4. ``CLI`` : 커맨드 라인 인터페이스, 명령어를 하나씩 입력하는 방식
5. ``Git Bash`` : CLI 방식으로 Git을 사용할 수 있는 환경
6. ``커밋`` : 버전 관리를 통해 생성된 파일 or 행위
7. ``로컬저장소`` : Git으로 버전 관리하는 내 컴퓨터 안의 폴더
8. ``원격 저장소`` : GitHub에서 협업하는 공간,폴더
9.  ``레포지토리`` : 원격저장소 (좀 더 있어보이는 용어)
10. ``push`` : 로컬의 커밋(버전관리한 파일)을 원격에 업로드
11. ``pull`` : 원격의 커밋을 로컬에 다운
12. ``클론(Clone)`` : 원격저장소의 코드와 버전 전체를 내 컴퓨터로 내려받는 것(최신 버전뿐만 아니라 이전버전들과 원격저장소 주소 등)
 <br>
 
> ### git 명령어
1. `` git config --global user.name / user.email `` : 사용자이름과 이메일 주소 설정. Git은 커밋할 때마다 이정보를 사용한다. 
2. ``git remote add origin`` : 로컬에서 원격 주소를 알려줌
3. ``git init`` : Git초기화 과정
4. ``git log`` : 현재까지의 모든 커밋내역 확인
5. ``git checkout`` : 원하는 커밋(버전)으로 되돌아감 (타임머신 역할)
 <br>

---
<br>
  
> ### 내 컴퓨터에 Git 설치 확인하기

  * 윈도우 검색창에서 Git Bash 실행 후 ``$ git`` 입력<br>
    아래처럼 Git 기본 명령어에 대한 안내가 나오면 설치 완료<br>
<img src="https://user-images.githubusercontent.com/84025858/224472472-2de151b2-2b47-4840-9cc2-ebe406cfeff6.png" width="500px" height="450px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
<br>

---
<br>

> ### 로컬저장소 만들기

``내컴퓨터 -> 바탕화면 -> 폴더 -> 하위폴더``

- 하위폴더 생성 (공부 진행을 위해 README.text 파일 생성)
- 하위폴더에서 마우스 오른쪽 버튼을 클릭하고 [Git Bash Here] 실행
- Git Bash 창이 열리면 ``git init`` 명령어 입력
- ``Initialized empty Git repository`` 텍스트가 나오면 성공
- 하위폴더 안에 [.git] 라는 폴더가 자동생성.<br>[.git] 폴더 안에는 Git으로 생성한 버전들의 정보와 원격저장소 주소 등이 들어있다.
- __[.git] 폴더를 로컬저장소 라고 부른다. 즉 하위폴더가 깃헙의 레파지토리로 생각하면 된다__
<br>

---
<br>

> ### 첫 번째 커밋 만들기
_먼저 버전관리를 위해 내 정보를 등록해야한다. 각 버전을 누가 만들었는지 알아야 협업하야 하므로_
- 하위폴더 [Git Bash] 실행 후 아래 두가지 명령어 입력<br>
<pre>
<code>
git config --global user.email "깃허브에 등록된 이메일" 
git config --global user.name "깃허브에 등록된 이름"
</code>
</pre> 
- 다음으로 커밋에 추가할 파일을 선택<br>
``git add 파일.확장명``

- 커밋에 대한 상세설명 입력 : __'-m'은 'message'의 약자__<br>
``git commit -m "사이트 설명 추가" ``<br><br>
![image](https://user-images.githubusercontent.com/84025858/224476509-505f2ba1-3fbb-4e56-a9a1-a2a8aaece8b1.png)<br>
`` 1 file changed, 1 insertion(+) `` 텍스트가 보이면 성공. 첫 번째 버전 만들기 완료! 
<br>

#### 방금 커밋한 파일을 수정 후 다시 커밋 하기 
_내용 업데이트 후 똑같은 과정을 반복하면 된다_
- 해당 파일 내용 추가 및 수정 후 저장 
- 명령어를 통해 커밋할 파일과 커밋메세지 입력
<pre><code>git add 파일.확장명
git commit -m "설명 업데이트"</code></pre> 
![image](https://user-images.githubusercontent.com/84025858/224476497-251954d4-df6b-4b3f-99e4-1e1d0257510f.png)<br>
`` 1 file changed, 1 insertion(+), 1 deletion(-) `` 텍스트가 보이면 성공

<br>

---

<br>

> ### 다른 커밋으로 시간 여행하기
- log 명령어로 현재까지 커밋 내역 확인<br>
``git log`` 입력<br>
![image](https://user-images.githubusercontent.com/84025858/224478376-ca102dee-004e-4229-b473-0fb4c6b3543e.png)<br>
`` commit d30c13be22c3173a91e3193540a8a51957e05745 ``<br> 알파벳과 숫자로 이루어진 긴 코드는 커밋 아이디이다.<br>
- checkout 명령어를 이용해 되돌리려는 커밋의 아이디 7자리를 가져와 해당 커밋으로 돌아간다. (전체 아이디를 가져와도 된다) <br>
``git checkout d30c13b`` 입력<br>
<img src="https://user-images.githubusercontent.com/84025858/224477854-e27fcfcb-043b-4cc9-a74d-6d23114bf0a2.png" width="757px" height="350px" title="px(픽셀) 크기 설정" alt="RubberDuck"></img><br/>
``HEAD is now at 해당커밋아이디 해당커밋상세내용 `` 텍스트가 뜨면 원하는 커밋으로 돌아간 상태.

- 작업중인 파일을 보면 커밋한 파일 내용으로 돌아간 것을 확인할 수 있음. 
- 다시 checkout을 이용해 최신 커밋으로 돌아가기 : __'-'은 최신 커밋을 의미한다.__<br>
`` git checkout - `` <br>
- 작업중인 파일을 다시여확인하여 최신 커밋으로 돌아온 것을 확인 할 수 있다. 

<br>

---

<br>

> ### GitHub 원격저장소에 커밋 올리기
- 원격저장소 깃허브 레파지토리 생성
- 원격저장소 폴더(레포지토리) Git Bash 실행 <br>
  ``remote add origin 원격저장소주소 `` 명령어 입력 <br>
- push 명령어를 이용해 로컬저장소에 있는 커밋들을 원격저장소에 업로드<br>
`` git push origin main`` <br>
- GitHub 원격 저장소에서 커밋한 파일과 내용 확인 

<br>

---

<br>

> ### GitHub 원격저장소의 커밋을 로컬저장소에 내려받기
- 내컴퓨터에 로컬저장소 폴더 생성
- GitHub의 해당 원격저장소 주소 복사<br>
⚠️ [Download ZIP] 으로도 소스코드를 받을 수 있지만, 원격저장소와 버전 정보가 제외되니 꼭 Clone을 통해 가져온다. <br>
- clone 명령어를 이용해 내 컴퓨터의 로컬저장소에 내려받기<br>
``git clone 복사한주소 .``<br>
파일 경로 : [로컬저장소 폴더] -> 내려받은파일 + [.git] 
<pre><code>⚠️⚠️⚠️


주소 뒤에 한칸 띄우고 .점을 꼭 찍어야한다 <br>
그렇지 않으면 해당 폴더안에 레포지토리 폴더가 생기고 그 안에 내려받은 파일과 [.git]이 생성된다. 파일구조거 복잡하게 되니 주의.<br>
[로컬저장소 폴더] -> [레포지토리 폴더] -> 내려받은파일 + [.git] 🚫
</code></pre>

- 내려받은 파일을 확인
- 해당 파일에서 작업 후 저장
- Git bash 에서 세 개의 명령어 실행
<pre>
<code>
git add 해당파일.확장자
git commit -m "커밋내용"
git push origin main
</code>
</pre> 
add -> commit -> push 순 기억하자!

<br>

---

<br>

> ### 원격저장소의 새로운 커밋을 로컬저장소에 갱신하기
_위에서 변경한 파일을 커밋 후 push 까지 완료 하여 원격에 업로드가 되었지만 내 로컬에는 반영이 되지 않았다.<br>
원격에 올린 새로운 커밋을 내 로컬에 내려받아 현재상태를 갱신해야한다._

- 나의 로컬저장소 Git Bash 실행 하여 ``pull`` 명령어 입력<br>
``git pull origin main`` <br> 
![image](https://user-images.githubusercontent.com/84025858/224480833-7bee8665-d5c6-469b-9dd3-2e9082d3802a.png) <br>
변경했던 파일이 1개이므로 ``1 file changed`` 메세지가 나오면 내 로컬에도 반영 성공! 
- 마지막으로 정상적으로 반영이 되었는지 확인한다. 
