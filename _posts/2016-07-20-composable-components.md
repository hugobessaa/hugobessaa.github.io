---
layout: post
title: "Composable components"
description: "Component composition is very powerful for components represented
as functions"
image: /public/images/posts/composition/component-composition-hero.png
date:   2016-07-20 17:31
english: true
redirect_from: /2016/07/20/composable-components/
---

Function composition, in mathematics, is the application of a function over the
value of another one to produce a third function. Given `f(x)` and `g(x)`, 
`ƒ: x → f(g(x))` is the composition of `f` with `g`.

A more simple example is the composition of `add2: x → x + 2` with 
`add4: x → x + 4`. It is a function `ƒ` that one can label as `add6` since
`add6: num → add2(add4(num))`. The application of `add6` with `4` can be
represented as: `add6(4) = add2(add4(4)) = add2(8) = 10`.

![Composition of Box with Button]({{ site.baseurl }}/public/images/posts/composition/component-composition-hero.png)

JavaScript functions are not pure mathematical functions, but you can
also compose them. We do this all the time. If we express our components as
functions, we can also compose them.

We are very used to nest HTML elements:

```js
+-<body>----------------------------+
| +-<div>-------------------------+ |
| |  <span>                       | |
| |  Continue?                    | |
| |                               | |
| |  <button>          <button>   | |
| |  +--------+        +--------+ | |
| |  | Cancel |        | Ok     | | |
| |  +--------+        +--------+ | |
| +-------------------------------+ |
+-----------------------------------+
```

With components as functions, we can build much more than just nested HTML
elements. **Structure, behavior, and styles can be composed** to create user
interfaces.

[React][react] was one of the first mainstream JavaScript libraries to propose a
simple way to compose components. You can represent the interface above using
React.

```html
<SectionBox>
  <Modal>
    <InfoMessage>Continue?</InfoMessage>
    <Button>Cancel</Button>
    <Button>Ok</Button>
  </Modal>
</SectionBox>
```

Each component (`<SectionBox>`, `<Modal>`, `<InfoMessage>`, `<Button>`) brings
its own custom behavior. In my opinion, being able to compose components easily
is the killer feature of React.

## An icon and a button

I have to implement something like this in almost every project I build:

```
+---------------+
|    Add (+)    |
+---------------+
```

This button is a simple example of how to compose different components to build
another. We can name this component `IconButton`. It receives `icon`,
`children`, and `onClick` as *props*. A simple implementation would be like:

```html
let IconButton = ({icon, children, onClick}) => 
  <Button onClick={onClick}>
    {children}
    <Icon icon={icon} /> 
  </Button>
```

To build `IconButton`, we used `Button` and `Icon` components. As simple as it
looks like, this component shows us how we can abstract something by composing two
components together. `Button` could have a very complicated logic to decide when
to call the `onClick` callback, and that would be invisible to `IconButton`.

## A button and a tooltip

Some complex UIs need to show some tooltip hints to the user while they use
them, guiding users through the available features. In some project I had to
implement a component very similar to this:

```
+--------------------+
|                    |
|     Hint text      |
|                    |
+---------V----------+
   +--------------+
   |    Button    |
   +--------------+
```

This component isn't that complex. The `Button` is the same component we used before.
`Tooltip` is a new component that receives `children`, `direction` and `hidden`
to render a floating tooltip.

```html
let Tooltip = ({direction, hidden, children}) =>
  <div className={`Tooltip is-${direction} ${hidden ? 'is-hidden' : ''}`}>
    {children}
  </div>

Tooltip.propTypes = {
  direction: React.PropTypes.oneOf(['up', 'down'])
}
```

A component using both could look like this:

```html
class ActionWrapper extends Component {
  constructor (props) {
    super(props)
    this.state = {isTipOpen: false}
  }

  onButtonClick () {
    this.setState({isTipOpen: !this.state.isTipOpen})
  }

  render () {
    return (
      <div>
        <Tooltip direction='up' hidden={!this.state.isTipOpen} />
        <Button onClick={onButtonClick.bind(this)}>Button</Button>
      </div>
    )
  }
}
```

The `onButtonClick` method hides/shows the `Tooltip`. Clicking the button
calls this method. This type of component is simple too.

However, one little requirement can change everything: `Tooltip` had to prevent
overflowing the screen when opened. If the button is rendered too high on the
screen, the tooltip couldn't be hidden and instead open with `direction='down'`.

