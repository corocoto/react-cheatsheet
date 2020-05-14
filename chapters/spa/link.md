## Link

[EN]

The primary way to allow users to navigate around your application. `<Link>` will render a fully accessible anchor tag with the proper `href`.

A `<Link>` can know when the route it links to is active and automatically apply an `activeClassName` and/or `activeStyle` when given either prop. The `<Link>` will be active if the current route is either the linked route or any descendant of the linked route.

### Props

* `to`
    A location descriptor. Usually this is a string or an object, with the following semantics:
    
    * If it's a string it represents the absolute path to link to, e.g. `/users/123` (relative paths are not supported).
        
    * If it's an object it can have four keys:
        * `pathname`: A string representing the path to link to.
        * `query`: An object of key:value pairs to be stringified.
        * `hash`: A hash to put in the URL, e.g. `#a-hash`.
        * `state`: State to persist to the location.

* `activeClassName`
    The className a `<Link>` receives when its route is active.

* `activeStyle`
    The styles to apply to the link element when its route is active.

[RU]

Основной способ позволить пользователям перемещаться по вашему приложению. `<Link>` будет отписован полностью доступным тегом `a` с атрибутом `href`.

`<Link>` может знать, когда маршрут активен, на который он ссылается, и автоматически применить `activeClassName`  и/или `activeStyle`, когда ему назначен этот проп. `<Link>` будет активным, если текущий маршрут является либо связанным маршрутом, либо любым его потомком (связанного маршрута).

### Пропсы

* `to`

    Дескриптор местоположения. Обычно это строка или объект со следующей семантикой:
    
    * Если это строка, она представляет из себя абсолютный путь до ссылки, н-р: `/users/123` (относительные пути не поддерживаются).
        
    * Если это объект, он может иметь 4 случая:
        
        * `pathname`: Строка, представляющая путь к ссылке.
        * `query`: Объект с парой ключ:значение является строковым.
        * `hash`: Хэш, который вставляется в URL, н-р: `#a-hash`.
        * `state`: Состояние до установленного местопоожения.
            
* `activeClassName`
    Имя класса `<Link>`, когда его маршрут является активным. 
    The `className` a `<Link>` receives when its route is active. No active class by default.

* `activeStyle`
    Стили применяются к элементу "ссылка", когда ее маршрут является активным.