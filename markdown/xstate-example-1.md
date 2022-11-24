```js [|1|6-43|5|7-19|11-17]
import { createMachine } from "xstate";

createMachine({
  id: "InputMachine",
  initial: "VALID",
  states: {
    VALID: {
      on: {
        toggleLock: "LOCKED",
        save: "LOADING",
        changeValue: [
          {
            cond: "isStringInvalid",
            target: "INVALID",
          },
          { target: "VALID" },
        ],
      },
    },
    INVALID: {
      on: {
        clear: "VALID",
        changeValue: [
          {
            cond: "isStringInvalid",
            target: "INVALID",
          },
          { target: "VALID" },
        ],
      },
    },
    LOADING: {
      on: {
        finish: "VALID",
        error: { target: "VALID", actions: ["addError"] },
      },
    },
    LOCKED: {
      on: {
        toggleLock: "VALID",
      },
    },
  },
});
```
