# React Resize Sensor

Resize Sensor for React Components.

## Install

```
npm install --save react-resize-sensor
```

## Why?

When building highly interactive user interfaces composed of many portable
UI components that need to look good no matter what layout space they are
dropped into, you might find that Media Queries fall flat on their face for
several reasons.

A few of those reasons:

1. Media queries depend on the window dimensions. There are more things that can
  affect a UI component's dimensions than just the window resize. Maybe you want
  to give the user controls that affect the interface layout?
2. Media queries are global, outside the component's control, and thus risk
  interference from things outside the UI component's control. Globals are evil
  when you want to compose your interface of many small, portable, reusable
  components. Overriding styles all over the place just to fit components into
  multiple custom layouts gets messy quickly.
3. Media queries are limited to only allowing style changes. You may want to do
  more than just change styles. And maybe you want the full power of javascript
  to control how the component responds to it's given dimensions. Example:
  redraw a graphic on html canvas with the canvas' new dimensions.

And for those of you who may be eagerly awaiting Element Queries, reread 2 and 3.

## How?

We place an iframe in your component. Then call your handler when we get a
resize event on the iframe's internal window. Really simple. Correct results
every time.

However, We have to make some tradeoffs for the simplicity and reliability of
this technique. The caveat: iframes are slow. But not noticeable until you have
a sufficient number of them on the page. So I considered this to be a tolerable
tradeoff.

There are other techniques out there. Pull requests welcome.

## Usage

Import:

```javascript
var ResizeSensor = require('react-resize-sensor');
```

The module is CommonJS format. I leave compilation up to you. Maybe you like to
`import` instead of `require`. I assume you are smart enough to figure it out.

Then, place sensor in your render method and set root style position:

```jsx
<div style={{position: 'relative'}}>
  <ResizeSensor onResize={this._handleResize} />
</div>
```

## Isomorphic wat?

The `ResizeSensor` uses a global and binds a DOM event. See source code for more
details. This may or may not jive with your isomorphic astronauts. If you don't
know or care what "isomorphic" means, forget about it.
