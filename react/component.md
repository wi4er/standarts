# React code style

## Functional style

* Имя функционального компонента всегда начинается с большой буквы;
* Структура функционального компонента:
    1. Деструктуризация зависимостей;
    2. Хуки;3
    3. Возвращение плохих рендеров (Если необходимо);
    4. Вычисления значений (Если необходимо);
    5. Возвращение react.element с телом компонента;

```javascript
function Item(props) {
    const {count, onUpdate} = props;
    let total = 0;

    React.useEffect(onUpdate);
    
    if (!count) {
        return null;
    }

    for (let i = 0; i < count; i++) {
        total += i;
    }

    return (
        <div>
            {total}
        </div>
    );
}
```

* В функциональном компоненте должно быть не более одного хука React.useState
* 

## Class Component style

### React methods

* В списке методов ```constructor``` всегда идёт первым, а ```render``` последним
