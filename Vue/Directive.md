##### : "v-" 접두사가 있는 특수 속성. 

+ value가 변경될 때 특정 효과를 [[DOM]]에 적용한다. 

##### ==v-bind== : 하나 이상의 속성 or 컴포넌트 데이터를 표현식에 동적으로 바인딩
1. **Attribute Bindings**
	+ HTML의 속성 값을 Vue의 상태 속성 값과 동기화 되도록 함 (ex. `<a v-bind:herf="myUrl"> Move to url</a>`)
	+ **`:`** 으로 대체 가능 (ex. `<a :herf="myUrl"> Move to url</a>`)
	+ 해당 코드 뒤에 오는 Argument 는 [[props]] 
	+ 동적 속성 이름 (Dynamic attribute name) -> (ex. `<a :[key]="myUrl"> Move to url</a>`)
	+ 여러 속성 바인딩 
		``` vue 
		const objectOfAttrs = {
			id: 'container',
			class: 'wrapper',
			style: 'background-color:green'
		}
		<div v-bin="objectOfAttrs"> </div>
		```

2. **Class and Style Bindings**
	+ Attribute 바인딩은 번거롭고 오류가 발생하기 쉬움 => **객체** 또는 **배열**을 활용하여 개선

##### ==v-on== : DOM 요소에 이벤트 리스너를 연결 및 수신 
+ `v-on:event ="handler"`
+ **handler**
	+ Inline handlers :  이벤트가 트리거 될 때 실행될 JavaScript 코드
	+ Method handlers : 컴포넌트에 정의된 메서드 이름 (DOM Event 객체를 자동으로 수신)
+ `@` 으로 대체 가능 (ex. `@event="handler"`)
