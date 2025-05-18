##### : 자식 컴포넌트가 이벤트를 발생시켜 부모 컴포넌트로 데이터를 전달하는 역할의 메서드 
+ `$emit()`으로 직접 사용자 정의 이벤트를 발신
	+ `<button @click="$emit('someEvent')">클릭 </button>`
+ 부모는 [[v-on]]을 사용하여 수신할 수 있음(`@`)
	+ `ParentComp @some-event="someCallback" />`

``` js
$emit(evnet, ...args)
```
+ event : 커스텀 이벤트 이름
+ args : 추가 인자 

`defineEmits()` -> 명시적으로 발신 할 이벤트를 선언할 수 있음

``` js
<!--ParentChild.vue -->
const emit = defineEmits(['someEvent', 'emitArgs'])

const emitArges = finction() {
	emit('emitArgs', 1, 2, 3)
}
```
``` js
<!-- Parent.vue -->
<ParentChild 
	@some-event="someCallback"
	@emit-args="getNumbers"
	my-msg="message"
	:dynamic-props="name"
/>

const getNumbers = function (...args) {
	console.log(args)
}
```