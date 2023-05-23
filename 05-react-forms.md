# React Forms

| Term | Definition |
| ---- | ---------- |
| __Controlled components__ | React inputs that are controlled by React state, ensuring that the state and view are synchronized. |
| __Uncontrolled components__ | Inputs in React that are not explicitly controlled by React, meaning their state is managed by the browser rather than React. |

---

## Checkboxes

- What is `checked={checked}` doing?
- What is `setChecked(!checked)` doing?
- What happens if we forget the `onChange` event listener?
- What's controlling the checkbox: React or the Browser?

```js
// State
const [checked, setChecked] = useState(false);

// Event Handler
function handleCheckboxChange() {
  setChecked(!checked);
}

// JSX
<input type="checkbox" checked={checked} onChange={handleCheckboxChange} />
```

## Select Dropdowns

- What is the default value of `selectOption`? Why?
- Why are we setting the `selectOption` to `event.target.value`?
- The option value `cats` doesn't match the option display `Cats!`. Is that ok?

```js
// State
const [selectOption, setSelectOption] = useState("");

// Event Handler
function handleSelectChange(event) {
  setSelectOption(event.target.value);
}

// JSX
<select value={selectOption} onChange={handleSelectChange}>
  <option value=""></option>
  <option value="cats">Cats!</option>
  <option value="dogs">Dogs!</option>
</select>
```

## Text Inputs

- What is missing from this text input?
- When does the `onChange` event trigger?

```js
// State
const [nickName, setNickName] = useState("");

// Event Handler
function handleNickNameChange(event) {
  setNickName(event.target.value);
}

// JSX
<input type="text" onChange={handleNickNameChange} />
```

## Form Submission

- When does the `onSubmit` event trigger?
- What does `event.preventDefault()` do?

```jsx
// Event Handler
function handleSubmit(event) {
  event.preventDefault();
  console.log("form submitted");
}

// JSX
<form onSubmit={handleSubmit}>
  <input type="submit" />
</form>
```

## Multiple text inputs with a shared change handler

- What data type is the `user` state?
- Why are we using curly braces when we invoke `setUser({...})`?
- What does `...user` accomplish?
- What's is this `[event.target.id]: event.target.value` doing?
- What other input attribute could you use instead of `id`?

```js
// State
const [user, setUser] = useState({
  firstName: "",
  lastName: "",
  zip: "",
  email: "",
  password: "",
});

// Event Handler
function handleTextChange(event) {
  setUser({
    ...user,
    [event.target.id]: event.target.value,
  });
}

// JSX
<form onSubmit={handleSubmit}>
  <input type="text" value={user.firstName} onChange={handleTextChange} id="firstName" />
  <input type="text" value={user.lastName} onChange={handleTextChange} id="lastName" />
  <input type="number" value={user.zip} onChange={handleTextChange} id="zip" />
  <input type="email" value={user.email} onChange={handleTextChange} id="email" />
  <input type="password" value={user.password} onChange={handleTextChange} id="password" />
  <input type="submit" />
</form>
```

## Resetting the form

- What is the `resetForm()` doing to the state?
- Are we updating the object directly? How can you tell?

```js
function resetForm() {
  setUser({
    firstName: "",
    lastName: "",
    zip: "",
    email: "",
    password: "",
  });
}

function handleSubmit(event) {
  event.preventDefault();
  console.log("form submitted");
  resetForm();
}
```
