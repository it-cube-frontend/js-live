Перемещение по DOM-дереву можно производить с помощью свойств ```children``` и ```parentElement```. ```parentElement``` содержит элемент родителя, а ```children``` дочерние элементы узла. 

Давайте доберемся до узла заголовка
```javascript
var pageHeading = document.children[0].children[1].children[0];
console.log(pageHeading.tagName);
```

Понятно, что работать так со вложенными элементами DOM очень неудобно. Поэтому для поиска элементов в DOM есть специальные методы у каждого элемента DOM-дерева:
* ```getElementById``` — находит конкретный элемент по атрибуту **id**;
* ```querySelector``` — находит первый элемент, совпавший по CSS-селектору;
* ```querySelectorAll``` — находит все элементы, совпадающие по CSS-селектору.
```javascript
console.log(pageHeading === document.getElementById('pageHeading'));
console.log(pageHeading === document.querySelector('.page-title'));
```

Для управления атрибутами DOM-дерева можно пользоваться специальными методами ```getAttribute``` и ```setAttribute```. Метод ```getAttribute``` возвращает значение указанного атрибута элемента, а ```setAttribute``` добавляет новый атрибут или изменяет значение существующего атрибута элемента по его названию в HTML.
```javascript
pageHeading.setAttribute('style', 'background: red;');
console.log(pageHeading.getAttribute('class'));
```

Большинство HTML-атрибутов доступны в виде свойств DOM-элемента, и к ним можно обращаться напрямую. Исключения составляют те атрибуты, названия которых являются ключевыми или зарезервированными для будущих версий словами JS, например ```class``` или ```for```. Чтобы обратиться к классу, нужно воспользоваться свойством ```className```, а чтобы прочитать лейбл, нужно воспользоваться свойством ```htmlFor```.
```javascript
console.log(pageHeading.className);
pageHeading.className = 'myclass';
console.log(pageHeading.className);
```

С некоторыми свойствами неудобно работать как с атрибутами. Например, один элемент может содержать несколько классов. Для этого в DOM-объектах предусмотрены специальные объекты, которые помогают работать с такими атрибутами. Например, для работы с классами существует объект ```classList```, который является свойством всех DOM-объектов.
```javascript
pageHeading.classList.add('myclass');
console.log(pageHeading.className);

pageHeading.classList.remove('page-title');
console.log(pageHeading.className);
```
