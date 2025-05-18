##### : 소스 데이터를 기반으로 요소 또는 템플릿 블록을 여러 번 렌더링 
+ Array, Object, Number, String, Iterable
+ 중첩 v-for 가능
+ 반드시 **key**를 같이 사용
+ [[v-if]] 를 같이 사용하지 **않는다**!
``` html
const myArr = ref([
	{name: 'Alice', age: 20},
	{name: 'Bella', age: 21}
])

<div v-for="(item, index) in myArr">
	{{index}} / {{item}} <!-- [Object]로 출력됨 -->
	{{item.name}} <!-- 값이 출력됨 -->
</div>
```

### Key
##### : 내부 컴포넌트의 상태를 일관되게 유지
``` html
<div v-for="item in items" :key="item.id"> </div>
```
!! 배열의 index를 key로 사용하지 말 것!

+ index는 식별자가 아닌 배열의 항목 위치만 나타내기 때문에 Vue가 DOM을 변경할 때 문제 발생
	+ 끝이 아닌 위치에 새 항목이 삽입될 경우, 컴포넌트 간 데이터 공유 시 문제 발생

#### `v-if`를 사용하지 않고, `v-for`에서 원하는 원소만 출력하는 방법
1. computed를 활용해 필터링 된 목록을 반환하여 반복하도록 설정 
2. template 요소를 사용하여 `v-if`의 위치를 for문 내부로 이동 
``` html
<ul>
	<template v-for="todo in todos" :key="todo.id">
		<li v-if="todo.isComplete">
			{{todo.name}}
		</li>
	</template>
</ul>
```