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

