##### : 컴포넌트의 템플릿, 로직 및 스타일을 하나의 파일로 묶어낸 특수한 파일 형식 (==*.vue==)

+ 일반적으로 Template -> Script -> style 순서로 작성 

### Template
+ 최상위 template 블록 하나만 포함할 수 있음
### Script
+ `<script setup>` 블록을 하나만 포함할 수 있음
### Style
+ 여러 개의 `<style>` 태그가 포함될 수 있음 
+ `scoped`가 지정되면 CSS는 현재 컴포넌트에만 적용
	+ 부모 컴포넌트 스타일이 자식으로 유출되지 않음
	
