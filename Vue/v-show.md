##### : 표현식 값의 T/F를 기반으로 요소의 가시성을 전환 

+ `v-show` 요소는 항상 렌더링 되어 [[DOM]]에 남아있음
+ CSS **display** 속성만 전환하기 때문 
``` html
const isShow = ref(false)

<div v-show="isShow"> v-show </div>

<div style="display: none;">v-show</div>
```

