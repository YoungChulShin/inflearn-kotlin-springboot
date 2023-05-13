# 저장소 설명
인프런 `실전! 코틀린과 스프링 부트로 도서관리 애플리케이션 개발하기` 실습 저장소

# 메모 
### `JvmStatic` 애노테이션 사용
companion object에 선언된 함수를 java의 static과 동일하게 변환되도록 할 때 사용

### Entity 생성시 id 같은 null 항목 처리
방법 1. null 항목은 생성자의 뒤로 보낸다

방법 2. 클래스 내에서 선언한다

### `var` 키워드 사용
생성자에 들어가는 var는 public setter가 생성되기 때문에 주의해야한다. 

팀 내 규칙으로 이를 사용하지만, setter를 사용하지 않도록 협의하는 방법도 있고, `_`를 사용해서 `private var`로 선언하는 방법도 있다. 
```kotlin
@Entity
class TestEntity(
    private var _isReturn: Boolean,
) {
    val isReturn: Boolean
        get() = this._isReturn

    fun doReturn() {
        this._isReturn = true
    }
}
```