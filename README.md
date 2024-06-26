# Hero motion

[![NPM version](https://img.shields.io/npm/v/hero-motion)](https://www.npmjs.com/package/hero-motion)

🌊 A shared layout animations for [vue](https://vuejs.org/) like [framer motion](https://www.framer.com/motion/), use `layoutId` prop and components will animate from one to another.

- [Demo](https://stackblitz.com/~/github.com/tmg0/hero-motion)

## Features

🏎 Smooth animations based on [@vueuse/motion](https://motion.vueuse.org/)

✨ Written in TypeScript

🙌 Easy to use

✅ Support most of the @vueuse/motion's props

## Installation

```
npm install hero-motion @vueuse/motion @vueuse/core
```

## Usage

### HeroProvider

Suggest to use this component wrap your hole project, this provider will provide private context for `Hero` component.

```vue
<script setup>
import { HeroProvider } from 'hero-motion'
</script>

<template>
  <HeroProvider>
    <RouterView />
  </HeroProvider>
</template>
```

### Hero

You can use hero with both component and composable method.

`Component`

```vue
<script setup>
import { Hero } from 'hero-motion'
</script>

<template>
  <Hero as="div" layout-id="ID" />
</template>
```

`Composable`

```vue
<script setup>
import { ref } from 'vue'
import { useHero } from 'hero-motion'

const domRef = ref()

useHero(domRef, {
  layoutId: 'LAYOUT_ID'
})
</script>

<template>
  <div ref="domRef" />
</template>
```

## Playground

See [playground](./playground/vite/README.md).

## Props

### `props.as`

- Type: `string`
- Default: `'div'`

### `props.layoutId`

- Type: `string | number`
- Default: `undefined`
- Required: `true`

### `props.ignore`

- Type: `string[]`
- Default: `[]`

### `props.transition`

- Type: `Transition`
- Default: `undefined`

Transition props can be used in both `HeroProvider` and `Hero`.

The configuration defined in `HeroProvider` will be used as global default value, and you do not need to re-declare it on each `Hero` components.

```ts
interface Transition {
  delay: number
  repeat: number
  repeatDelay: number
  repeatType: 'loop' | 'mirror' | 'reverse'
  type: 'spring' | 'keyframes'
  stiffness: number
  damping: number
  mass: number
  bounce: number
  duration: number
  ease: string
}
```

**Example:**

```vue
<Hero
  as="div"
  layout-id="cursor"
  :ignore="['width']"
  :transition="{
    duration: 1000,
    type: 'keyframes',
    bounce: 0
  }"
/>
```

## Emit

### `complete`

- Type: `() => void`
- Default: `() => {}`

## License

[MIT](./LICENSE) License © 2024-PRESENT [Tamago](https://github.com/tmg0)
