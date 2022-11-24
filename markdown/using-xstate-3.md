`useInterpret`, `useSelector`, `useActor` hooks in React:

```js [|1-2|5|8-10|16-21|17-18|20|24-25|30-34]
import { useInterpret, useSelector } from "@xstate/react";
import notificationsMachine from "./machine";

function App() {
  const service = useInterpret(notificationsMachine);

  return (
    <MyCustomMachineContext.Provider value={service}>
      <AnActualApp />
    </MyCustomMachineContext.Provider>
  );
}

// ...

function ComponentUsingMachine() {
  const service = useContext(MyCustomMachineContext);
  const count = useSelector(service, (state) => state.context.count);

  return <div>This many notifcations: {state.context.count}</div>;
}

function ComponentThatAlsoSendsEvents() {
  const service = useContext(MyCustomMachineContext);
  const [state, send] = useActor(service);

  return (
    <div>
      <p>This many notifcations: {state.context.count}</p>
      <button
        onClick={() => {
          send("ADD");
        }}
      >
        Add notification
      </button>
    </div>
  );
}
```
