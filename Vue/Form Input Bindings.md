##### : 양방향 바인딩. form을 처리할 때 사용자가 input에 입력하는 값을 실시간으로 JS 상태에 동기화 해야 하는 경우
#### HOW?
1. [[v-bind]]와 [[v-on]]을 함께 사용
	+ `v-bind` 를 사용하여 input 요소의 value 속성 값을 입력 값으로 사용 
	+ `v-on` 을 사용하여 input 이벤트가 발생할 때마다 input 요소의 value값을 별도 반응형 변수에 저장하는 핸들러 호출 
``` html
const inputText = ref('')
const onInput = function(event) {
	inputText.value = event.currentTarget.value
}

<p> {{inputText}} </p>
<input :value="inputText" @input="onInput">
```
2. [[v-model]] 사용 (내부적으로 1번 방식을 사용한 것이긴 함)
	+ **form input** 요소 또는 **컴포넌트**에서 양방향 바인딩을 만듦
	+ IME(Input Method Editor)가 필요한 언어(한, 중, 일 등)의 경우 v-model이 제대로 업데이트 되지 않음
``` html
const inputText = ref('')

<p> {{inputText}} </p>
<input v-model="inputText">
```
+ checkbox, radio, select 같이 사용 가능 
``` html 
const checked =  ref(false)
<inut type="checkbox" id="checkbox" v-model="checked">

const checkedNames =  ref([]])
<inut type="checkbox1" id="checkbox1" value="A" v-model="checkedNames">
<inut type="checkbox2" id="checkbox2" value="B" v-model="checkedNames">
```
+ v-model의 표현식의 초기 값이 어떤 option과도 일치하지 않는 경우 select 요소는 "선택되지 않은" 상태로 렌더링 됨
``` html 
const selected = ref('')

<select v-model="selected">
	<option disabled value=""> Please select one </option>
	<option> A </option>
	<option> B </option>
	<option> C </option>
</select>
```

