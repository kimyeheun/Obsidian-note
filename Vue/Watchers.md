##### : 반응형 데이터를 감시하고, 감시하는 데이터가 변경되면 콜백 함수를 호출 

+ 원본 데이터를 직접 변경하지 않음 
#### vs Computed
+ 특정 데이터 속성의 변화를 감시하고 작업을 수행
+ 데이터 변경에 따른 특정 작업 처리용
+ 비동기 API 요청, 연관 데이터 업데이트 등에 사용됨 

+ [[Computed Property]]와 유사 


#### 구조
+ **Variable** : 감시하는 변수. 반응형이 아닌 경우는 getter로 처리 
+ **newValue** : 감시하는 변수가 변화된 값. 콜백 함수의 첫 번째 인자.
+ **oldValue** : 콜백 함수의 두 번째 인자. 
``` js
watch(variable, (newValue, oldValue) => {
 // do something
})
```
