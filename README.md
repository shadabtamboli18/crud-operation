import React, { useState } from "react";

function App() {
  const [list, setList] = useState([]);
  const [text, setText] = useState("");

  const add = () => {
    setList([...list, text]);
    setText("");
  };

  const remove = (i) => setList(list.filter((_, idx) => idx !== i));

  const edit = (i) => {
    const t = prompt("Edit", list[i]);
    if (t) setList(list.map((item, idx) => (idx === i ? t : item)));
  };

  return (
    <div>
      <input value={text} onChange={(e) => setText(e.target.value)} />
      <button onClick={add}>Add</button>

      {list.map((item, i) => (
        <p key={i}>
          {item}
          <button onClick={() => edit(i)}>Edit</button>
          <button onClick={() => remove(i)}>Delete</button>
        </p>
      ))}
    </div>
  );
}

export default App;
