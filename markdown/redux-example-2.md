```js [1-3|5-11]
const store = configureStore({
  reducer: counterReducer,
});

function App() {
  return (
    <Provider store={store}>
      <YourApplication />
    </Provider>
  );
}
```
