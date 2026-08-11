# Deep copy, shallow copy

[12. 얕은 복사(shallow copy)와 깊은 복사(deep copy)](https://wikidocs.net/16038)

1. shwallow cpy (얕은 복사)
    
    얕은 복사는 객체의 1차 구조만 복사하고, 내부에 있는 중첩 객체는 원본과 같은 참조를 공유한다.
    
    `copy.copy()` 또는 `list()`, `[:]` 등을 사용
    
    ```python
    import copy
    
    original = [[1, 2], [3, 4]]
    shallow = copy.copy(original)
    
    shallow[0][0] = 999
    
    print("Original:", original) # Original: [[999, 2], [3, 4]]
    print("Shallow:", shallow) # Shallow: [[999, 2], [3, 4]]
    ```
    
    `int`, `str`, `float` 등 불변 객체(immutable)로 구성된 리스트라면 **참조는 같지만 값은 바뀌지 않음**
    
    ```python
    a = [1, 2, 3]
    b = a[:]
    
    id(a) #4396179528
    id(b) #4393788808
    
    print(a == b) #True
    print(a is b) #False
    
    b[0] = 5
    
    print(a) #[1, 2, 3]
    print(b) #[5, 2, 3]
    ```
    
    - 여기서 `a[:]`는 **shallow copy**를 수행합니다.
    - `a`와 `b`는 **리스트 객체 자체는 서로 다른 id**를 가집니다.
    - 그러나 각 요소 `1`, `2`, `3`은 불변 객체이기 때문에, `a[0]`, `b[0]`은 **동일한 int 객체를 참조**합니다.
    
    이후 `b[0] = 5` 를 실행하면:
    
    - `b[0]`의 참조가 1 → 5로 바뀔 뿐이고,
    - `a[0]`은 여전히 1을 참조합니다.
    
    따라서 `a`와 `b`는 서로 영향받지 않습니다.
    
    1. Deep copy(깊은 복사)
        
        깊은 복사는 객체들까지 모두 새롭게 복사한다.
        
        원본과 복사본은 완전히 다른 독립된 객체이다.
        
        ```python
        import copy
        
        original = [[1, 2], [3, 4]]
        deep = copy.deepcopy(original)
        
        deep[0][0] = 999
        
        print("Original:", original) # Original: [[1, 2], [3, 4]]
        print("Deep:", deep) # Deep: [[999, 2], [3, 4]]
        ```
        
        독립적인 객체이므로 `original`에는 영향이 없다.
