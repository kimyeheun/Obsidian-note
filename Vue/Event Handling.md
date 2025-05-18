1. **Inline handler**
	+ 이벤트가 트리거 될 때 실행될 JS 코드
``` html
const count = ref(0)

<button @click="count++">Add 1</button>
<p> Count: {{count}} </p>
```
2. **Method handler**
	+ 컴포넌트에 정의된 메서드 이름 (**DOM Event 객체를 자동으로 수신**)
``` html
const name = ref('Alice')
const myFunc = function(event) {
	console.log(event) <!-- PointerEvent -->
	console.log(event.currentTarget)
	console.log(`Hello ${name.value}!`)
}

<button @click="myFunc">Hello</button>
OR
<button @click="myFunc($event)">Hello</button>
```
