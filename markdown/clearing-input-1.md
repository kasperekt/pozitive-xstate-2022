#### `if` condition before dispatch?

```js [|2-3|8-10]
function ClearButton() {
  const isLocked = useSelector((state) => state.locked);
  const dispatch = useDispatch();

  return (
    <button
      onClick={() => {
        if (!isLocked) {
          dispatch({ type: "CLEAR" });
        }
      }}
    >
      Clear
    </button>
  );
}
```
