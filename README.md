1. [CODE STYLE] - Don't overuse empty lines between components.

BAD EXAMPLE:
```
<A />


<B />



<C />
```

GOOD EXAMPLE:
```
<A />
<B />
<C />
```

2. [PROJECT STRUCTURE] - create separate folder per component, where you could put all files(styles, components, and so on)
3. [GIT KNOWLEDGE] - check if you added ALL your files to git.
---
1. [CODE STYLE] - If you have < 3 attribues on a tag and the values are short 
write the tag in one line (to make it easier to write and read).

BAD EXAMPLE:
```jsx
<Sum
  a={2}
  b={3}
/>
```

GOOD EXAMPLE:
```jsx
<Sum a={2} b={3} />
```

2. [CODE STYLE] - Use string interpolation inside tag content

BAD EXAMPLE: (it is hard to get the final result)
```jsx
<p>
  Sum of
  {' '}
  {a}
  {' '}
  and
  {' '}
  {b}
  {' '}
  is
  {' '}
  {a + b}
</p>
```
  
GOOD EXAMPLE:
```jsx
<p>
  {`Sum of ${a} and ${b} is ${a + b}`}
</p>
 ```
---
1. [CODE STYLE] - Use destructuring for getting access to values of `props` object

BAD EXAMPLE:
```jsx
export const Component = props => (
  <>
    <h1>{props.firstProperty}</h1>
    <span>{props.secondProperty}</span>
    <p>{props.thirdProperty}</p>
  </>
);
```

GOOD EXAMPLE:
```jsx
export const Component = ({
 firstProperty,
 secondProperty,
 thirdProperty
}) => (
  <>
    <h1>{firstProperty}</h1>
    <span>{secondPropery}</span>
    <p>{thirdProperty}</p>
  </>
);
```

ALSO GOOD EXAMPLE: 

```jsx
export const Component = (props) => {
 const {
  firstProperty,
  secondProperty,
  thirdProperty
} = props; 

 return (
  <>
    <h1>{firstProperty}</h1>
    <span>{secondPropery}</span>
    <p>{thirdProperty}</p>
  </>
 )
};
```
2. [CODE STYLE] - Readabily is everything. Format ternary operator operands correctly - move each operand to the separate line:

BAD EXAMPLE:
```jsx
const value = condition ? firstValue : secondValue;
```

GOOD EXAMPLE:
```jsx
const value = condition 
  ? firstValue 
  : secondValue;
```


3. [CODE STYLE] - Avoid putting several cases to conditional rendering. Create separate variable for the condition.

BAD EXAMPLE:
```jsx
{listEnabled && list.length && smthElse > 0 
  ? <ComponentOne />
  : <ComponentTwo />}
```
---
1. [CODE KNOWLEDGE] - Don't interact with DOM directly, use React as much as possible;
2. [CODE KNOWLEDGE] - When you rendering a list, don't forget to add `key` prop

BAD EXAMPLE:
```jsx
<div>
  {cats.map(cat => <Cat cat={cat} />)}
</div>
```

GOOD EXAMPLE:
```jsx
<div>
  {cats.map(cat => <Cat key={cat.id} cat={cat} />)}
</div>
```
3. [UX] - don't forget to mark the active button to explain to the user what action is active
4. [CODE STYLE] - Function's name should start with a verb (so you could easily tell what your method actually do)

BAD EXAMPLE:
```jsx
const clickHandler = () => {
 console.log('Hello, world');
}
```

GOOD EXAMPLE:
```jsx
const handleClick = () => {
 console.log('Hello, world');
}
```
---
1. [CODE STYLE] - Don't use one-letter variable naming. (It could be confusing for another developer, who reads your code. Also, it would really hard to find this variable in the code editor using search)

BAD EXAMPLE:
```jsx
onChange={(e) => setVariable(e.target.value)}
```

GOOD EXAMPLE:
```jsx
onChange={(event) => setVariable(event.target.value)}
```


ALSO GOOD EXAMPLE:
```jsx
onChange={(changeEvent) => setVariable(changeEvent.target.value)}
```

2. [CODE STYLE] - Don't repeat yourself. If you see that you copy/paste some block code, maybe, it's time to create a separate variable/function
3. [CODE KNOWLEDGE] - If you are using a non-mutating array method, you **don't** need to create a copy of the array

BAD EXAMPLE:
```jsx
const filteredCats = [...cats].filter(cat => cat.age > 6);
```

GOOD EXAMPLE:
```jsx
const filteredCats = cats.filter(cat => cat.age > 6);
```

4. [REACT KNOWLEDGE] - Don't render the component if the property that you pass to the component has `null` or `undefined` value.

BAD EXAMPLE:
```jsx
const CatInfo: FC<Props> = (props) => {
  const { cat } = props;
  
  return (
    {cat 
     ? <p>{cat.name}</p>
     : null
  );
}
```

GOOD EXAMPLE:
```jsx
const CatInfo: FC<Props> = (props) => {
  const { cat } = props;
  
  return (
    <p>{cat.name}</p>
  );
}

....


{cat 
  ? <CatInfo cat={cat} /> 
  : <p>No cat found</p>
}
```

5. Prepare data in one place (App component) and pass it to child components. Don't use `import` keyword in non-root components

BAD EXAMPLE:
```jsx
import owners from './owners';

const CatInfo: FC<Props> = (props) => {
  const { cat } = props;
  const { ownerId } = props;
  
  const foundOwner = owners.find(owner => owner.id === ownerId);
  
  return (
    <>
     <p>{cat.name}</p>
     <p>{foundOwner.name}</p>
    </>
  );
}
```

GOOD EXAMPLE:
```jsx
import owners from './owners';

const catWithOwner = {
  ...cat,
  owner: owners.find(owner => owner.id === ownerId) || null
}

const App: FC = () => {
  return (
    {catWithOwner 
      ? <CatInfo cat={catWithOwner} />
      : <p>No cat was found</p>
    }
  )
}
```
```jsx
import owners from './owners';

const CatInfo: FC<Props> = (props) => {
  const { cat } = props;
  const { owner, name } = props;
  
  return (
    <>
     <p>{name}</p>
     <p>{owner.name}</p>
    </>
  );
}
```

6. [CODE KNOWLEDGE] - While handling form values, trigger submit logic using `onSubmit` prop of form, instead of `onClick` submit button

BAD EXAMPLE:
```jsx

const AddCatForm: FC<Props> = (props) => {
  const handleSubmit = () => {};
  
  return (
    <form>
      <input type="text />
      <button type="submit" onClick={handleSubmit}>
        Add cat
      </button>
    </form>
  );
}
```

GOOD EXAMPLE:
```jsx

const AddCatForm: FC<Props> = (props) => {
  const handleSubmit = () => {};
  
  return (
    <form onSubmit={handleSubmit}>
      <input type="text />
      <button type="submit">
        Add cat
      </button>
    </form>
  );
}
```
