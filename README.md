# UI Animation Helpers

This package provides components you can use to easily add animation to your components, along with a set of pre-built animations and timing functions.

## Demos

You can see each of the helpers and animations that are included in action on [this demo page](https://nearform.github.com/ui-animation-helpers/).

## Usage

```
npm install @nearform/ui-animation-helpers
```

## Components

The following components can be used to easily add animation to specific circumstances.

### AnimateOnChange

It can be helpful to let users know when something has changed in our UI. This component aims to help by adding an animation to any content that changes.

    <AnimateOnChange>{value or child components}</AnimateOnChange>

The `AnimateOnChange` component will automatically fade out old content and fade in the new content when the content changes. This could be a number or string or any child components.

The following (optional) properties can be used:

- animationIn
- animationOut
- durationOut
- style

By default, the animation used is a fade out and in. You can specify an animation for both the `out` (when the old content is removed) and `in` (when new content is shown) stages of the animation.

You can reference these by name, for example:

    <AnimateOnChange animationIn="popIn" animationOut="popOut">...</AnimateOnChange>

This will apply a `popOut` animation when removing the old content, and a `popIn` animation on the new content.

### HideUntilLoaded

Nobody likes a half-downloaded image appearing when rendering our UI. This component helps by hiding any children content until a specified image has finished downloading.

    <HideUntilLoaded imageToLoad="[IMAGE_URL]">Your content</HideUntilLoaded>

By default the component will apply an `opacity` of 0 and then a `transition` when loading has completed. This will fade in the fully downloaded content.

You can supply `animationIn` an animation name to use that instead of the default fade.

#### Spinners

You can specify any React component as a "spinner" or loading indicator. This will be shown while the loading is taking place, and then removed once the content is ready to be shown.

```
import MySpinner from '../MySpinner' // This could be an animated SVG or any React component

<HideUntilLoaded imageToLoad="[IMAGE_URL]" Spinner={Spinner}>Your content</HideUntilLoaded>

```

## Animations

This package includes some pre-built animations along with their associated keyframes. As well as supplying the animation names to the above components, you can also apply these animations directly to your components:

```
import { animations } from '@nearform/ui-animation-helpers'

const style = {
  animation: animations.popIn
}

<MyComponent style={style} />

```

In this example, `popIn` evaluates to `pop-in 500ms cubic-bezier(0.19, 1, 0.22, 1) forwards`.

The following animations are included:

- fadeIn
- fadeOut
- fadeInUp
- popIn
- popOut
- bounceIn
- bounceOut
- slideIn
- slideOut

### Using your own animations

Currently there is no option to pass in your own `animation` properties, but this is something I'm keen to add.

## Easings

As well as pre-built animations, this package includes a range of timing functions you can use in animations and transitions.

The full set can be seen in action on the [demo page](https://nearform.github.io/ui-animation-helpers/).

You can apply these to your component styles like so:

```
import { easings } from '@nearform/ui-animation-helpers'

const style = {
  animation: `pop-in ${easings.easeOutExpo} 500ms forwards`
}

<MyComponent style={style} />

```

The full list includes:

- linear
- easeInSine
- easeOutSine
- easeInOutSine
- easeInQuad
- easeOutQuad
- easeInOutQuad
- easeInCubic
- easeOutCubic
- easeInOutCubic
- easeInQuart
- easeOutQuart
- easeInOutQuart
- easeInQuint
- easeOutQuint
- easeInOutQuint
- easeInExpo
- easeOutExpo
- easeInOutExpo
- easeInBack
- easeOutBack
- easeInOutBack

## License

Copyright 2018 nearForm

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.

You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS,

WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

See the License for the specific language governing permissions and limitations under the License.
