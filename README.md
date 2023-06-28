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
