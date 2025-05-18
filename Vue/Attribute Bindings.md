##### : HTML의 id 속성 값을 지정할 때 사용 

``` html
<div v-bind:id="dynamicId"> </div>

const dynamicId = ref('my-id')

<!-- 실제 랜더링 되는 html -->
<div id="my-id"></div>
```

+ [[v-bind]] 사용 ( `{{}}` 는 HTML속성 내에 사용할 수 없음)
+ 바인딩 값이 ==null이나 undefind==인 경우 렌더링 요소에서 ==**제거**==됨 