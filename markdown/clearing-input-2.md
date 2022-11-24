#### `if` condition in reducer?

```js [3-12|4-6|8-11]
function inputReducer(state, action) {
  switch (action.type) {
    case "CLEAR": {
      if (state.blocked) {
        return state;
      }

      return {
        ...state,
        value: "",
      };
    }
  }
}
```
