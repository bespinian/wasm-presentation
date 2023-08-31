---
author: Lena Fuhrimann
---

# WebAssembly and JavaScript

Love story or competition?

---

## whoami

Lena Fuhrimann
Cloud Architect @ bespinian

```bash
chafa --size 35x35 assets/bespinian.png
```

---

## WebAssembly (WASM)

Wasm is designed as a portable compilation target for programming languages, enabling deployment on the web for client and server applications.

<!--
Efficient and fast: aims to execute at native speed by taking advantage of common hardware capabilities
Open and debuggable: is designed to be pretty-printed in a textual format for debugging, testing, experimenting, optimizing, learning, teaching, and writing programs by hand.
Safe: describes a memory-safe, sandboxed execution environment.
Part of the open web platform: access browser functionality through the same Web APIs accessible from JavaScript.
-->

---

## The Three Paths to Happiness

- Combine WASM and JS
- Replace JS with WASM
- All serverside, no JS

---

### WASM First Class Citizens

- C/C++
- Rust
- AssemblyScript
- C#
- Dart
- F#
- Go
- Kotlin
- Swift
- D
- Pascal
- Zig
- Grain

<!--
No JavaScript! But can be called from there.
AssemblyScript is like TypeScript for WASM.
Many of these have heavy runtimes.
They are mostly different from the high level languages we are used to.
-->

---

### Rust

- Predictable Performance
- Small Code Size
- Modern Ergonomics

---

### Simple DOM Manipulation

```rust
fn start_app() {;
  let window = window().unwrap();
  let document = window.document.unwrap();
  let body = document.body().unwrap();

  let h1 = document.create_element("h1").unwrap();
  let text_node = document.create_text_node("Hello World");

  h1.append_child(&text_node).unwrap();
  body.append_child(&h1).unwrap();
}
```

---

#### Rust

```rust
let h1 = document.create_element("h1").unwrap();
let text_node = document.create_text_node("Hello World");
h1.append_child(&text_node).unwrap();
```

#### JavaScript

```javascript
const h1 = document.createElement("h1");
const textNode = document.createTextNode("Hello World");
h1.appendChild(textNode);
```

<!--
Looks like JS (but without the weird language quirks)
Obviously, this is not how we write JS nor Rust today.
-->

---

## Calculator

```javascript
function calculateResult(num1, num2, operator) {
  switch (operator) {
    case "+":
      return num1 + num2;
    case "-":
      return num1 - num2;
    case "*":
      return num1 * num2;
    case "/":
      return num1 / num2;
  }
}

console.log(calculateResult(3, 5, "+"));
```

---

## wasm-pack

Build a part of an application — using Rust in an existing JavaScript frontend.

```bash
chafa --size 35x35 assets/wasm-ferris.png
```

<!--
npm init rust-webpack calculator-wasm
-->

---

## Replace JS with WASM

---

## Yew

Yew - Build an entire application — an entire web app based in Rust.

```bash
chafa --size 25x35 assets/yew.svg
```

---

### Hello Yew

```rust
#[function_component]
fn App(props &Props) -> Html {
  html! {
    <p>{ &props.text }</p>
  }
}
```

---

### Yew ❤️ HTML

```bash
error: this closing tag has no corresponding opening tag
  --> src/main.rs:4:27
 |
 |    <p>{ &props.text }</span>
 |                      ^^^^^^^
```

---

### State Handling

```rust
struct Model {
  value: i64
}

enum Msg {
  AddOne,
  SubtractOne,
}
```

---

## What Else?

- Native graphics? --> WebGL
- Multithreading? --> Web Workers
- Garbace collection? --> No! It's a feature 😉

---

## All serverside, no JS

---

## HTMX

<!--
https://htmx.org/
-->
