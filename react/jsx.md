# JSX code style

* Внутри jsx кода не должно быть никаких сложных js выражений, допускаются
    * Простые условные операторы;
    * Вызовы функций;
    * Простые математические действия;

```javascript
function List(props) {
    const {handleClick, value, count} = props;

    return (
        <div onClick={handleClick("Something")}>
            <div>
                {value + 1}
            </div>

            <div>
                {count > 1 ? count : ""}
            </div>
        </div>
    );
}
```

* В начале метода всегда деструктуризируется все используемые значения из:
    * state;
    * props;
    * context

```javascript
class List extends React.Component {
    static contextType = someContext;

    state = {
        value: 1,
    }

    render() {
        const {list} = this.props;
        const {value} = this.state;
        const {handleClick} = this.context;

        return (
            <div onClick={handleClick}>
                <List list={list}/>

                <div>
                    {value}
                </div>
            </div>
        );
    }
}
```

* Деструктуризация проходит от первого ключа после this до нужного значения

```javascript
class List extends React.Component {
    state = {
        item: {
            property: {
                value: 10
            }
        },
    }

    render() {
        const {item: {property: {value}}} = this.props;

        return (
            <div>
                {value}
            </div>
        );
    }
}
```

* В одной строке должен содержаться только один аттрибут слоя

```javascript
function Item(props) {
    const {list, handleClick} = this.props;

    return (
        <div onClick={handleClick}>
            <List
                list={list}
                value="value"
                count={10}
            />
        </div>
    );
}
```

* Обработчики событий всегда выносятся в отдельную функцию, имя которой начинается со слова handle

```javascript
class List extends React.Component {
    handleClick = () => {
        const {onClick} = this.props;

        onClick("CLICK")
    }

    render() {
        return (
            <div onClick={this.handleClick}/>
        );
    }
}
```

* Если функция возвращает jsx, то её имя начинается со слова render

```javascript
class List extends React.Component {
    renderTitle() {
        const {title} = this.props;

        return (
            <div className="title">
                {title}
            </div>
        );
    }

    render() {
        return (
            <div>
                {this.renderTitle()}
            </div>
        );
    }
}
```

* Горизонтальный разделитель это всегда 4 пробела

```javascript
class List extends React.Component {
    render() {
        const {value} = this.props;

        if (value) {
            if (value > 5) {
                return (
                    <div>
                        {value}
                    </div>
                );
            } else {
                return null;
            }
        }

        return (
            <div>
                {"EMPTY"}
            </div>
        );
    }
}
```
