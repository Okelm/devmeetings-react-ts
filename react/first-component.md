# The first component

Here's probably the simplest component we can write, in all it's glory:

![first component](../.gitbook/assets/first_component.png)

```jsx
import React from 'react';

const App: React.FC = () => {
    return (
        <h1>Hello DevMeetings!</h1>
    );
}

export default App;
```

It doesn't do much, but still there's a couple of things to notice:

* `import React from 'react';` - always import React
* `const App: React.FC` - the component is typed as a React's `FunctionalComponent`
* `const App: React.FC = () => { ... }` - it takes no arguments
* `export default App;` is exported from the file

## A single product component

![single product](../.gitbook/assets/single_product.png)

```jsx
import React from 'react';

const App: React.FC = () => {
    const product: Product = {
      name: "JavaScript: The Definitive Guide",
      description: `Since 1996, JavaScript: The Definitive Guide...`,
      price: 28.89
    }

    return (
        <section>
            <h1>Hello DevMeetings!</h1>
            <div>
                <header>{product.name}</header>
                <p>
                    {product.description}
                </p>
                <span>{product.price}$</span>
            </div>
        </section>
    )
}

export default App;
```

* not exactly the best practice, but for now, the data is hardcoded inside of the component
* There's plenty of elements to render, but a component must always return exactly one element or null

### Resources

