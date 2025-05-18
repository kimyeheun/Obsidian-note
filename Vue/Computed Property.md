##### : 계산된 속성을 정의하는 함수 
+ 미리 계산된 속성을 사용하여 템플릿에서 표현식을 단순하게 하고 불필요한 반복 연산을 줄임

+ 반환 되는 값은 **computed ref**
 이며, 일반 refs와 유사하게 계산된 결과를 `.value`로 참조 할 수 있음
+ computed 속성은 의존된 반응형 데이터를 **자동으로 추적** 
#### vs Methods 
+ 의존하는 데이터에 따라 결과가 바뀌는 계산된 속성을 만들 때 유용 
+ 동일한 의존성을 가진 여러 곳에서 사용 시, 중복 계산 방지 ([[Cache]] 사용)
	+ 즉, 의존된 반응형 데이터가 변경되지 않는 한 이미 계산된 결과에 대해 여러 참조는 즉시 반환된다. 
#### vs Watchers
+ 의존하는 데이터 속성의 계산된 값을 반환
+ 템플릿 내에서 사용되는 데이터 연산용
+ 연산 된 길이, 필터링 된 목록 계산 등에 사용됨

##### 유사한 기능
+ [[Methods]] : 계산된 속성을 반환한다는 점에서 유사함.
+ [[Watchers]] : 데이터의 변화를 감지하고 처리한다는 점에서 유사함.

### 사용 예시 
``` html
const todos = ref([
	{text: 'Vue 실습'},
	{text: '자격증 공부'},
	{text: 'TIL 작성'}
])

<p> {{todos.length > 0 ? '아직 남았다' : '퇴근'}} </p> <!-- 반복 연산이 이루어짐!! -->
```
#### computed 적용 
``` html
const {createApp, ref, computed } = Vue

const restOfTodos = computed(() = > {
	return todos.value.length > 0 ? '아직 남았다' : '퇴근!'
})

<p>{{restOfTodos}}</p>
```

### 주의 사항
#### computed의 반환 값은 변경하지 말 것. 
+ 일종의 snapshot. 
+ 의존하는 데이터가 변경될 때마다 새로운 snapshot 이 생성된다. 
+ 계산된 반환 값은 읽기 전용!!
	`const sum = computed(() => a.value + b.value)`
	`sum.value = 10`   -> 오류!! 
#### computed 사용 시 원본 배열 변경하지 말 것
+ `reverse()` 및 `sort()` 사용 시 원본 배열을 변경하기 때문에 복사본을 만들어야 함
+ `return numbers.reverse()`  -> 안됨!
+ `return [...numbers].reverse()`  // 복사 
