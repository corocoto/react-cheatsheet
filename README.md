# React.js tips and tricks cheatsheet

[EN]
This repo is contains some useful opportunities for work with React.js library.

[RU]
Этот репозиторий содержит некоторые полезные возможности для работы с библиотекой React.js.

### Chapters

1. [Creating component (Создание компонента)](%20chapters/CreateComponent.md)
2. [Briefly about `state` and `props` (Кратко о `state` и `props`)](%20chapters/state_props.md)
3. Patterns (Паттерны): 
    * [Stateless and Stateful Components (Stateless и Stateful Компоненты)](%20chapters/patterns/StatelessStatefulComponents.md)
    * [Controlled and Uncontrolled Component (Контролируемые  и Неконтролируемые Компоненты)](%20chapters/patterns/ControlledUncontrolledComponents.md)
4. [Class-based Components and Functional Components (Классовые и Функциональные Компоненты)](%20chapters/ClassFuncComponents.md)
5. [`props.children`](%20chapters/props_children.md)
6. [`defaultProps`](%20chapters/defaultProps.md)
7. [`PropTypes`](%20chapters/PropTypes.md)
8. Lifecycle methods (Методы жизненного цикла):
    * [What's a Lifecycle Method? (Что такое метод жизненного цикла?)](%20chapters/lifecycle_methods/LifecycleMethodsDescr.md)
    * [Mounting Lifecycle Methods (Монтирующие методы жизненного цикла)](%20chapters/lifecycle_methods/types/mounting/MountingLifecycleMethods.md):
        * [`constructor`](%20chapters/lifecycle_methods/types/mounting/constructor.md)
        * [`static getDerivedStateFromProps`](%20chapters/lifecycle_methods/types/mounting/getDerivedStateFromProps.md)
        * [`render`](%20chapters/lifecycle_methods/types/mounting/render.md)
        * [`componentDidMount`](%20chapters/lifecycle_methods/types/mounting/componentDidMount.md)
    * [Updating Lifecycle Methods (Обновляющие методы жизненного цикла)](%20chapters/lifecycle_methods/types/updating/UpdatingLifecycleMethods.md):
        * [`static getDerivedStateFromProps`](%20chapters/lifecycle_methods/types/mounting/getDerivedStateFromProps.md)
        * [`shouldComponentUpdate`](%20chapters/lifecycle_methods/types/updating/shouldComponentUpdate.md)
        * [`render`](%20chapters/lifecycle_methods/types/mounting/render.md)
        * [`getSnapshotBeforeUpdate`](%20chapters/lifecycle_methods/types/updating/getSnapshotBeforeUpdate.md)
        * [`componentDidUpdate`](%20chapters/lifecycle_methods/types/updating/componentDidUpdate.md)
    * [Unmounting Lifecycle Methods (Размонтирующие методы жизненного цикла)](%20chapters/lifecycle_methods/types/unmounting/UnmountingLifecycleMethods.md):
        * [`componentWillUnmount`](%20chapters/lifecycle_methods/types/unmounting/componentWillUnmount.md)
    * [Errors Handle: (Обработка ошибок:)](%20chapters/lifecycle_methods/types/errors/errors_handle.md)
        * [`static getDerivedStateFromError`](%20chapters/lifecycle_methods/types/errors/getDerivedStateFromError.md)
        * [`componentDidCatch`](%20chapters/lifecycle_methods/types/errors/componentDidCatch.md)
9. Hooks (Хуки):
    * [`useState`](%20chapters/hooks/useState.md) 
    * [`useEffect`](%20chapters/hooks/useEffect.md)
    * [`useRef`](%20chapters/hooks/useRef.md)
    * useContext
    * useMemo
10. Styling (Стилизация):
    * [Dynamic styling components (Динамическая стилизация компонентов)](%20chapters/styling/dynamic_styling.md)  
    * [Using pseudo classes, pseudo elements and media queries in inline styles (Использование псевдоклассов, псевдоэлементов и медиа выражений в inline-стилях)](%20chapters/styling/radium.md) 
    * [`styled-components` library (библиотека `styled-components`)](%20chapters/styling/styled-components.md) 
    * [Adding isolating styles using CSS Modules (Добавление изолирующих стилей, используя CSS Modules)](%20chapters/styling/css_modules.md)   
11. Debugging React Apps (Отладка React-приложений):
    * [Error Boundary](%20chapters/debug/error_boundary.md)
12. [React Application Structure (Структура React-приложения)](%20chapters/structure/app_structure.md)
13. Optimizations (Оптимизации):
    * [React.memo](%20chapters/optimization/react_memo.md)
    * [React.Component vs React.PureComponent](%20chapters/optimization/component_vs_purecomponent.md)
    * lazyLoading
14. [Ref](%20chapters/ref/ref.md)
15. [Context](%20chapters/context/context.md)
16. Suspense
17. Single Page Application (SPA)
    * Link
    * NavLink
    * Route
    * Switch
    * BrowserRouter
    * Redirect
    * Hooks:
        * withRouter
18. Redux        
