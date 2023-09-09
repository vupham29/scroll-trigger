# Scroll Trigger

> A mimic version of GSAP ScrollTrigger with 5.86kB 👀

## Getting started

### Initialize

#### Options

| Name                    | Default         | Description                                                                       |
|-------------------------|-----------------|-----------------------------------------------------------------------------------|
| `id`                    | `unique`        | id for clarifying each instance                                                   |
| `start`                 | `top top`       | trigger start position (trigger when the top of the element hits the top of the viewport) |
| `end`                   | `bottom bottom` | end position (when the bottom of the element hits the bottom of the viewport)             |
| `responsive`            | `[]`            | Change the observed breakpoint (`start` and `end`) on different breakpoints        |
| `onEnter:(self) => {}`  | `function`      |                                                                                   |
| `onLeave:(self) => {}`  | `function`      |                                                                                   |
| `onUpdate:(self) => {}` | `function`      |                                                                                   |

### Methods

| Name      | Parameter  | Description                        |
|-----------|------------|------------------------------------|
| `create`  | `object`   | create the instance                |
| `get`     | `id`       | get the ScrollTrigger instance     |
| `destroy` | `instance` | destroy the ScrollTrigger instance |

```js
const instance = ScrollTrigger.create({
    start: 'top center', // trigger when the top of the element hits the center of the viewport
    end: () => '+=' + 300, // end when scroll 300px after trigger
    onEnter: (self) => {
        // get the trigger element
        console.log('The trigger element has entered the viewport', self.trigger);

        // check which direction the trigger enters the viewport
        console.log('Enter back:', self.isEnterBack);
    },
    onUpdate: (self) => {
        console.log('Progress:', self.progress);
    },
    onLeave: (self) => {
        // check which direction the trigger leaves the viewport
        console.log('Leave back:', self.isLeaveBack);

        // destroy the instance when out of viewport
        self.destroy();
    },
    responsive: [
        {
            breakpoint: 1024,
            start: 'top 60%', // top of the element hits the 60% of the viewport
            end: 'bottom 60%+=200px' // end when the bottom of the element hits the (60% + 200px) of the viewport
        }
    ]
});
```

#### Events

| Name                    | Description                                                             |
|-------------------------|-------------------------------------------------------------------------|
| `onEnter:(self) => {}`  | trigger at the first time that the element hits the viewport breakpoint |
| `onUpdate:(self) => {}` | trigger on each scroll event when the element in viewport               |
| `onLeave:(self) => {}`  | trigger when the element goes out of viewport                           |

## Deployment

Run `./public` and `./dev` in live server

```shell
npm run dev
```

Build files from `./src` and `./dev` to `./dist` for production

```shell
npm run build
```

Build files from `./src` for production

```shell
npm run prod
```
