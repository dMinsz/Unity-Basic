# Unity Basic Functions And Usages

유니티를 사용할때 기본적으로 알아야하는 함수들과 설명

## 목차

* [GameObject 관련 함수들](#GameObject-관리)
* [입력 관련 함수들](#사용자-입력-관련-함수)

## GameObject 관리

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

gameObject는 유니티의 모든 컴포넌트가 포함하고있다. (MonoBehaviour 를 상속하기때문)

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


## 2. Find(strign name)

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

FindGameObjectWithTag 함수를 사용하여 태그 기준으로도 찾을 수 있다.


## 3. Desroty(object)

```cs
Destroy(destroyGameObject);
```
destroyGameObject 는 삭제할 오브젝트의 변수명이다.

매개변수를 object 라고 해둔 이유는 매개변수로 오브젝트들을 받을수 있어서이다.

> Unity 오브젝트들은 모두 매개변수로 들어 갈 수있다.

이를 통해 스크립트에서 오브젝트를 삭제 할 수 있다.

>당연히 new 를 통해 게임 오브젝트를 생성 할 수 있다.

```cs
Destroy(destroyGameObject , 5f);
```

5초 후에 삭제 하는 방식 도 있다.


## 4. GetComponent<T>()

T => 가져올 컴포넌트의 클래스를 뜻한다. (제네릭 방식)

기본적으로 [오브젝트].GetComponent<T>() 형식으로 사용하며

오브젝트 안에 있는 컴포넌트 기준으로 값을 가져온다.

```cs
//중략..
		// GetComponent를 이용하여 게임오브젝트 내 컴포넌트 접근
		gameObjectGetComponent = GetComponent<AudioSource>();
		// 컴포넌트에서 GetComponent를 사용할 경우 부착되어 있는 게임오브젝트를 기준으로 접근
		componentGetComponent = GetComponent<AudioSource>();    // == gameObject.GetComponent<AudioSource>();

		component = otherGameObject.GetComponent<AudioSource>();					// 게임오브젝트의 컴포넌트 접근
		components = otherGameObject.GetComponents<AudioSource>();					// 게임오브젝트의 컴포넌트들 접근
		childComponent = otherGameObject.GetComponentInChildren<AudioSource>();		// 자식 게임오브젝트 포함 컴포넌트 접근
		childComponents = otherGameObject.GetComponentsInChildren<AudioSource>();	// 자식 게임오브젝트 포함 컴포넌트들 접근
		parentComponent = otherGameObject.GetComponentInParent<AudioSource>();		// 부모 게임오브젝트 포함 컴포넌트 접근
		parentComponents = otherGameObject.GetComponentsInParent<AudioSource>();	// 부모 게임오브젝트 포함 컴포넌트들 접근

		// <씬 내의 컴포넌트 탐색>
		findWithType = FindObjectOfType<Rigidbody>();								// 씬 내의 컴포넌트 하나 찾기
		findsWithType = FindObjectsOfType<Rigidbody>();								// 씬 내의 컴포넌트 모두 찾기

		// <컴포넌트 추가>
		// Rigidbody rigid = new Rigidbody();	// 가능하나 의미없음, 컴포넌트는 게임오브젝트에 부착되어 동작함에 의미가 있음
		Rigidbody rigid = addComponent.AddComponent<Rigidbody>();					// 게임오브젝트에 컴포넌트 추가

		// <컴포넌트 삭제>
		Destroy(destroyComponent);
//중략..
```

[Object].AddComponenet<T>();

AddComponenet 함수를 사용하면 스크립트 내에서 Object에 T 컴포넌트를 추가해줄 수 있다.


## 사용자 입력 관련 함수

사용자는 외부 장치를 이용하여 게임을 제어할 수 있음

유니티는 다양한 타입의 입력기기(키보드 및 마우스, 조이스틱, 터치스크린 등)를 지원한다.


## 특정한 장치를 기준으로 입력 감지

특정한 장치의 입력을 감지하기 때문에 여러 플랫폼에 대응이 어려움

### Input.GetKey , Input.GetMouseButton 함수들

```cs
		// 키보드의 입력감지
		if (Input.GetKey(KeyCode.Space)) // 스페이스 입력 확인
			Debug.Log("Space key is pressing");
		if (Input.GetKeyDown(KeyCode.Space))// 스페이스 가 눌린 순간
			Debug.Log("Space key is down");
		if (Input.GetKeyUp(KeyCode.Space))// 스페이스 가 눌리고 나서 땐 순간
			Debug.Log("Space key is up");

		// 마우스의 입력감지
		if (Input.GetMouseButton(0))
			Debug.Log("Mouse left button is pressing");
		if (Input.GetMouseButtonDown(0)) // 눌린 순간
			Debug.Log("Mouse left button is down");
		if (Input.GetMouseButtonUp(0)) // 땐 순간
			Debug.Log("Mouse left button is up");
```

## 여러 장치의 입력을 <입력매니저>를 통해 입력 감지

**InputManager**

여러 장치의 입력을 입력매니저에 이름과 입력을 정의
	
입력매니저의 이름으로 정의한 입력의 변경사항을 확인
	
유니티 에디터의 Edit -> Project Settings -> Input Manager 에서 관리

```cs
	private void InputByInputManager()
	{
		// 버튼 입력
		// Fire1 : 키보드(Left Ctrl), 마우스(Left Button), 조이스틱(button0)으로 정의됨
		if (Input.GetButton("Fire1"))
			Debug.Log("Fire1 is pressing");
		if (Input.GetButtonDown("Fire1"))
			Debug.Log("Fire1 is down");
		if (Input.GetButtonUp("Fire1"))
			Debug.Log("Fire1 is up");

		// 축 입력
		// Horizontal(수평) : 키보드(a,d / ←, →), 조이스틱(왼쪽 아날로그스틱 좌우)
		float x = Input.GetAxis("Horizontal");
		// Vertical(수직) : 키보드(w,s / ↑, ↓), 조이스틱(왼쪽 아날로그스틱 상하)
		float y = Input.GetAxis("Vertical");
	}
```

## 여러 장치의 입력을 <입력 시스템>을 통해 입력 감지

**InputSystem**

Unity 2019.1 부터 지원하게 된 입력방식

컴포넌트를 통해 입력의 변경사항을 확인

GamePad, JoyStick, Mouse, Keyboard, Pointer, Pen, TouchScreen, XR 기기 등을 지원

```cs
	private void InputByInputSystem()
	{
		// InputSystem은 이벤트 방식으로 구현됨
		// Update마다 입력변경사항을 확인하는 방식 대신 변경이 있을 경우 이벤트로 확인
		// 메시지를 통해 받는 방식과 이벤트 함수를 직접 연결하는 방식 등으로 구성
	}

	// Move 입력에 반응하는 OnMove 메시지 함수
	private void OnMove(InputValue value)
	{
		Vector2 input = value.Get<Vector2>();
	}
```