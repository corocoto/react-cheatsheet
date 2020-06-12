# React.js cheatsheet

[EN]

This repo is contains some useful opportunities for work with React.js library.

[RU]

Этот репозиторий содержит некоторые полезные возможности для работы с библиотекой React.js.

### Chapters (Главы)

1. [Creating component (Создание компонента)](chapters/CreateComponent.md)
2. [Briefly about `state` and `props` (Кратко о `state` и `props`)](chapters/state_props.md)
3. Patterns (Паттерны): 
    * [Stateless and Stateful Components (Stateless и Stateful Компоненты)](chapters/patterns/StatelessStatefulComponents.md)
    * [Controlled and Uncontrolled Component (Контролируемые  и Неконтролируемые Компоненты)](chapters/patterns/ControlledUncontrolledComponents.md)
4. [Class-based Components and Functional Components (Классовые и Функциональные Компоненты)](chapters/ClassFuncComponents.md)
5. [`props.children`](chapters/props_children.md)
6. [`defaultProps`](chapters/defaultProps.md)
7. [`PropTypes`](chapters/PropTypes.md)
8. Lifecycle methods (Методы жизненного цикла):
    * [What's a Lifecycle Method? (Что такое метод жизненного цикла?)](chapters/lifecycle_methods/LifecycleMethodsDescr.md)
    * [Mounting Lifecycle Methods (Монтирующие методы жизненного цикла)](chapters/lifecycle_methods/types/mounting/MountingLifecycleMethods.md):
        * [`constructor`](chapters/lifecycle_methods/types/mounting/constructor.md)
        * [`static getDerivedStateFromProps`](chapters/lifecycle_methods/types/mounting/getDerivedStateFromProps.md)
        * [`render`](chapters/lifecycle_methods/types/mounting/render.md)
        * [`componentDidMount`](chapters/lifecycle_methods/types/mounting/componentDidMount.md)
    * [Updating Lifecycle Methods (Обновляющие методы жизненного цикла)](chapters/lifecycle_methods/types/updating/UpdatingLifecycleMethods.md):
        * [`static getDerivedStateFromProps`](chapters/lifecycle_methods/types/mounting/getDerivedStateFromProps.md)
        * [`shouldComponentUpdate`](chapters/lifecycle_methods/types/updating/shouldComponentUpdate.md)
        * [`render`](chapters/lifecycle_methods/types/mounting/render.md)
        * [`getSnapshotBeforeUpdate`](chapters/lifecycle_methods/types/updating/getSnapshotBeforeUpdate.md)
        * [`componentDidUpdate`](chapters/lifecycle_methods/types/updating/componentDidUpdate.md)
    * [Unmounting Lifecycle Methods (Размонтирующие методы жизненного цикла)](chapters/lifecycle_methods/types/unmounting/UnmountingLifecycleMethods.md):
        * [`componentWillUnmount`](chapters/lifecycle_methods/types/unmounting/componentWillUnmount.md)
    * [Errors Handle (Обработка ошибок):](chapters/lifecycle_methods/types/errors/errors_handle.md)
        * [`static getDerivedStateFromError`](chapters/lifecycle_methods/types/errors/getDerivedStateFromError.md)
        * [`componentDidCatch`](chapters/lifecycle_methods/types/errors/componentDidCatch.md)
9. Hooks (Хуки):
    * [What're Hooks? (Что такое хуки?)](chapters/hooks/hooks.md)
    * [`useState`](chapters/hooks/useState.md) 
    * [`useEffect`](chapters/hooks/useEffect.md)
    * [`useRef`](chapters/hooks/useRef.md)
    * [`useContext`](chapters/hooks/useContext.md)
    * [`useMemo`](chapters/hooks/useMemo.md)
10. Styling (Стилизация):
    * [Dynamic styling components (Динамическая стилизация компонентов)](chapters/styling/dynamic_styling.md)  
    * [Using pseudo classes, pseudo elements and media queries in inline styles (Использование псевдоклассов, псевдоэлементов и медиа выражений в inline-стилях)](chapters/styling/radium.md) 
    * [**styled-components** library (библиотека **styled-components**)](chapters/styling/styled-components.md) 
    * [Adding isolating styles using CSS Modules (Добавление изолирующих стилей, используя CSS Modules)](chapters/styling/css_modules.md)   
11. Debugging React Apps (Отладка React-приложений):
    * [Error Boundary](chapters/debug/error_boundary.md)
12. [React Application Structure (Структура React-приложения)](chapters/structure/app_structure.md)
13. Optimizations (Оптимизации):
    * [React.memo](chapters/optimization/react_memo.md)
    * [React.Component vs React.PureComponent](chapters/optimization/component_vs_purecomponent.md)
    * [Lazy Loading (Ленивая загрузка)](chapters/optimization/lazy_loading.md)
14. [Ref](chapters/ref/ref.md)
15. [Context (Контекст)](chapters/context/context.md)
17. Single Page Application (SPA):
    * [`react-router-dom` package (пакет `react-router-dom`)](chapters/spa/react-router-dom.md)
    * [BrowserRouter](chapters/spa/browser-router.md)
    * [Route](chapters/spa/route.md)
    * [Link](chapters/spa/link.md)
    * [NavLink](chapters/spa/navlink.md)
    * [Switch](chapters/spa/switch.md)
    * [Redirect](chapters/spa/redirect.md)
    * HOC:
        * [withRouter](chapters/spa/hoc/with-router.md)
18. Redux        
