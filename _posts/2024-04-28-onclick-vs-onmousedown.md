---
title: "[React] onClick, onBlur 이벤트의 실행 순서 문제 해결하기"
date: 2024-04-28 00:00:00
categories: [Web, React]
tags: [onclick, onmousedown, onblur] # TAG names should always be lowercase
---

### 구현 목표

검색창을 클릭하면 자동 완성 검색어가 드롭다운으로 나타나, 빠른 검색이 가능하도록 만들기.

- 검색창을 클릭하면 자동 완성 검색어가 나타나고, 검색창 이외의 곳을 클릭할 때는 사라져야 함
- 자동 완성 검색어를 클릭하면 검색창에 자동으로 입력되어야 함

### 문제 상황

자동 완성 검색어를 클릭하면 **검색창 밖을 클릭한 것으로 인식되어 드롭다운이 사라지기만** 했다.  
문제가 생긴 코드를 간단화하면 다음과 같다.

```tsx
const [isFocus, setIsFocus] = useState(false);
const [inputValue, setInputValue] = useState("");

return {
  <input
	    value={inputValue}
	    onFocus={() => setIsFocus(true)}
	    onBlur={() => setIsFocus(false)}
	/>
	{isFocus ?
		<div>
			<div
				onClick={() => {
				setInputValue(/*자동 완성 검색어*/);
				}}
			>
				{/*자동 완성 검색어*/}
			</div>
		</div>
	}
}
```

자동 완성 검색어를 클릭하면 onClick이 호출되기 전에, 검색창의 onBlur가 먼저 호출되어 자동 완성 검색어를 담은 <div>가 사라진다.

### 해결 방법

**onClick을 onMouseDown으로 변경**해 onBlur보다 먼저 호출되도록 한다.

각 이벤트가 실행되는 순서는 다음과 같다. 

```
onMouseDown -> onBlur -> onMouseUp -> onClick
```
참고로, onMouseDown에서 event.preventDefault()를 호출하여 mousedown 이벤트를 취소해 onBlur 이벤트가 발생하지 않게 만들 수도 있다.