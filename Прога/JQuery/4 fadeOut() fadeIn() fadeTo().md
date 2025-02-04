Плавное скрытие и отображение элементов
```js
function elemOut(element, time) {
	if(time>1000 && time<2000){
		$("."+element).fadeOut(time);
	}
}
```
fadeIn(duration)  отображает элемент
fadeOut(duration) скрывает элемент
fadeTo(duration) делает элемент прозрачным
Можно менять время, за которое происходит действие