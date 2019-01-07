# ⏰ browser-interaction-time

browser-interaction-time lets you track the time a user is active on your webpage while ignoring time spent on a different tab or with a minimized window. It also ignores the time spent while the user is idle on a web page meaning after a certain amount of time (idleTimeoutMs) without any user interactions (scroll, mousemovement etc) the time will also stop until the next user interaction.

## Importing BrowserInteractionTime

You can import the generated bundle to use the whole library generated by this starter:

```javascript
import BrowserInteractionTime from 'browser-interaction-time'
```

Additionally, you can import the transpiled modules from `dist/lib` in case you have a modular library:

```javascript
import BrowserInteractionTime from 'browser-interaction-time/dist/lib/'
```

## API

### Initialize

```js
import BrowserInteractionTime from 'browser-interaction-time'

const browserInteractionTime = new BrowserInteractiontime({
    {
        timeIntervalEllapsedCallbacks: [],
        absoluteTimeEllapsedCallbacks: [],
        userLeftCallbacks: [],
        userReturnCallbacks: [],
        pauseOnMouseMovement: false,
        pauseOnScroll: false,
        idleTimeoutMs: 3000,
        checkCallbacksIntervalMs: 250
    },
    {
        addEventListener: window.addEventListener,
        removeEventListener: window.addEventListener,
        setInterval: window.setInterval,
        clearInterval: window.clearInterval,
        hidden: document.hidden
    }
})
```

### Start timer

```js
browserInteractionTime.startTimer()
```

### Stop timer

```js
browserInteractionTime.stopTimer()
```

### Adding a callback that is executed on interval

```js
const cb = {
  multiplier: time => time * 2,
  timeInMilliseconds: 1000,
  callback: () => console.log('callback')
}
browserInteractionTime.addTimeIntervalEllapsedCallback(cb)
```

### Adding a callback that is executed on absolute time

```js
const callbackData = {
  timeInMilliseconds: 1000,
  callback: () => console.log('callback')
  pending: false
}
browserInteractionTime.addAbsoluteTimeEllapsedCallback(callbackData)
```

### Adding callback executed when browser tab becomes inactive

```js
const callback = () => console.log('some callback')
browserInteractionTime.addBrowserTabInactiveCallback(callback)
```

### Adding callback executed when browser tab becomes active

```js
const callback = () => console.log('some callback')
browserInteractionTime.addBrowserTabActiveCallback(callback)
```

### Get Time in Milliseconds

```js
browserInteractionTime.getTimeInMilliseconds() // number
```

### Check if timer is running

```js
browserInteractionTime.isRunning() // boolean
```

### Reset all times

```js
browserInteractionTime.reset()
```

### Cleanup event listeners and timers

```js
browserInteractionTime.destroy()
```

## NPM scripts

- `npm t`: Run test suite
- `npm start`: Run `npm run build` in watch mode
- `npm run test:watch`: Run test suite in [interactive watch mode](http://facebook.github.io/jest/docs/cli.html#watch)
- `npm run test:prod`: Run linting and generate coverage
- `npm run build`: Generate bundles and typings, create docs
- `npm run lint`: Lints code
- `npm run commit`: Commit using conventional commit style ([husky](https://github.com/typicode/husky) will tell you to use it if you haven't :wink:)
