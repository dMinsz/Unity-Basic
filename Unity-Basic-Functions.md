# Unity Basic Functions And Usages

����Ƽ�� ����Ҷ� �⺻������ �˾ƾ��ϴ� �Լ���� ����

## ����

* [GameObject ���� �Լ���](#GameObject-����)
* [�Է� ���� �Լ���](#�����-�Է�-����-�Լ�)
* [TransForm](#Transform-Functions)

## GameObject ����

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
		// <���ӿ�����Ʈ ����>
		// ������Ʈ�� �پ��ִ� ���ӿ�����Ʈ�� gameObject �Ӽ��� �̿��Ͽ� ���ٰ���
		thisGameObject = gameObject;                // ������Ʈ�� �پ��ִ� ���ӿ�����Ʈ
	}
}
```

gameObject�� ����Ƽ�� ��� ������Ʈ�� �����ϰ��ִ�. (MonoBehaviour �� ����ϱ⶧��)

�� �ڵ�� �ش� ������Ʈ�� start �Ҷ� ���� �����θ� ���ӿ�����Ʈ�� ����������

���� �׷��� ���ص� gameObject�� ���ٰ����ϴ�.

**���ӿ�����Ʈ �������**

���ӿ�����Ʈ���� ���ٰ����� �Ӽ���

- name			: ���ӿ�����Ʈ�� �̸�
- active		: ���ӿ�����Ʈ�� Ȱ��ȭ ����, ��Ȱ��ȭ�� ��� ���� ���� ���ӿ�����Ʈ�� ��޵�
- static		: ���ӿ�����Ʈ�� �������� ����, ��Ÿ�� ��� ������� �ʴ� �����͸� �����Ͽ� ����ȭ
- tag			: ���ӿ�����Ʈ�� �±�, ���ӿ�����Ʈ�� Ư���ϱ� ���� �������� ���
- layer		: ���ӿ�����Ʈ�� ���̾�, ������ ���ӿ�����Ʈ�� �и��ϴ� ���� (ī�޶��� ������ ǥ��, �浹 �׷�, ���̾� ����ũ � ���)
- component	: ���ӿ�����Ʈ�� ���Ե� ��ɸ��, ���ӿ�����Ʈ�� ������Ʈ�� ������� �����̳� ����


## 2. Find(strign name)

```cs
		//..�߷�
		// <�� ���� ���ӿ�����Ʈ Ž��>
		findWithName = GameObject.Find("FindGameObject");           // �̸����� ã��
		findWithTag = GameObject.FindGameObjectWithTag("MyTag");    // �±׷� �ϳ� ã��
		findsWithTag = GameObject.FindGameObjectsWithTag("MyTag");	// �±׷� ��� ã��
		//..�߷�
```
Find �Լ��� �̸� ����(GameObject�� name �Ӽ�)���� �ش��ϴ� ������Ʈ�� ã�´�.

���� �̸��� �Ȱ����� ���� ���� ã�� ��ü�� �����ش�.

FindGameObjectWithTag �Լ��� ����Ͽ� �±� �������ε� ã�� �� �ִ�.


## 3. Desroty(object)

```cs
Destroy(destroyGameObject);
```
destroyGameObject �� ������ ������Ʈ�� �������̴�.

�Ű������� object ��� �ص� ������ �Ű������� ������Ʈ���� ������ �־�̴�.

> Unity ������Ʈ���� ��� �Ű������� ��� �� ���ִ�.

�̸� ���� ��ũ��Ʈ���� ������Ʈ�� ���� �� �� �ִ�.

>�翬�� new �� ���� ���� ������Ʈ�� ���� �� �� �ִ�.

```cs
Destroy(destroyGameObject , 5f);
```

5�� �Ŀ� ���� �ϴ� ��� �� �ִ�.


## 4. GetComponent<T>()

T => ������ ������Ʈ�� Ŭ������ ���Ѵ�. (���׸� ���)

�⺻������ [������Ʈ].GetComponent<T>() �������� ����ϸ�

������Ʈ �ȿ� �ִ� ������Ʈ �������� ���� �����´�.

```cs
//�߷�..
		// GetComponent�� �̿��Ͽ� ���ӿ�����Ʈ �� ������Ʈ ����
		gameObjectGetComponent = GetComponent<AudioSource>();
		// ������Ʈ���� GetComponent�� ����� ��� �����Ǿ� �ִ� ���ӿ�����Ʈ�� �������� ����
		componentGetComponent = GetComponent<AudioSource>();    // == gameObject.GetComponent<AudioSource>();

		component = otherGameObject.GetComponent<AudioSource>();					// ���ӿ�����Ʈ�� ������Ʈ ����
		components = otherGameObject.GetComponents<AudioSource>();					// ���ӿ�����Ʈ�� ������Ʈ�� ����
		childComponent = otherGameObject.GetComponentInChildren<AudioSource>();		// �ڽ� ���ӿ�����Ʈ ���� ������Ʈ ����
		childComponents = otherGameObject.GetComponentsInChildren<AudioSource>();	// �ڽ� ���ӿ�����Ʈ ���� ������Ʈ�� ����
		parentComponent = otherGameObject.GetComponentInParent<AudioSource>();		// �θ� ���ӿ�����Ʈ ���� ������Ʈ ����
		parentComponents = otherGameObject.GetComponentsInParent<AudioSource>();	// �θ� ���ӿ�����Ʈ ���� ������Ʈ�� ����

		// <�� ���� ������Ʈ Ž��>
		findWithType = FindObjectOfType<Rigidbody>();								// �� ���� ������Ʈ �ϳ� ã��
		findsWithType = FindObjectsOfType<Rigidbody>();								// �� ���� ������Ʈ ��� ã��

		// <������Ʈ �߰�>
		// Rigidbody rigid = new Rigidbody();	// �����ϳ� �ǹ̾���, ������Ʈ�� ���ӿ�����Ʈ�� �����Ǿ� �����Կ� �ǹ̰� ����
		Rigidbody rigid = addComponent.AddComponent<Rigidbody>();					// ���ӿ�����Ʈ�� ������Ʈ �߰�

		// <������Ʈ ����>
		Destroy(destroyComponent);
//�߷�..
```

[Object].AddComponenet<T>();

AddComponenet �Լ��� ����ϸ� ��ũ��Ʈ ������ Object�� T ������Ʈ�� �߰����� �� �ִ�.


## ����� �Է� ���� �Լ�

����ڴ� �ܺ� ��ġ�� �̿��Ͽ� ������ ������ �� ����

����Ƽ�� �پ��� Ÿ���� �Է±��(Ű���� �� ���콺, ���̽�ƽ, ��ġ��ũ�� ��)�� �����Ѵ�.


## Ư���� ��ġ�� �������� �Է� ����

Ư���� ��ġ�� �Է��� �����ϱ� ������ ���� �÷����� ������ �����

### Input.GetKey , Input.GetMouseButton �Լ���

```cs
		// Ű������ �Է°���
		if (Input.GetKey(KeyCode.Space)) // �����̽� �Է� Ȯ��
			Debug.Log("Space key is pressing");
		if (Input.GetKeyDown(KeyCode.Space))// �����̽� �� ���� ����
			Debug.Log("Space key is down");
		if (Input.GetKeyUp(KeyCode.Space))// �����̽� �� ������ ���� �� ����
			Debug.Log("Space key is up");

		// ���콺�� �Է°���
		if (Input.GetMouseButton(0))
			Debug.Log("Mouse left button is pressing");
		if (Input.GetMouseButtonDown(0)) // ���� ����
			Debug.Log("Mouse left button is down");
		if (Input.GetMouseButtonUp(0)) // �� ����
			Debug.Log("Mouse left button is up");
```

## ���� ��ġ�� �Է��� <�Է¸Ŵ���>�� ���� �Է� ����

**InputManager**

���� ��ġ�� �Է��� �Է¸Ŵ����� �̸��� �Է��� ����
	
�Է¸Ŵ����� �̸����� ������ �Է��� ��������� Ȯ��
	
����Ƽ �������� Edit -> Project Settings -> Input Manager ���� ����

```cs
	private void InputByInputManager()
	{
		// ��ư �Է�
		// Fire1 : Ű����(Left Ctrl), ���콺(Left Button), ���̽�ƽ(button0)���� ���ǵ�
		if (Input.GetButton("Fire1"))
			Debug.Log("Fire1 is pressing");
		if (Input.GetButtonDown("Fire1"))
			Debug.Log("Fire1 is down");
		if (Input.GetButtonUp("Fire1"))
			Debug.Log("Fire1 is up");

		// �� �Է�
		// Horizontal(����) : Ű����(a,d / ��, ��), ���̽�ƽ(���� �Ƴ��α׽�ƽ �¿�)
		float x = Input.GetAxis("Horizontal");
		// Vertical(����) : Ű����(w,s / ��, ��), ���̽�ƽ(���� �Ƴ��α׽�ƽ ����)
		float y = Input.GetAxis("Vertical");
	}
```

## ���� ��ġ�� �Է��� <�Է� �ý���>�� ���� �Է� ����

**InputSystem**

Unity 2019.1 ���� �����ϰ� �� �Է¹��

**����Ƽ ��Ű�� �Ŵ������� unity Resistry �� InputSystem �� ��ġ�� �ָ� ��밡���ϴ�.**

������Ʈ�� ���� �Է��� ��������� Ȯ��

GamePad, JoyStick, Mouse, Keyboard, Pointer, Pen, TouchScreen, XR ��� ���� ����

> ����Ƽ ���½��� Oculus Integration ������ �̿��ص� ��ŧ���� vr �� �Է¸Ŵ����� ��밡�� �ϰ� ����������
><br/> ������Ʈ ���� �Ǿ��� ������ �ΰ��� �˾Ƶ־��Ѵ�.



```cs
	private void InputByInputSystem()
	{
		// InputSystem�� �̺�Ʈ ������� ������
		// Update���� �Էº�������� Ȯ���ϴ� ��� ��� ������ ���� ��� �̺�Ʈ�� Ȯ��
		// �޽����� ���� �޴� ��İ� �̺�Ʈ �Լ��� ���� �����ϴ� ��� ������ ����
	}

	// Move �Է¿� �����ϴ� OnMove �޽��� �Լ�
	private void OnMove(InputValue value)
	{
		Vector2 input = value.Get<Vector2>();
	}
```

### Input System ����

* ����Ƽ ��Ű�� �Ŵ������� unity Resistry �� InputSystem �� ��ġ
* �Է��� �ް����ϴ� ������Ʈ �� Component�� �߰����ش�
* Actions �� ���� ����ų� ����Ʈ�� ������ش�.

![InputSystemIamges](./Images/InputSystemActions.png)



## Transform Functions

* ���ӿ�����Ʈ�� ��ġ, ȸ��, ũ�⸦ �����ϴ� ������Ʈ
* ���ӿ�����Ʈ�� �θ�-�ڽ� ���¸� �����ϴ� ������Ʈ
* ���ӿ�����Ʈ�� �ݵ�� �ϳ��� Ʈ������ ������Ʈ�� ������ ������ �߰� & ������ �� ����

### Translate

Ʈ������ �̵�

AddForce �� �ٸ��� ��ġ�̵��̱� ������ ����, �����ϴ� ������ �����ʴ´�.

���� ������Ʈ�� ����� Ʈ������ �� ������ �ֱ⶧���� ���ٹ� ��밡���ϴ�.

Translate : Ʈ�������� �̵� �Լ�

```cs
	private void TranslateMove()
	{
		// ���͸� �̿��� �̵�
		transform.Translate(Vector3.forward * moveSpeed * Time.deltaTime);
		// x,y,z�� �̿��� �̵�
		transform.Translate(0, 0, moveSpeed * Time.deltaTime);
	}
```


Ʈ�������� �̵� ������ �����ԵǴµ�

����� �������� , ������ �������� , �ٸ� ����� �������� �̵��� �� �� �ִ�.

```cs
	private void TransformMoveSpace()
	{
		// ���带 �������� �̵�
		transform.Translate(1, 0, 0, Space.World);
		// ������ �������� �̵�
		transform.Translate(1, 0, 0, Space.Self);
		// �ٸ� ����� �������� �̵�
		transform.Translate(1, 0, 0, Camera.main.transform);
	}
```

### Ratation

Ʈ�������� ȸ��

```cs
	// <Ʈ������ ȸ��>
	// Rotate : Ʈ�������� ȸ�� �Լ�
	private void Rotate()
	{
		// ���� �̿��� ȸ�� (���� �������� �ð�������� ȸ��)
		transform.Rotate(Vector3.up, rotateSpeed * Time.deltaTime);
		// ���Ϸ��� �̿��� ȸ��
		transform.Rotate(Vector3.up * rotateSpeed * Time.deltaTime);
		// x,y,z�� �̿��� ȸ��
		transform.Rotate(0, rotateSpeed * Time.deltaTime, 0);
	}

	// <Ʈ������ ȸ�� ����>
	private void RotateSpace()
	{
		// ���带 �������� ȸ��
		transform.Rotate(1, 0, 0, Space.World);
		// ������ �������� ȸ��
		transform.Rotate(1, 0, 0, Space.Self);
		// ��ġ�� �������� ȸ��
		transform.RotateAround(Camera.main.transform.position, Vector3.up, 1);
	}
```


```cs
// <Ʈ������ LookAt ȸ��>
	// LookAt : ��ġ�� �ٶ󺸴� �������� ȸ��
	private void LookAt()
	{
		// ��ġ�� �ٶ󺸴� ȸ��
		transform.LookAt(new Vector3(0, 0, 0));
		// �Ӹ��� ������ �߰��� �ٶ󺸴� ȸ��
		transform.LookAt(new Vector3(0, 0, 0), Vector3.right);
	}
```


#### Ʈ������ �θ�-�ڽ� ����

 Ʈ�������� �θ� Ʈ�������� ���� �� ����

�θ� Ʈ�������� �ִ� ��� �θ� Ʈ�������� ��ġ, ȸ��, ũ�� ������ ���� �����

�̸� �̿��Ͽ� ������ ������ �����ϴµ� ������ (ex. ���� �����̸�, �հ����� ���� ������)

���̾��Ű â �󿡼� �巡�� & ����� ���� �θ�-�ڽ� ���¸� ������ �� ����

```cs
	private void TransformParent()
	{
		GameObject newGameObject = new GameObject() { name = "NewGameObject" };

		// �θ� ����
		transform.parent = newGameObject.transform;

		// �θ� ���������� Ʈ������
		// transform.localPosition	: �θ�Ʈ�������� �ִ� ��� �θ� �������� �� ��ġ
		// transform.localRotation	: �θ�Ʈ�������� �ִ� ��� �θ� �������� �� ȸ��
		// transform.localScale		: �θ�Ʈ�������� �ִ� ��� �θ� �������� �� ũ��

		// �θ� ����
		transform.parent = null;

		// ���带 ���������� Ʈ������
		// transform.localPosition == transform.position	: �θ�Ʈ�������� ���� ��� ���带 �������� �� ��ġ
		// transform.localRotation == transform.rotation	: �θ�Ʈ�������� ���� ��� ���带 �������� �� ȸ��
		// transform.localScale								: �θ�Ʈ�������� ���� ��� ���带 �������� �� ũ��
	}
```

### Quarternion & Euler

Quarternion	: ����Ƽ�� ���ӿ�����Ʈ�� 3���� ������ �����ϰ� �̸� ���⿡�� �ٸ� ���������� ��� ȸ������ ����

�������� ȸ������ ������ ������ �߻����� ����

EulerAngle	: 3���� �������� ���������� ȸ����Ű�� ��� 

������������ ������ ������ �߻��Ͽ� ȸ���� ��ġ�� ���� ���� �� ����
	
> ������ : ���� �������� ������Ʈ�� �� ȸ�� ���� ��ġ�� ����


Quarternion�� ���� ȸ�������� ����ϴ� ���� ���������� �ʰ� �����ϱ� �����

������ ��� ���ʹϾ� -> ���Ϸ����� -> �������� -> ������Ϸ����� -> ������ʹϾ� �� ���� ������ ��� ���ʹϾ��� �����