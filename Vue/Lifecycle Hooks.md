##### : Vue 인스턴스의 생애주기 동안 특정 시점에 실행되는 함수 
+ 개발자가 특정 단계에서 의도하는 로직이 실행될 수 있도록 함
+ Lifecycle hooks에 등록된 콜백 함수들을 인스턴스와 **자동으로 연결**한다. 
+ hooks 함수들은 반드시 동기적으로 작성되어야 함.
	+ hooks 함수 내부가 비동기 인건 상관 X. but, hooks 함수 자체에 await 같은데 붙으면 안됨!
+ ex. `onMounted`, `onUpdated`, `onUnmounted`

### created
##### : Vue 객체가 만들어질 때만 동작 
+ Vue 객체는 만들어지고 아직 화면과 연결(mount)되지 않은 상태 
+ Composition 방식에서는 setup 코드에서 created 포함 
### mounted
##### : Vue 객체가 DOM에 mount된 상태 
+ DOM 트리가 완성되어 부모 Container에 삽입 완료된 상태 
+ 모든 자식 Component들도 mount 완료된 상태 
+ COm과 관련된 동작을 수행하려 할 때 

#### 예시
##### 1. Vue 컴포넌트 인스턴스가 초기 렌더링 및 DOM 요소 생성이 완료된 후 특정 로직을 수행하기 
``` js
const { createApp, ref, onMounted } = Vue

setup() {
	onMounted(() => {
		console.log("mounted")
	})
}
```
##### 2. 반응형 데이터의 변경으로 인해 컴포넌트의 DOM이 업데이트 된 후 특정 로직을 수행하기 
``` js
const { createApp, ref, onMounted, onUpdated } = Vue

onUpdated(() => {
	message.value = 'updated' // 업데이트 후에 실행 
})
```

