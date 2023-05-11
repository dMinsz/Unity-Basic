# Unity Settings Tips

0. Preferences 에 External tools 설정을 바꾸어 비주얼스튜디오 연동가능 (IDE 연동가능)

1. Preferences 에 PlayModeTint 로 게임 실행하는걸 색으로 구분가능하게 할수있다. 

    > 플레이 모드에서 무언가 바꾸면 안바뀌기때문 

2. Project Settings 에 Editor  Enter Play Mode Settings 를 설정해주면 씬만 리로드해서 플레이 전환이빠르게할수도있다.

	> 원래는 프로젝트 전체를 다시 리로드한다. 그래서 몇까지 문제가 생길 수 도있다. 
	(Static 변수가 초기화를 다른씬에서 한다던가.. 그러면 초기화가 안될수도있다.)


**3. 깃허브 세팅 및 비주얼 스튜디오로 깃허브연동**

   - Project Settings - Mode - Visible Meta Files 로 바꾼다.
   - Project Settings - Asset Serialization - Mode - Force Text 로 바꾼다.

   - Assets - Open C# Project 로 비주얼 스튜디오 를 열어준다.
	(여기서 깃 을 만들면된다..~ (git create Git Repository) , 주의 일단 로컬 에만 깃을 만든다.)

  - unity ignore로 추가하여 커밋한다.

> 그냥 커밋하면 문제는 에셋이 자동으로 모두 올라간다. 이러면 라이센스 문제등이 생길 수도있고
파일이 너무 커진다.
	
	그래서 다운 받은 모델이나 소스 , 에셋들은 (Imports/Resources) 임의의 폴더안에 넣어주자

	UserSettings 폴더도 제외해주자. (요즘 비주얼스튜디오는 자동으로 해준다)

	만약 유니티 버전 을 무시하고싶으면 버전컨트롤세팅도 제외하자.
	그러고 리셋 믹스드 해주고 깃 ignore 추가해서 다시 커밋하자.

4. 유니티 받기
	
	유니티로  파일가져와서 키면된다. 
	
	>추가로 임포트 ignore 추가해줘야 제대로 돌아갈 것 이다.
	><br>패키지형태로 복사해서 넣어주면된다.
	
	>Assets - import package 로 가져온다 (빼내는건 Export Package)
