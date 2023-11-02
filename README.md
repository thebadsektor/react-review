# React Reviewer

# Section 1: Introduction

## Pros and Cons of React

### Q1: What are the pros and cons of React?
### Q2: How can you compare it to Angular?

Here are the pros and cons of React compared to Angular:

#### Pros of React:
- Uses a virtual DOM which can improve performance compared to Angular's dirty checking.
- Encourages composable and reusable UI components.
- Easy to integrate with other libraries and frameworks.
- Large ecosystem of third-party libraries and tools.
- Easier learning curve than Angular.

#### Cons of React:
- Only handles the UI layer, so you need to pull in other libraries for routing, state management, etc.
- JSX can seem awkward to some developers.
- Styling can be more challenging as CSS-in-JS solutions are often used.
- Rapid release cycle can mean more breaking changes.

When comparing React to Angular:
- Angular provides more out of the box - routing, state management, form validation, etc. This can save time but also means more to learn upfront.
- React is more flexible and gives more freedom in how you structure your app. Angular is more opinionated.
- Angular uses TypeScript which provides more type safety but also another layer of complexity.
- React has a larger community and ecosystem than Angular.

For larger enterprise applications, Angular may work better. For smaller web apps, React may be easier to work with. The choice depends on your background, team, and type of application. Evaluating pros/cons of each can help make the best decision.

## How to create a React application?

### Q1: How do you prefer to generate your React application?
### Q2: What are the ways?

There are a few main ways to generate a React application:

#### Q1: My preferred way is to use the Create React App. It


##Why do we use className and not class?
###Q1: Why can't we write class inside our JSX markup?

Class is a reserved keyword in JavaScript for defining classes. So if we tried to keep the class in the JSX, it would cause a syntax error when compiled to JavaScript.

To avoid this conflict, JSX uses className which maps to the HTML class attribute, but doesn't conflict with the class keyword:
```<div className="header">```

Compiles to:
``` React.createElement("div", {className: "header"});```

##What are functional components and props?
###Q1: How to create functional components?
###Q2: How to pass props to the components?

Function component defined 
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>; 
}```

// Function components accept props as an argument 
// and return JSX

```function App() {
  return (
    <div>
      {/* Pass props when rendering the component */}
      <Welcome name="Sara" /> 
      <Welcome name="Cahal" />
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));```
```
Welcome component rendered with different props
```
// <h1>Hello, Sara</h1>
// <h1>Hello, Cahal</h1>
```
##What are class components, props and state?
###Q1: How to create class components?
###Q2: How to pass props to class components?
###Q3: How state is working in class components?
```
// Class component
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

// Class components receive props via this.props

class App extends React.Component {
  // Initialize state
  state = { name: 'Mary' }
  
  render() {
    return (
      <div>
        {/* Pass props when rendering */}
        <Welcome name="Sara" />
        
        {/* Access state via this.state */}
        <Welcome name={this.state.name} />  
      </div>
    );
  }
}

ReactDOM.render(<App />, document.getElementById('root'));
```
Welcome renders:
```
<h1>Hello, Sara</h1> 
<h1>Hello, Mary</h1>
```

##What are dumb vs smart components?
###Q1: What are dumb and smart components?
###Q2: What are presentational vs container components?

Here's an overview of dumb vs smart components and presentational vs container components:

###Q1: What are dumb and smart components?
- Dumb components are simple components that only render UI.
- They receive data through props and render it.
- Smart components are more complex with additional logic and state.
- They may fetch data, handle UI logic, initialize state, etc.

###Q2: What are presentational vs container components?
- Presentational components focus on the UI and visuals.
- They render UI based on the data they receive through props.
- Container components manage data and logic.
- They often provide the data to presentational components.
- Container components are also called smart/stateful components.
- Presentational components are dumb/stateless components.

The core idea is separation of concerns:
- Presentational components handle styling, rendering UI
- Container components handle data, fetch API calls, state updates

This makes components more reusable and your app more maintainable.

###What is a key index map?

##Q1: How to render a list in React?
- Use the array map() method to loop through items.
- Return JSX for each item from the map callback.
For example:
```
const listItems = data.map(item => <li>{item.name}</li>);
return <ul>{listItems}</ul>;
```

###Q2: What is key and why it is bad to use index for it?
- When rendering list items, each one needs a unique "key" prop.
- The key helps React identify which items changed between re-renders.
- Using the item index as the key is not recommended:
- The index can change when adding/removing items.
- This can cause performance issues and bugs with component state.
- Better to use a unique ID from each data item as the key.
For example:
```
data.map(item => <Item key={item.id} name={item.name} />)
```
In summary, use map() to render lists and make sure to specify a stable key like an ID.

