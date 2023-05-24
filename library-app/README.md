# 메모
확장 함수를 기존의 함수를 한번 더 래핑해서 기능을 추가할 수 있다
```kt
fun fail(): Nothing {
    throw IllegalArgumentException()
}

// findByIdOrNull의 기능을 확장한다
fun <T, ID> CrudRepository<T, ID>.findByIdOrThrow(id: ID): T {
    return this.findByIdOrNull(id) ?: fail()
}
```

객체 생성
1. 생성자
2. 추가 생성자
3. Companion Object 내에서 확장 생성자