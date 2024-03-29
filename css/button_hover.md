# Button の Hover 効果

## What I learned

<p>

`transition`でアニメーション効果が付与できる。

> :heavy_multiplication_x: ただし、`all`を使うのは避ける

<details>
<summary>
例
</summary>

```css
transition: all 0.2s;
```

</details>
</p>
<p>

要素の形や位置に変化を与える時、`transform`を使用する。 ( 'translate', 'rotate', 'scew', 'scale'等が存在 )。

</p>

<p>

`box-shadow`で影効果を付与できる。影の位置、濃度、サイズ、色を設定。

</p>

## Code

- body element

```css
body {
  font-family: "Roboto" sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #151b29;
}
```

- button element<br>

```css
button {
  background: none;
  color: #ffa260;
  border: 2px solid;
  padding: 1em 2em;
  font-size: 1em;
  transition: color 0.2s, border-color 0.2s, box-shadow 0.2s, transform 0.2s;
}
```

- hover<br>

```css
button:hover {
  border-color: #f1ff5c;
  color: white;
  box-shadow: 0 0.5em 0.5em -0.4em #f1ff5c;
  transform: translateY(-0.25em);
  cursor: pointer;
}
```

### Result example :arrow_down:

<p>

![hovering](https://user-images.githubusercontent.com/106340297/234332599-70375e1c-4a10-49ca-a507-e52e29fc9393.gif)

</p>

---

**Reference**

1. _The Web Developer Bootcamp 2023_ by Colt Steele (https://www.udemy.com/share/105vzw3@Kh4GMxDaMBSPu6-cHVp-P6QoX0TGwJk0ncMMYSGA45EQ18gOB81K85aSNk2BFu6gew==/)
