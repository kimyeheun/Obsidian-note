##### : 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달할 때 사용되는 단방향 데이터 전달 방식 
+ 부모 속성이 업데이트 되면 자식으로 전달되지만, 그 반대는 안됨
+ 즉, 자식 컴포넌트 내부에서 props를 변경하려고 시도해서는 안됨. & 불가능 
+ 또한 부모 컴포넌트가 업데이트 될 때마다 이를 사용하는 자식 컴포넌트의 모든 props가 최신 값으로 업데이트 됨 
#### One-Way Data Flow

### Static Props
``` js
<ParentChild my-msg="message" />
```
### Dynamic Props
+ v-bind를 사용하여 동적으로 할당된 props를 사용할 수 있음
``` js
<!-- parent.vue -->
<ParentChild my-msg="message" :dynamic-props="name" />
```