# React.js tips and tricks cheatsheet

This repo is contains some useful opportunities for work with React.js library.

### Chapters

1. [Creating component](%20chapters/CreateComponent.md)
2. [Briefly about `state` and `props`](%20chapters/state_props.md)
3. Patterns: 
    * [Stateless and Stateful Components](%20chapters/patterns/StatelessStatefulComponents.md)
    * [Controlled and Uncontrolled Components](%20chapters/patterns/ControlledUncontrolledComponents.md)
4. [Class-based Components and Functional Components](%20chapters/ClassFuncComponents.md)
5. [`props.children`](%20chapters/props_children.md)
6. [`defaultProps`](%20chapters/defaultProps.md)
7. [`PropTypes`]( chapters/PropTypes.md)
8. Lifecycle methods:
    * [What's a Lifecycle Method?](%20chapters/lifecycle_methods/LifecycleMethodsDescr.md)
    * [Mounting Lifecycle Methods](%20chapters/lifecycle_methods/types/mounting/MountingLifecycleMethods.md):
        * [`constructor`](%20chapters/lifecycle_methods/types/mounting/constructor.md)
        * [`static getDerivedStateFromProps`](%20chapters/lifecycle_methods/types/mounting/getDerivedStateFromProps.md)
        * [`render`](%20chapters/lifecycle_methods/types/mounting/render.md)
        * [`componentDidMount`](%20chapters/lifecycle_methods/types/mounting/componentDidMount.md)
    * [Updating Lifecycle Methods](%20chapters/lifecycle_methods/types/updating/UpdatingLifecycleMethods.md):
        * [`static getDerivedStateFromProps`](%20chapters/lifecycle_methods/types/mounting/getDerivedStateFromProps.md)
        * [`shouldComponentUpdate`](%20chapters/lifecycle_methods/types/updating/shouldComponentUpdate.md)
        * [`render`](%20chapters/lifecycle_methods/types/mounting/render.md)
        * [`getSnapshotBeforeUpdate`](%20chapters/lifecycle_methods/types/updating/getSnapshotBeforeUpdate.md)
        * [`componentDidUpdate`](%20chapters/lifecycle_methods/types/updating/componentDidUpdate.md)
    * [Unmounting Lifecycle Methods](%20chapters/lifecycle_methods/types/unmounting/UnmountingLifecycleMethods.md):
        * [`componentWillUnmount`](%20chapters/lifecycle_methods/types/unmounting/componentWillUnmount.md)
    * [Errors Handle:](%20chapters/lifecycle_methods/types/errors/errors_handle.md)
        * [`static getDerivedStateFromError`](%20chapters/lifecycle_methods/types/errors/getDerivedStateFromError.md)
        * [`componentDidCatch`](%20chapters/lifecycle_methods/types/errors/componentDidCatch.md)
9. Hooks:
    * [`useState`](%20chapters/hooks/useState.md) 
    * [`useEffect`](%20chapters/hooks/useEffect.md)
    * [`useRef`](%20chapters/hooks/useRef.md)
10. Styling:
    * [Dynamic styling components](%20chapters/styling/dynamic_styling.md)  
    * [Using pseudo classes, pseudo elements and media queries in inline styles](%20chapters/styling/radium.md) 
    * [`styled-components` library](%20chapters/styling/styled-components.md) 
    * [Adding isolating styles using CSS Modules](%20chapters/styling/css_modules.md)   
11. Debugging React Apps:
    * [Error Boundary](%20chapters/debug/error_boundary.md)
12. [React Application Structure](%20chapters/structure/app_structure.md)
13. Optimizations:
    * [React.memo](%20chapters/optimization/react_memo.md)
    * [React.Component vs React.PureComponent](%20chapters/optimization/component_vs_purecomponent.md)
14. [Ref](%20chapters/ref/ref.md)