``` html
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div :id="`list-${id}`"></div>
```


+ Vue는 모든 데이터 바인딩 내에서 JavaScript 표현식의 모든 기능을 지원할 수 있다. 
+ Vue 템플릿에서 JS 표현식을 사용할 수 있는 위치?
	+ 중괄호 구문 내부
	+ 모든 directvie 속성 값 (== "v-"로 시작하는 특수 속성)

#### 주의 사항!
+ 각 바인딩에는 **하나의 단일 표현식**만 포함될 수 있음 (if문, 선언식 사용 불가)
