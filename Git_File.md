Git으로 관리하는 파일의 4가지 상태
=============
<br>


Git으로 관리하는 파일은 총 네가지 상태를 가진다. 각각 파일이 이 네가지상태를 오가며 버전 관리를 한다.
![](https://velog.velcdn.com/images/tlsghwn/post/6e544072-7152-4ef6-b640-b64d50ff69af/image.png)
<br><br>

> ### Git이 파일을 추적하고 스테이지에 올리는 법
1. 프로젝트 폴더에 Git 초기화를 하고 작업파일 두개를 만든 상태<br>이 두 파일은 한번도 커밋되지 않은 파일이라 파일상태 ``추적안됨(untracked)``
![image](https://user-images.githubusercontent.com/84025858/225081252-0764a754-0f9f-4394-84c8-089cb3de790a.png)<br><br>
2. add 명령어를 입력하면 스테이지에 등록됨.  파일상태 ``staged``
![image](https://user-images.githubusercontent.com/84025858/225080906-29df6b25-3b85-4cd5-966a-b3c78efc70f0.png)<br><br>
3. commit 명령어를 입력하면 스테이지에 등록된 파일 전체를 버전으로 만듦. 파일 상태``수정없음 (unmodified)`` (다시 수정가능)
![image](https://user-images.githubusercontent.com/84025858/225074112-724feefe-4217-4d36-b194-fd43761e9571.png)<br><br>
4. push 명령어를 통해 원격저장소에 업로드
![image](https://user-images.githubusercontent.com/84025858/225074408-747001cf-7465-4cc3-9f30-5b7eda25be83.png)<br><br>
5. 파일을 하나 수정해서 파일상태를 ``modified``로 변경. 새파일 생성하고 이 파일의 상태는 ``추적안됨(untracked)``
![image](https://user-images.githubusercontent.com/84025858/225075034-2c11a12a-80c4-436a-98db-1c5a5d6a510b.png)<br><br>
6. __파일상태가 ``수정없음``인 파일은 변경사항이 없으므로 스테이지에 올릴 수 없다!__ <br>
수정되고 새로생성된 파일만 add 명령어를 통해 스테이지에 등록. <br>
README 파일은 add 하지 않았지만 변경사항이 없기 때문에 이미 등록되어 있음.
![image](https://user-images.githubusercontent.com/84025858/225076866-6101c152-c33a-4506-9cb2-a570845d47b0.png)<br><br>
7. 커밋을 해준다. 이 커밋은 앞서 만든 커밋은 "프로젝트 초기화"에 연결되어 있어, app.js가 수정되었고 app.css 파일이 추가되었음.
![image](https://user-images.githubusercontent.com/84025858/225078882-fe8427ee-1248-4774-81c2-97519911e479.png)<br><br>
8. push 명령어를 통해 새로 만든 하나의 커밋 또한 원격에 업로드하면 버전관리 성공
![image](https://user-images.githubusercontent.com/84025858/225079839-6c767a10-1eff-4745-984d-fef8ce193fc5.png)


