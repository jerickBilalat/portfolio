<p class="lead">
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ducimus, vero,
  obcaecati, aut, error quam sapiente nemo saepe quibusdam sit excepturi nam
  quia corporis eligendi eos magni recusandae laborum minus inventore?
</p>

```javascript
function test() {
  console.log("hello worl");
}
```

<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ut, tenetur natus
  doloremque laborum quos iste ipsum rerum obcaecati impedit odit illo dolorum
  ab tempora nihil dicta earum fugiat. Temporibus, voluptatibus.
</p>

<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eos, doloribus,
  dolorem iusto blanditiis unde eius illum consequuntur neque dicta incidunt
  ullam ea hic porro optio ratione repellat perspiciatis. Enim, iure!
</p>

<blockquote class="blockquote">
  <p class="mb-0">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere
    erat a ante.
  </p>
  <footer class="blockquote-footer">
    Someone famous in <cite title="Source Title">Source Title</cite>
  </footer>
</blockquote>

<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error, nostrum,
  aliquid, animi, ut quas placeat totam sunt tempora commodi nihil ullam alias
  modi dicta saepe minima ab quo voluptatem obcaecati?
</p>

<p>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Harum, dolor quis.
  Sunt, ut, explicabo, aliquam tenetur ratione tempore quidem voluptates
  cupiditate voluptas illo saepe quaerat numquam recusandae? Qui,
  necessitatibus, est!
</p>

# Sharing Reusable Logic

Created: Apr 12, 2021 4:19 PM
Edited: Apr 13, 2021 11:07 AM
tag: blog

For a while, we used React components and props to reuse logic and two patterns or technique, Render props and Higher Order Components, are formed to enable logic reuse. Then on February 2019, the React team have developed the Hooks API which can be use to reuse logic. Some still prefer HOC or render props in some cases but according to the React team hooks are sufficient in most cases. On this article, we would go over the both patterns and Hooks API in able to compare how they achieve logic reuse.

# Our reusable logic

To start let's say we these two contrived reusable logic:

- log a message to the console every time a component is rendered ( in real app maybe we are calling an api to log page views)
- check if user is authenticated

# Higher Order Components (HOC) Technique

- refs:

  [https://reactjs.org/docs/higher-order-components.html](https://reactjs.org/docs/higher-order-components.html)

  [https://medium.com/@franleplant/react-higher-order-components-in-depth-cf9032ee6c3e](https://medium.com/@franleplant/react-higher-order-components-in-depth-cf9032ee6c3e)

README first: You might have to be familiar with functional programming and its benefits to appreciate using HOC over the other two alternative. If you're not then you might not get my rookie explanation of HOC and its benefits. If you want a good introduction to functional programming, then follow Eric Elliott and his creations.

This technique or pattern came straight out of functional programming where higher order function (HOF) are functions that can receive function as an argument and return function as values. HOC is the same concept because a React component is just a function. We give HOC a component and returns another component.

This pattern involves four things. A higher order function, a component to be wrapped, wrapper component, and the most important part is the reusable logic that needs to be applied.

```jsx
function aHOFFunction(ComponentToBeWrapped) {
  return function WrapperComponent(props) {
    // ... apply reusable logic
    return <ComponentToBeWrapped {...props} />;
  };
}
```

Some developer are using HOC over the other two alternatives because of its composability. Since the idea of HOC is from a functional programming paradigm, it gains the ability to be composable to provide a component a behavior or logic.

Just look at this functional programming beauty:

```jsx
// ...import a compose function from utility library or your own
// ...import withLogger and withAuthentication HOCs

funciton Acomponent() {
	return // ... render some UI
}

// now lets compose our logger and authentication logic or behaviors
// into our component

const MyComposedComponent = compose(
	withLogger,
	withAuthentication,
	Acomponent
)

export default MyComposedComponent
```

# Render props pattern

React hooks pretty much handle use cases for render props and does it much better. If you still need learn it because it in your code base then the React docs is enough.

# React Hooks API