```
            Normal                    Automatic
    +--------------------+   
    |                    |   
    |     Hint text      |
===========================screen==========================
    |                    |   
    +---------V----------+   
       +--------------+            +--------------+
       |    Button    |            |    Button    |
       +--------------+            +--------------+
                                +---------ʌ----------+
                                |                    |
                                |     Hint text      |
                                |                    |
                                +--------------------+
```

It's not good to implement this logic inside each component that uses `Tooltip`.
We have to abstract this automatic positioning logic inside `Tooltip` and reuse
it everywhere.

As we can compose other components with `Tooltip`, they get this behavior
for free.

## Layout components

The most used components inside React projects I built were the layout
components. These components abstract the logic and the styling of how to
compose other components to create an entire UI.

If we use component composition with the right components, all pages can be just
the composition of a bunch of components and have no page-specific
styling/logic.

In my experience, decoupled components can dramatically improve the 
flexibility of the project. After implementing some sections, designers will
ask for changes.  Product managers and clients will want some new or custom 
feature. If we focus on having a simple and flexible kit of components, 
changing the project won't be hard.

`Spacing` is a component I used in many projects. It is responsible for wrapping
every child inside a `div` and space them accordingly.

```html
<Spacing>
  <Button>Ok</Button>
  <Button>Cancel</Button>
</Spacing>
```

This piece of code would render two buttons separated by a blank spacing.
`Spacing`s can also be nested to create more complex layouts.

```html
<Spacing>
  <span>Continue?</span>
  <Spacing direction='horizontal'>
    <Button>Cancel</Button>
    <Button>Ok</Button>
  </Spacing>
</Spacing>
```
```
+-<Spacing>----------------------+
|  Continue?                     |
|                                |
| +-<Spacing>------------------+ |
| |+--------+        +--------+| |
| || Cancel |        | Ok     || |
| |+--------+        +--------+| |
| +----------------------------+ |
+--------------------------------+
```

Complex pages could compose many `Spacing`s to implement their layouts in
a reusable and straightforward manner.

`Spacing`'s implementation is pretty simple:

```html
let Spacing = ({children = [], direction = 'vertical'}) =>
  <div className={`Spacing is-${direction}`}>
    {[].concat(children).map((child) =>
      <div className='Spacing-item'>{child}</div>
    )}
  </div>
```

Its styles are simple too:

```css
.Spacing {
  display: flex;
}

.Spacing.is-vertical {
  flex-direction: column;
}

.Spacing.is-horizontal {
  flex-direction: row;
}

.Spacing-item {
  padding: 5px;
}
```

For more complex layouts, I recommend [Reflexbox][reflexbox]. It is a kit with
great components to build designs using Flexbox.

## Flexible components

The last example I want to show you is the idea of flexible components. From my
experience, user interfaces change all the time. As UI developers, we need to
improve our projects to embrace change.

Very strict components do not match with flexible projects. We end up
creating and using them a lot.

A simple and strict way of implementing a modal component would be like:

```html
<Modal
  title='Continue?'
  message='This will remove all changes'
  onOk={}
  onCancel={} />
```

It isn't possible to change which buttons render, insert a component
between the title and the content and so on.

By splitting the `Modal` component into many components, we can provide an easy
way of changing the way modals look.

```html
<Modal>
  <ModalTitle>Continue?</ModalTitle>
  <ModalMessage>
    This will remove all changes
  </ModalMessage>
  <ModalActions>
    <Button onClick={}>Ok</Button>
    <Button onClick={}>Cancel</Button>
  </ModalActions>
</Modal>
```

Splitting components give us the flexibility to change how each modal in our
project renders. It is simpler to change the buttons, content placement and
even change the modal style. An excelent example of the power that component
composability gives to us.

You can even create an abstraction of a standard modal and leave the building
blocks open for reusability if needed.

***

These are just some patterns and ideas I used in the projects I built in the
last year using React and other libraries. Feel free to contact me and send any
improvements tips to this article.

## Further reading

- [Thinking React/Composition](https://github.com/krasimir/react-in-patterns/tree/master/patterns/composition)
- [Presentational and Container Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

[Haskell]: https://www.haskell.org/
[Elm]: http://elm-lang.org/
[hyperscrit-helpers]: https://github.com/ohanhi/hyperscript-helpers
[react]: http://reactjs.com/
[jsx]: https://facebook.github.io/jsx/
[reflexbox]: https://github.com/jxnblk/reflexbox
