# Unity Basic Functions

����Ƽ�� ����Ҷ� �⺻������ �˾ƾ��ϴ� �Լ���� ����

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

gameObject�� ����Ƽ�� ��� ������Ʈ�� �����ϰ��ִ�.

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


## 2. Find()

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

�߰��� �±׷ε� ã�� �� �ִ�.


## 3. Desroty()

```cs
Destroy(destroyGameObject);
```
destroyGameObject �� ������ ������Ʈ�� �������� ��.

�̸� ���� ��ũ��Ʈ���� ������Ʈ�� ���� �� �� �ִ�.

>�翬�� new �� ���� ���� ������Ʈ�� ���� �� �� �ִ�.

```cs
Destroy(destroyGameObject , 5f);
```

5�� �Ŀ� ���� �ϴ� ��� �� �ִ�.



