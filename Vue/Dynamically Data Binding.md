#### 1.  **[[Attribute Bindings]]**
+ HTML의 속성 값을 Vue의 상태 속성 값과 **동기화** 되도록 함 
	+ (ex. `<a v-bind:herf="myUrl"> Move to url</a>`)
+ **`:`** 으로 대체 가능 
	+ (ex. `<a :herf="myUrl"> Move to url</a>`)
+ 해당 코드 뒤에 오는 Argument 는 [[props]] 
+ 동적 속성 이름 (Dynamic attribute name)
	+ 대괄호로 표현
	+ (ex. `<a :[key]="myUrl"> Move to url</a>`)
+ 여러 속성 바인딩 
``` vue 
	const objectOfAttrs = {
		id: 'container',
		class: 'wrapper',
		style: 'background-color:green'
	}
	
	<div v-bin="objectOfAttrs"> </div>
```

#### 2. **Class and Style Bindings**
+ Attribute 바인딩은 번거롭고 오류가 발생하기 쉬움 => **객체** 또는 **배열**을 활용하여 개선
+ **Binding HTML classes**
	+ 객체를 `:class` 에 전달하여 클래스를 동적으로 전달할 수 있음 
``` html
const isActive = ref(false)

<div :class="{active: isActive }"> Text </div>
```

``` html
const isActive = ref(false)
const hasInfo = ref(true)

<div class="static" :class = "{active: isActive, 'text-primary': hasInfo }"> Text </div>

<!-- 실제 랜더링 되는 html -->
<div class = "static text-primary"> Text </div>
```

``` html
const isActive = ref(false)
const hasInfo = ref(true)

<!--반응형 변수 활용 -->
const classObj = ref({
	active: isActive,
	'text-primary': hasInfo
})

<div class="static" :class = "classObj"> Text </div>

<!-- 실제 랜더링 되는 html -->
<div class = "static text-primary"> Text </div>
```

``` html
const activeClass = ref('active')
const infoClass = ref('text-primary')

<div :class="[activeClass, infoClass]"> Text </div>
<div :class="[{active: isActive}, infoClass]"> Text </div> 
```

 + **Binding Inline styles**
``` html
const activeColor = ref('crimson')
const fontSize = ref(50)

<div :style="{color: activeColor", fontSize: fontSize + 'px'}"> Text </div>
<!-- 'font-size' : fontSize <- 이 방식도 지원! -->
```

``` html
const styleObj = ref({
	color: activeColor,
	fontSize: fontSize.value + 'px'
})

<div :style="styleObj"> Text </div>
```

``` html
const styleObj2 = ref({
	color: 'blue',
	border: `1px solid black`
})

<div :style="[styleObj, styleObj2]"> Text </div>

<!-- 실제 랜더링 되는 html -->
<div style="color: blue; font-size: 50px; border: 1px solid black;"> </div>
```