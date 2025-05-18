##### :  표현식 값의 T/F를 기반으로 요소를 조건부로 렌더링
``` html
const isSeen = ref(true)
<p v-if="isSeen"> true일 때 보여요</p>
<p v-else> false일 때 보여요 </p>
<button @click="isSeen = !isSeen">토글 버튼 </button>
```

#### HTML <template> element 
##### : 페이지가 로드될 때 렌더링 되지 않지만, JS를 사용하여 나중에 문서에서 사용할 수 있도록 하는 HTML을 보유하기 위한 메커니즘 
