# Unity Settings Tips

0. Preferences 에 External tools 설정을 바꾸어 비주얼스튜디오 연동가능 (IDE 연동가능)
> 환경 변수에 등록이 되어있는 IDE 기준(혹은 편집기)으로 보여준다.

1. Preferences 에 PlayModeTint 로 플레이 모드 상태를 색으로 구분가능하게 할 수 있다. 
> 플레이 모드에서 무언가 바꾸면 게임에 적용이안되고 게임 플레이를 멈추면 사라지기 때문에 조심하자.

2. Project Settings 에 Editor  Enter Play Mode Settings 를 설정 해주면 현재 씬만 리로드해서 
   
   플레이 모드로 빠르게 전환 할 수 도있다.

> 원래는 프로젝트 전체를 다시 리로드한다. 
><br> 그래서 이기능을 사용하면 몇까지 문제가 생길 수 도있다. 
<br>(Static 변수가 초기화를 다른씬에서 한다던가.. 그러면 초기화가 안될수도있다.)


**3. 깃허브 세팅 및 비주얼 스튜디오로 깃허브연동**

   - Project Settings - Mode - Visible Meta Files 로 바꾼다.
  >메타파일 을 다 텍스트 형식으로 올려줘야한다
  - Project Settings - Asset Serialization - Mode - Force Text 로 바꾼다.
  > 역시나 텍스트 기반으로 버전관리해서 해줘야한다.

  - Assets - Open C# Project 로 비주얼 스튜디오 를 열어준다.

  -	깃을 만들어준다. git create Git Repository (주의 일단 로컬에 만 깃을 만드는것 추천)

  - 이때 Ignore 파일을 Unity 용으로 해준다. 문제는 이렇게 첫 커밋을 날리면 비주얼 스튜디오가 자동으로 파일을 쭉올려버린다.
> 그냥 커밋하면 문제는 에셋이 자동으로 모두 올라간다. 
<br>이러면 라이센스 문제등이 생길 수도있고 파일이 너무 커진다.

  - 그래서 reset으로 ignore 파일 추가한쪽으로 돌아가주자(-mixed)
  
  - 올리면 안되는 것들을 unity ignore로 추가하여 커밋한다.

  
**안올리는 것들 은 아래의 예시를 확인하자.**

1. 다운 받은 모델이나 소스 , 에셋들은 (Imports/Resources) 임의의 폴더안에 넣고 Ignore에 추가해주자.

2. UserSettings 폴더도 제외해주자. (요즘 비주얼스튜디오는 자동으로 해준다)
	> 본인 이쓰는 단축키 등이 들어있다.

3. 만약 유니티 버전 을 무시하고싶으면 버전컨트롤세팅도 제외하자.

4. 깃허브에서 소스파일을 유니티로 연결하기
	- 파일을 다운 받거나 비주얼스튜디오로 열기를 선택한다.
	- 그후 유니티 허브를 키고 Open 을 눌러서 이미있는 프로젝트 열기를 해준다.
	- 그렇게 실행시키면 기본 유니티 라이브러리 등 이 자동으로 임포트 된다.
	- 추가로 에셋들이 필요한 것은 따로 받아서 넣어준다.
	> 이때 패키지 형태로 이동시키면 편하다. 
	><br> Assets - import package , Export Package 이용

