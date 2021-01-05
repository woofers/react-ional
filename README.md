

# React Micron

[![img](https://github.com/woofers/react-micron/workflows/build/badge.svg)](https://github.com/woofers/react-micron/actions) [![img](https://david-dm.org/woofers/react-micron.svg)](https://www.npmjs.com/package/react-micron) [![img](https://badge.fury.io/js/react-micron.svg)](https://www.npmjs.com/package/react-micron) [![img](https://img.shields.io/npm/dt/react-micron.svg)](https://www.npmjs.com/package/react-micron) [![img](https://img.shields.io/npm/l/react-micron.svg)](https://github.com/woofers/react-micron/blob/master/LICENSE)

`react-micron`


# Installation

**Yarn**

    yarn add react-micron

**npm**

    npm install react-micron


# Usage

```jsx
import React from 'react'
import { Bounce } from 'react-micron'

const App = () => (
  <Bounce>
    <button>Click me!</button>
  </Bounce>
)

export default App
```

Simply add the component to the React application using JSX.

The following example shows the default props set explicitly.

```jsx
import React from 'react'
import { Blink,
         Bounce,
         Fade,
         Flicker,
         Groove,
         Jelly,
         Jerk,
         Pop,
         Shake,
         Squeeze,
         Swing,
         Tada } from 'react-micron'

const App = () => (
  <Bounce
    events="onClick"
    timing="ease-in-out"
    duration={0.45}
    inline={false}
  >
    <button>Click me!</button>
  </Bounce>
)

export default App
```


## Props


### Children

The elements to typed out. **Required**

Each direct child of `Typer` must be of type `TyperElement`.

Type: React.Children or function


### Events

`prefix` is appended to the start of the typed out values. **Default:** None

Can be any value of type `ReactNode`.

Type: String, Array or Object


### Timing

`cursor` indicates if the cursor is displayed. **Default:** `true`

Type: String


### Duration

`cursorDelay` indicates the time it takes for the cursor to blink in seconds. **Default:** `2`

Type: Number or string


### Inline

`cursorWidth` is a scale factor applied to the width of the cursor. **Default:** `1.75`

type: boolean


## Advanced Usage

For more complex usage, using render prop is recommended.

This allows the interaction to be triggered directly, or access micron directly.

```jsx
import React from 'react'
import { Blink,
         Bounce,
         Fade,
         Flicker,
         Groove,
         Jelly,
         Jerk,
         Pop,
         Shake,
         Squeeze,
         Swing,
         Tada } from 'react-micron'

const App = () => (
  <Bounce events={[]} duration={0.1} timing="ease-in">
    {(interaction, micron) => (
      <button
        onClick={interaction}
        onMouseOver={() =>
          micron().interaction('bounce').duration(2).timing('linear')
        }
      >
        Click me!
      </button>
    )}
  </Bounce>
)

export default App
```

Or equivalently using the corresponding HOC

```jsx
import React from 'react'
import { withBlink,
         withBounce,
         withFade,
         withFlicker,
         withGroove,
         withJelly,
         withJerk,
         withPop,
         withShake,
         withSqueeze,
         withSwing,
         withTada } from 'react-micron'

const App = ({ interaction, micron }) => (
  <button
    onClick={interaction}
    onMouseOver={() =>
      micron().interaction('bounce').duration(2).timing('linear')
    }
  >
    Click me!
  </button>
)

export default withBounce(App, {
  events: [],
  timing: 'ease-in',
  duration: 0.1
})
```

In the above 2 examples setting `events` to an empty array disables any of the interaction
done by `react-micron`.  This can then be triggered by using the `interaction` callback directly or using the `micron` API directly.

This allow animations of different speeds or timing to be triggered depending on how the interaction is triggered.
