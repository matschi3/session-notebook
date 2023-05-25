## createButton with different props

```jsx
import React from "react";
import "./styles.css";

export default function App() {
  return (
    <Button
      color="lightgreen"
      disabled
      isHappy
      text="Ich bin grün"
      onButton={() => {
        alert("ouch, you hit me!");
      }}
      value={3} // numbers have to be inside {}
    />
  );
}

function Button({ color, disabled, isHappy, text, onButton, value }) {
  return (
    <button
      style={{ backgroundColor: color }}
      disabled={disabled}
      onClick={onButton}
    >
      {text}
      <span role="img" aria-label={isHappy ? "happy" : "sad"}>
        {isHappy ? "🙂" : "😕"}
      </span>
      Value is {value}
    </button>
  );
}
```

---
