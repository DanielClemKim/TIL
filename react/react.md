# React

React の勉強中記録したい内容をメモ

## Rendering が 2 回行われる問題

- App.js

```jsx
import { useState } from "react";

function App() {
  const [counter, setValue] = useState(0);
  const onClick = () => setValue((prev) => prev + 1);
  console.log("render");
  return (
    <div>
      <h1>{counter}</h1>
      <button onClick={onClick}>Click me</button>
    </div>
  );
}

export default App;
```

基本的にページが Rendering されるのは`state`に変化が加わった場合。よって、上のケースではボタンをクリックし、`setValue`で`counter`の値を変えたあと、"render"という文字列を出力してるので、"render"は一回出力されるはず。
しかし、ブラウザコンソールを開いてみると以下のようになっていた。

<img width="473" alt="render1" src="https://github.com/DanielClemKim/TIL/assets/106340297/c5aa7f1b-03d8-42d5-a0d3-4059f01d3dd5">

### 原因

> **React.StrictMode**

- index.js

```jsx
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

`index.js`を見てみると`<React.StrictMode>`というタグが使われている。これは`create-react-app`を使用した時基本的に生成されるもの。ここでこのタグの役割は、

> `React.StrictMode`はコードの問題を感知し、警告するために構成要素を 2 回 Rendering する。

上記のような理由で Rendering が１回ではなくなったということ。
