# Truthy와 Falsy

```jsx
function print(person){
	if(!person){ //undefined, null,0,' ', NAN 같은 경우 아무것도 출력 안됨
		return;
	}
	console.lob(person.name);
}

const person{
	name : 'Jhon'
};

print(); // Jhon
```

falsy한 값

- undefined
- null
- 0
- ‘ ‘  → 공백
- NAN
- false

truthy한 값 → falsy 값을 제외하고 다