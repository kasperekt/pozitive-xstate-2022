Pure JavaScript:

```js [|1-3|5|6|7|8]
const machine = createMachine({
  // ...
});

const service = intepret(machine);
service.start();
service.send({ type: "SOME_EVENT" });
service.stop();
```
