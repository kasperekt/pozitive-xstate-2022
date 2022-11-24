#### Parallel state

```js [|2|4-10|11-32]
const machine = createMachine({
  type: 'parallel',
  states: {
    VALIDATION: {
      initial: 'VALID',
      states: {
        VALID: {},
        INVALID: {}
      }
    },
    AUTOCOMPLETE: {
      initial: 'OFF'
      states: {
        OFF: {
          on: {
            toggleAutocomplete: 'LOADING'
          }
        },
        LOADING: {
          invoke: {
            src: 'loadSuggestions'
            onDone: { target: 'ON', actions: 'putSuggestionsInContext' },
            onError: { target: 'OFF' }
          }
        },
        ON: {
          on: {
            toggleAutocomplete: 'OFF'
          }
        }
      },
    },
  },
});
```
