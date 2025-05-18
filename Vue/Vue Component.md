```App.vue 존재 ```
-  **컴포넌트 파일 생성**
`MyComponent.vue` 생성 (/src/components/)
-  **컴포넌트 등록 (import)**
``` js
<!-- App.vue -->
<template>
	<h1>App.vue</h1>
	<MyComponent />
</template>

<script setup>
	import MyComponent from '@/components/MyComponent.vue'
	<!-- "@" == "src/" -->
</script>
```
