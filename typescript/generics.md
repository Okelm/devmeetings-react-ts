# Generics

[![Edit dazzling-sun-8cl98](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/dazzling-sun-8cl98?fontsize=14)

Generic types are like functions for type declarations the let you pass some arguments \(other types\) later. This is a \(part of\) simple [linked list](https://en.wikipedia.org/wiki/Linked_list) implementation:

```text
type ListNode = {
  value: any;
  next: ListNode|null;
}

function add(head: ListNode, value: any): ListNode {
  const newElement: ListNode = { value, next: null };
  let current: ListNode = head;

  while (current.next) {
      current = current.next;
  }

  current.next = newElement;

  return current;
}
```

This code is fine, it works, but gives no type safety:

```text
const head: ListNode = {
  value: 12,
  next: null
}

add(head, "Hello!")
```

Generics give us a way to specify: this is a `LinkedList` **of numbers**. Or strings. Or whatever.

### A generic type <a id="a-generic-type"></a>

This is the same type, but this time written as generic:

```text
type ListNode<T> = {
  value: T;
  next: ListNode<T>|null;
}
```

`T` is the variable type argument here. When creating the `head` element we'll specify the type of values in the list:

```text
const head: ListNode<number> = {
    value: 12, next: null
}
```

Trying to give different type of value will result in an error:

```text
const head: ListNode<number> = {
    value: "12", next: null
}
```

### Generic functions <a id="generic-functions"></a>

Functions can be generic too! First, let's take a look at a simple example:

```text
function makeTuple<T>(a: T, b: T): [T, T] {
    return [a, b];
}
```

Great thing about generic functions is that TypeScript is actually quite smart about them. This obviously works as expected:

```text
makeTuple<number>(1, 20);
```

But TypeScript is also to guess the type `T` based on the first argument it gets.

```text
makeTuple("Hello", "Devmeetings")
makeTyple("Hello", 13) // error
```

Let's rewrite the `add` function from previous example:

```text
function add<T>(head: ListNode<T>, value: T): ListNode<T> {
  const newElement: ListNode<T> = { value, next: null };
  let current: ListNode<T> = head;

  while (current.next) {
      current = current.next;
  }

  current.next = newElement;

  return current;
}


add(head, 12);
add(head, "That's illegal!"); // error
```

#### Resources <a id="resources"></a>

* [TypeScript Deep Dive: Generics](https://basarat.gitbooks.io/typescript/docs/types/generics.html)
* [Handbook: Generics](https://www.typescriptlang.org/docs/handbook/generics.html)

