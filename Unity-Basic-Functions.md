# Unity Basic Functions

유니티를 사용할때 기본적으로 알아야하는 함수들과 설명

## 1. gameObject 

```cs
public class UnityBasic : MonoBehaviour
{
	[Header("This GameObject")]
	public GameObject thisGameObject;
	
	private void Start()
	{
		GameObjectBasic();
	}

	void GameObjectBasic()
	{
		// <게임오브젝트 접근>
		// 컴포넌트가 붙어있는 게임오브젝트는 gameObject 속성을 이용하여 접근가능
		thisGameObject = gameObject;                // 컴포넌트가 붙어있는 게임오브젝트
	}
}
```

gameObject는 유니티의 모든 컴포넌트가 포함하고있다.

위 코드는 해당 오브젝트가 start 할때 본인 스스로를 게임오브젝트를 세팅했지만

굳이 그렇게 안해도 gameObject로 접근가능하다.

**게임오브젝트 구성요소**

게임오브젝트에서 접근가능한 속성들

- name			: 게임오브젝트의 이름
- active		: 게임오브젝트의 활성화 여부, 비활성화인 경우 씬에 없는 게임오브젝트로 취급됨
- static		: 게임오브젝트의 정적상태 여부, 런타임 당시 변경되지 않는 데이터를 지정하여 최적화
- tag			: 게임오브젝트의 태그, 게임오브젝트를 특정하기 위한 수단으로 사용
- layer		: 게임오브젝트의 레이어, 씬에서 게임오브젝트를 분리하는 기준 (카메라의 선별적 표현, 충돌 그룹, 레이어 마스크 등에 사용)
- component	: 게임오브젝트에 포함된 기능모듈, 게임오브젝트는 컴포넌트를 담기위한 컨테이너 역할


## 2. Find()

```cs
		//..중략
		// <씬 내의 게임오브젝트 탐색>
		findWithName = GameObject.Find("FindGameObject");           // 이름으로 찾기
		findWithTag = GameObject.FindGameObjectWithTag("MyTag");    // 태그로 하나 찾기
		findsWithTag = GameObject.FindGameObjectsWithTag("MyTag");	// 태그로 모두 찾기
		//..중략
```
Find 함수는 이름 기준(GameObject의 name 속성)으로 해당하는 오브젝트를 찾는다.

만약 이름이 똑같으면 가장 먼저 찾은 객체를 돌려준다.

추가로 태그로도 찾을 수 있다.


## 3. Desroty()

```cs
Destroy(destroyGameObject);
```
destroyGameObject 는 삭제할 오브젝트의 변수명이 다.

이를 통해 스크립트에서 오브젝트를 삭제 할 수 있다.

>당연히 new 를 통해 게임 오브젝트를 생성 할 수 있다.

```cs
Destroy(destroyGameObject , 5f);
```

5초 후에 삭제 하는 방식 도 있다.



