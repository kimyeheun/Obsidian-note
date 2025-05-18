##### : 실제 HTML을 출력할 때 사용 


``` html
<div v-html="rawHtml"> </div>

const rawHtml = ref('<span style="color:red">This should be red.</span>')
```