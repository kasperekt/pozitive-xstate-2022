#### Actor model

```js [|1|6|11-17|18-27|21-25]
import autocompleteMachine from "./todo.machine";

const machine = createMachine({
  context: {
    value: '',
    autocompleteRef: [],
  },
  states: {
    ACTIVE: {
      on: {
        toggleAutocomplete: {
          actions: assign({
            autocompleteRef: (context, event) => {
              return spawn(autocompleteMachine, `autocomplete`),
            },
          }),
        },
        changeValue: {
          // ...
          actions: [
            send((context) => {
              return { type: 'VALUE_CHANGED', value: context.value }
            }, {
              to: (context) => context.autocompleteRef
            })
          ]
        }
      },
    },
  },
});
```
