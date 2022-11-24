#### Nested state

_Also known as: hierarchical or compound state_

```js [4-23|5|6-13|14-21]
const machine = createMachine({
  states: {
    LOCKED: {},
    ACTIVE: {
      states: {
        VALID: {
          on: {
            changeValue: [
              { cond: "isIncorrect", target: "INVALID" },
              { target: "VALID" },
            ],
          },
        },
        INVALID: {
          on: {
            changeValue: [
              { cond: "isIncorrect", target: "INVALID" },
              { target: "VALID" },
            ],
          },
        },
      },
    },
  },
});
```
