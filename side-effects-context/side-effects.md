# Side-effects

For side-effects other than simply changing the application state we'll be using the `useEffect` hook. There's three parts to each `useEffect` hook: `setup`, `cleanup`, and `dependencies`where `cleanup` and `dependencies`are optional.



```typescript
useEffect(
    () => {
        // body of a setup function
        return () => {} // cleanup function
    },
    [] // dependency array
)
```

## Setup

The setup is where all the hook's logic is placed.

```typescript
useEffect(() => {
    console.log("setup")
    window.addEventListener("mousemove", (event: MouseEvent) => {
        setPosition({ x: event.clientX, y: event.clientY })
    })
})
```

Hook written like that will run on each render, and create a myriad of event listeners.

> In fact this code will break your browser.

## Cleanup

The setup can return a function that will be called when its time to "undo" the changes the hook has made.

```typescript
useEffect(() => {
    console.log("setup")
    const handler = (event: MouseEvent) => {
        setPosition({ x: event.clientX, y: event.clientY })
    }

    window.addEventListener("mousemove", handler)

    return () => {
        console.log("cleanup")
        window.removeEventListener("mousemove", handler)
    }
})
```

> ⚠ In fact this code will **probably** break your browser.

## Dependencies

We really only want the hook to run once:

```typescript
useEffect(() => {
    console.log("setup")
    const handler = (event: MouseEvent) => {
        setPosition({ x: event.clientX, y: event.clientY })
    }

    window.addEventListener("mousemove", handler)

    return () => {
        console.log("cleanup")
        window.removeEventListener("mousemove", handler)
    }
}, [])
```

Second argument to the `useEffect` function is the array of dependencies. Hook behavior changes depending what's in it:

* `null` or `undefined`: the hook will run for every render
* `[]` \(empty array\): the hook will run once, after the first render
* `[value1, value2]`: the hook will only run when one of the values changes

[![Edit useEffect](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/stupefied-sun-ni09g?fontsize=14)

### Resources

* [Docs: useEffect hook](side-effects.md)
* [A Complete Guide to useEffect](https://overreacted.io/a-complete-guide-to-useeffect/)
* [React's useEffect and useRef Explained for Mortals](https://leewarrick.com/blog/react-use-effect-explained/)

