# Lifting State Up

We've learned how to pass data from a parent component to a child component using props. We've also learned how to change the data within the same component using state. To summarize: state belongs to the component itself and props are used to pass data to child components. 

Would it also be possible to pass data from a child component back to a parent component? Yes it is. :) It's called 'lifting state up'. A more descriptive name would be "establishing two way communication with the parent component". It's done by passing a handler function to the child component as a props.

Try to understand how it works by analyzing the code first: 

<iframe height="400px" width="100%" src="https://repl.it/@Piepongwong/React-Lifting-State-Up?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

The `<ToDo/>` parent component holds multiple tasks in its state. These tasks are represented by simple strings. Based on this state, the `<ToDo/>` component renders the individual `<Task/>` child components. Every `<Task/>` will receive a props with the task string, a props with an index number that identifies the task and a props with a handler function. It's this function that enables the `<Task/>` component to communicate with its parent `<ToDo/>` component. When we click on a task, we'll call this function with the index number as an argument in order to notify the parent component that this task is completed. The parent will update the state and rerender is triggered. This time without the task clicked.

To summarize: in basic react we can deal with data in 3 ways:

* Pass data from a parent to a child component by passing props in the child `<SomeChild someProp={value} />`
* Modify the data from within a component with `setState({someStateKey: "someValue})`
* Pass data up from a child component to a parent component by passing a handler function from the parent to the child as a prop. In the example code this is `<SomeChild aHandlerFunction={updateToDoList} />`

## Interesting questions

* Why do we have to bind updateToDoList?
* Can a child of a child component communicate with the parent of the first child? In other words, can grandparents communicate with their grandchildren?
* And great grandparents with their great grandchildren? 
  
## In class exercise

Your turn. Create a shopping list from scratch. A `<ShoppingList/>` renders `<ShoppingItem/>`'s. If you click on a `<ShoppingItem/>`, you should notify `<ShoppingList/>` by 'lifting state up'. 

### Bonus exercise

For this exercise we'll increase the complexity of our component tree with 1 extra layer. Make a component called `<MasterPlan/>`. This component will render several to `<ToDo/>`'s by passing down the tasks, the title of the list and a handler function as props. If all tasks of `<ToDo/>` are completed, so is the `<ToDo/>` list itself. Remove it from `<Masterplan/>`'s state.

### Looking ahead
Managing 1 layer of complexity is doable, like with the to do list and tasks. With the masterplan it's already starting to get tricky, but any more layers will make you mad! Keep your React project as shallow as possible to keep your sanity. Only add layers of complexity if it's really necessary. You'll find that there's often a simpler, more elegant solution. 

<small> There's also a library called Redux to deal with this issue, but that's outside the scope of this course and for most of your projects an overkill.</small>
  