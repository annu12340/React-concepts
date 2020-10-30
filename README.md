# React-concepts

### Index
1. Lifecycle oPure Componentsf Components
2. Pure Components
3. React Refs 
4. Higher-Order Components
5. 

## Lifecycle of Components

Each component in React has a lifecycle which undergoes three phases : Mounting, Updating, and Unmounting.

React has four built-in methods that gets called, in this order, when mounting a component:

- constructor()  **/```useState( )```**
- getDerivedStateFromProps() **/ ```useEffect( ()=>{}, [prop1,prop2]  )```**
- render()
- componentDidMount()  **/```useEffect( ()=>{}, [prop1,prop2]  )```** : fetches data from an API 

A component is updated whenever there is a change in the component's state or props.React has five built-in methods that gets called, in this order, when a component is updated:

- getDerivedStateFromProps()
- shouldComponentUpdate() / **/```useMemo()```**
- render()
- getSnapshotBeforeUpdate()  **/```custom hooks```**
- componentDidUpdate()  **/```useEffect( ()=>{} )```**

React has only one built-in method that gets called when a component is unmounted:
- componentWillUnmount()  **/```useEffect(() => { return () => {},  [])```**

<img src="https://miro.medium.com/max/1400/1*EnuAy1kb9nOcFuIzM49Srw.png">

## Pure Components

Generally we use state or props value to decide the update cycle. React has now provided us a PureComponent which does the comparison of state and props to decide the update cycle.
Pure Components in React are the components which do not re-renders when the value of state and props has been updated with the same values. If the value of the previous state or props and the new state or props is the same, the component is not re-rendered This helps in improving the performance of the application

## React Refs 

## Higher-Order Components


## Error Boundaries
