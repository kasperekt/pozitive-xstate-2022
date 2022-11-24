`useMachine` hook in React:

```js [|1-2|5-9]
import { useMachine } from "@xstate/react";
import myMachine from "./machine";

function App() {
  const [state, send] = useMachine(myMachine, {
    context: {
      value: "...",
    },
  });

  return (
    <div>
      {state.matches("idle") && <span>I am idle</span>}
      <div>{state.context.value}</div>
    </div>
  );
}
```
