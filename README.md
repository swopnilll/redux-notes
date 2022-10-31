Redux Architecture

We cannot directly modify or mutate the store. (Redux is built on top of Functional Programing principles).

To update the store, we need to create a function that takes the store as an argument and returns the updated store

Action: 
Plain JS Object that represents what happened. (Could have been termed as Events)

Reducer: 
One or more reducers each responsible for updating a slice of the store. (Works like an Event Handler).
Reducers are pure functions. 
They don't touch the global state.
They don't mutate the argument.
They don't have any side effects. 
They just get the current store instance and return the updated one. 

Example case

User Action: 
User adds an item to the shopping cart 

Redux App:
Action object is created and Dispatched

Store object has a dispatch method that takes an action. 

It will then forward this action to the reducer. 
(We do not call the reducer directly, we just work with the store)
Store is incharge of calling the reducer. 

Reducer computes the new state and returns it to the store. 

Then, the store will set the state internally and then notify the UI components about the update. 
The UI components will pull out the updated data and refresh themselves. 

Dispatch: 

Dispatch is like the entry point to our store.

By dispatching action, we are sending every action through the same entry point. 
We have a central place where we can control what should happen every time the user performs an action. 

Advantage of this approach is that we can log every action, and this is how the Redux Dev tools work. 

It shows every action that has been dispatched and how this data has changed.
We can also easily implement an undo and redo mechanism. 


Bug tracking Example Case Study 

Design the Store: 

[

    {
        id: 1, 
        description: "",
        resolved: false
    },

    {......},
    {......},
    {......},
]


Defining the Action : 

Actions that can be performed in the bug tracking applications: 
    Add a Bug 
    Mark as Resolved 
    Delete a Bug 

Note: Action is  a plain JS object that describes what has happened.
For example:

Example action for adding a bug: 

{
    type: "ADD_BUG",
    description: ""
}

Type is the only property that the redux expects in your action object. 

Description: Data associated with the action.
For example, if a user types something in the text box to add a bug, you store that value in the description property. 


Example action for removing a bug: 

{
    type: "bugRemoved",
    payload: {
        id: 1
    }
}