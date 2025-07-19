---
{"dg-publish":true,"permalink":"/03.Resource/Development Wiki/Development Wiki (Sources)/CSharp 인덱서/","noteIcon":"","created":"2024-10-03T17:18:16.000+09:00","updated":"2025-07-19T22:58:36.958+09:00"}
---

### 클래스를 배열처럼 동작하게 만들 수 있다
- 특징
    - 여러개 매개변수 가능
    - get, set 키워드 사용
    - 클래스, 구조체, 인터페이스에서 사용 가능
    
    ```csharp
    public class MyClass
    {
    	public List<T> myValues = new ();
    	
    	public T this[int index]
    	{
    		get => return myValues[index];
    		set => myValues[index] = value; 
    	}
    }
    ...
    public void Foo()
    {
    	myClass[0] = new T();
    }
    
    ```