// What is React.Fragment?
// Q1: What is React fragment?
// Q2: Do you know the short version?

// Q1: What is React fragment?
// - React requires components to return a single element.
// - Fragments allow grouping a list of children without adding extra nodes to the DOM.
// - Fragments are declared using:
```
<React.Fragment>
  <ChildA />
  <ChildB />
  <ChildC />
</React.Fragment>
```
This avoids needing to wrap child elements in unnecessary divs.

// Q2: Do you know the short syntax?
// - There is a shorter syntax that uses empty tags:
<>
  <ChildA />
  <ChildB />
  <ChildC />  
</>

// The <></> syntax is equivalent to <React.Fragment></React.Fragment>
// Fragments can also accept keys which is useful when mapping component arrays.

// So in summary, fragments let you group elements without adding wrapper nodes which helps simplify component trees. The short syntax is very convenient!

// What is conditional rendering in React?
// Q1: What do you know about conditional rendering in React?

// Q1: What do you know about conditional rendering in React?
// - Use standard if/else, &&, ||, ternary operators to conditionally render elements.
// - For example:
{ condition ? <ComponentA /> : <ComponentB /> }

{ show && <Component />}

{ errors.length > 0 && 
  <ErrorMessages errors={errors} />
}

// Conditional rendering can be done inside functions components.
// The condition can check props, state, etc.
// You can use variables to store elements before conditionally rendering them.
// Helpful for more complex conditional logic.
// Avoid rendering unnecessary components to optimize performance.
// Be careful when conditionally rendering child components to avoid issues with re-mounting.

// In summary, conditional rendering is useful to control what gets rendered based on application logic. Simple JavaScript expressions can be used inside JSX.

// How to apply styles in React?
// Q1: How to apply styles in React?
// Q2: How to add several classes conditionally?

// Q1: How to apply styles in React?
// - Inline styles - Style objects can be defined and passed:
<div style={{color: 'blue', fontSize: 20}}></div>

// - CSS Stylesheets - Import .css files:
import './styles.css';

<div className="my-div"></div>

// - CSS Modules - CSS files scoped locally by component:
/* Button.module.css */
.button {
  /* CSS */
}
import styles from './Button.module.css';

<button className={styles.button}></button>

// - CSS-in-JS - Define styles in JS, generate CSS at runtime:
const styles = {
  button: {
    color: 'blue'
  }
}

<button style={styles.button}></button>

// Q2: How to add several classes conditionally?
// - Use template literals to build class names:
<div className={`${styles.base} ${active && styles.active}`}

// - Or join class arrays:
const cls = [styles.base, active && styles.active].join(' ');

<div className={cls}></div>

// In summary, React provides flexibility in styling approaches - inline, CSS, CSS Modules, CSS-in-JS. Conditional classes can be built up programmatically.
```

How to handle forms in React? Q1: How to handle forms in React?

Handling forms in React involves managing and interacting with form elements, capturing user input, and possibly validating and submitting data. Here's how to handle forms in React:

1.  Controlled Components:
    
    -   In React, form elements like `<input>`, `<textarea>`, and `<select>` are made "controlled components."
    -   A controlled component stores its state in the component's state, and its value is updated via the `onChange` event.
    -   To set up a controlled component, you need to maintain its state using React's state management (typically `useState`) and provide an `onChange` handler to update the state.
Example:
```
const [inputValue, setInputValue] = useState('');

const handleInputChange = (e) => {
  setInputValue(e.target.value);
};

return (
  <input
    type="text"
    value={inputValue}
    onChange={handleInputChange}
  />
);
```
Form Submission:

-   To handle form submission, you can use the `onSubmit` event of the `<form>` element.
-   You can create a form and submit it with a submit button or handle form submission programmatically with JavaScript.
Example:
```
const handleSubmit = (e) => {
  e.preventDefault(); // Prevent the default form submission behavior.
  // Handle form data or make an API request.
};

return (
  <form onSubmit={handleSubmit}>
    {/* Form inputs here */}
    <button type="submit">Submit</button>
  </form>
);
```
State Management and Validation:

-   When handling form input, you can manage the state for each input field, validate the input, and display validation errors.
-   Use React state to store input data and validation status.
Example:
```
const [email, setEmail] = useState('');
const [emailError, setEmailError] = useState('');

const handleEmailChange = (e) => {
  const value = e.target.value;
  setEmail(value);
  // Validate the email and set the error state if necessary.
  if (!isValidEmail(value)) {
    setEmailError('Invalid email address');
  } else {
    setEmailError('');
  }
};
```
