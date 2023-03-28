A개발자와 B개발자는 각각 브랜치를 만들어 작업했다. 작업이 완료되어 코드들을 합치려한다.<br><br>

> ## 브랜치와 브랜치 합치 : 병합 (merge)

- ``merge commit`` : 병합 커밋. 두버전의 합집합을 구해 __새로운 커밋__ 으로 생성된다.
- ``Fast-forward`` : 빨리 감기. 새로 상태를 만들어줄 필요 없이 최신 커밋으로 상태를 바꿔준다. 추가되거나 충돌되는 것 없이 그냥 휘리릭 이동만 하면 되서 빨리감기라고 한다. 
- ``Conflict`` : 충돌. 충돌이 난 부분만 확인을 하고 무엇을 남길지 수동으로 선택해주면 된다. 
<br><br>
### 두 브랜치를 합치는 과정
``merge`` 는 두 브랜치를 합치는 명렁어다.<br>
앞서 A, B개발자는 각각 개발을 완료했기 때문에 각자 만든 두개의 브랜치를 base브랜치에 합쳐야한다.<br><br>

- [main] 브랜치에 [feature/detail-page] merge하기 __(Before)__ <br>
A개발자는 [feature/datail-page] 브랜치에서 개발을 마치고 base 브랜치인 [main]에 이를 합치고자한다. 
![image](https://user-images.githubusercontent.com/84025858/227699943-9b492ded-12ef-41ea-8461-086a1bf902e5.png)<br>
위 그림에서 커밋4는 커밋2의 단순히 수정한 최신본이므로 두 브랜치를 합치면 특별히 바뀌는 상태없이 커밋4가 될것이다 <br>
-> ``Fast-forward``
<br><br>

- [main] 브랜치에 [feature/detail-page] merge하기 __(After)__ <br>
![image](https://user-images.githubusercontent.com/84025858/227700616-ea2bda62-a274-4e92-911b-01034d510585.png)<br>
커밋2을 가르키던 main브랜치가 ``Fast-forward``를 해서 커밋4를 가르키게 됨<br>
이제 main브랜치는 [feature/datail-page] 브랜치의 새로운 코드가 반영된 버전이 됨!<br><br>

- [feature/datail-page] 브랜치 삭제<br>
 [feature/datail-page]의 모든 내용이 main브랜치에 반영되었으므로 브랜치 삭제.<br>
![image](https://user-images.githubusercontent.com/84025858/227700642-7da4f556-4da1-4daf-841f-18eb4b291e3b.png)<br><br>
B개발자도 [feature/cart] 브랜치에서 작업을 마치고 main브랜치에 합치려한다. <br>그런데 위의 ``fast-forward`` 상황과는 다르다. <br>
위의 그림의 보면 [main]이 가르키는 커밋4와 [cart]브랜치가 가르키는 커밋5는 __커밋2를 중심으로 상태가 바뀌었기 때문이다.__ <br>
이런 경우 브랜치를 합치게 되면 __merge 즉, 병합 커밋 사례__ 가 될 것이다. 커밋4와 커밋5을 합친 병합 커밋을 만드는 것이다. <br>
![image](https://user-images.githubusercontent.com/84025858/227702154-3bc09ced-0f36-49ca-9db9-7a34e0572fa3.png)<br><br>
그렇다면 새롭게 만들어진 병합 커밋은 main브랜치와 cart 브랜치 중 어디에 올려야 하는가?<br>
둘 중 어디든 올려도 되니 상황에 따라 선택하면 된다.<br><br>
💬 _"main브랜치를 기준으로 병합한다"_ <br>
⚠️ 이때, main브랜치에 합쳐진 내용은 cart 브랜치에 반영안됨. <br><br>
- 소스트리에서 병합하는 법<br>
![image](https://user-images.githubusercontent.com/84025858/227701317-e1bebaf6-9ddf-4f83-8cbd-d039fe42cadb.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227701272-baced7eb-d2ea-4f38-b55e-fe648c6cdf99.png)<br>
![image](https://user-images.githubusercontent.com/84025858/227701402-f26eb41c-6bbc-42b6-85c6-2c27f972fe74.png)<br>
로컬에만 병합이 일어났고 원격에는 반영이 안되었기 때문에 'main 4'라고 표시된다.<br>
![image](https://user-images.githubusercontent.com/84025858/227701530-12a83359-54c0-4abe-a757-7eee3e5c521c.png)<br>
push를 해주면 병합이 원격에서 적용된다. 