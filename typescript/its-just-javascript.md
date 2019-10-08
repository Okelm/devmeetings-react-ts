# It's just JavaScript

Here's some TypeScript code:

```typescript
const array = [1, 2, 3, 4, 5]

function squareNumber(num) {
    return num * num
}

const squared = array.map(squareNumber)

squared // [1, 4, 9, 16, 25]
array // [1, 2, 3, 4, 5]

const doubled = array.map(num => num * 2); // [2, 4, 6, 8, 10]

const books = [
    {
        name: "JavaScript: The Definitive Guide",
        description: `Since 1996, JavaScript: The Definitive Guide...`,
        price: 28.89
    },
    {
        name: "Eloquent JavaScript",
        description: `JavaScript lies at the heart...`,
        price: 21.22
    },
    {
        name: "JavaScript: The Good Parts",
        description: `Most programming languages...`,
        price: 16.59
    }
];

const getTitle = book => book.name;

const titles = books.map(getTitle);

const titlesOfExpensiveBooks = books
    .filter(book => book.pirce > 20)
    .map(getTitle);
```

What's the point then? Let's [take a look](https://codesandbox.io/embed/typescript-vs-javascript-n8ci4).

## Benefits of TypeScript

* type safety \(duh...\)
* your editor gets smarter
* no need for as many unit tests as you need now
* almost no entry cost if you already know JS 
* most \(?\) of the latest JS features

## By the way

During this workshop we'll be using the latest version of TypeScript \(`3.6.3`\) that has been installed with `create-react-app` on project creation.

If you haven't created a project yet, now's the last chance, here's what to do:

```bash
npx create-react-app react-ts-devmeeting --typescript
cd react-ts-devmeeting && npm start
```

### Resources

* [Typescript playground](http://www.typescriptlang.org/play/)

