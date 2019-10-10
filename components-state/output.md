# Talking to a parent component

We've learned earlier that a parent passes data to a child component by `props`. What about passing data from a child to a parent? The simplest way for child to talk to a parent is to call a function given from that parent:

```jsx
type CounterProps = { increment: () => void; decrement: () => void; }

const Counter: React.FC<CounterProps> = ({ increment, decrement }) => {
    return (
        <div>
            <button onClick={increment}>+</button>
            <button onClick={decrement}>-</button>
        </div>
    )
}
```

```jsx
const App: React.FC = () => {
    const [count, setCount] = useState<number>(0)

    const onIncrement = () => setCount(count + 1)
    const onDecrement = () => setCount(count - 1)

    return (
        <div>
            { count }
            <Counter increment={onIncrement} decrement={onDecrement} />
        </div>
    )
}
```

[![Edit talking with parent](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/peaceful-wood-mlh9k?fontsize=14)

