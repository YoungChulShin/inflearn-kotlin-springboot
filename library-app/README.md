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

JOSN - 객체 매핑 에러
```kotlin
Resolved [org.springframework.http.converter.HttpMessageNotReadableException: JSON parse error: Cannot construct instance of `com.group.libraryapp.dto.book.request.BookRequest` (although at least one Creator exists): cannot deserialize from Object value (no delegate- or property-based Creator); nested exception is com.fasterxml.jackson.databind.exc.MismatchedInputException: Cannot construct instance of `com.group.libraryapp.dto.book.request.BookRequest` (although at least one Creator exists): cannot deserialize from Object value (no delegate- or property-based Creator)<EOL> at [Source: (org.springframework.util.StreamUtils$NonClosingInputStream); line: 1, column: 2]]
```
- jackson-module-kotlin
   - https://github.com/FasterXML/jackson-module-kotlin
   - jackson 역직렬화를 위해서 기본 생성자가 꼭 있어야했던 부분을 지원해주는 모듈