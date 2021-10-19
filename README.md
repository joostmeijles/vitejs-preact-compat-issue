# 

```
> npm init vite@latest my-vue-app --template preact-ts
> npm i keen-slider
```

Enable preact-compat in vite.config.ts as described here https://github.com/vitejs/vite/issues/1466:
```
import { defineConfig } from 'vite'
import preact from '@preact/preset-vite'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [preact()],
  alias: {
    react: 'preact/compat',
    'react-dom': 'preact/compat'
  }
})
```

Use keen-slider React in app.tsx:
```
import { Logo } from './logo'
import { useKeenSlider } from "keen-slider/react"
import "keen-slider/keen-slider.min.css"

export function App() {
  const [ref] = useKeenSlider<HTMLDivElement>()

  return (
    <>
      <div ref={ref} className="keen-slider">
        <div className="keen-slider__slide number-slide1">1</div>
        <div className="keen-slider__slide number-slide2">2</div>
        <div className="keen-slider__slide number-slide3">3</div>
        <div className="keen-slider__slide number-slide4">4</div>
        <div className="keen-slider__slide number-slide5">5</div>
        <div className="keen-slider__slide number-slide6">6</div>
      </div>
      <Logo />
      <p>Hello Vite + Preact!</p>
      <p>
        <a
          class="link"
          href="https://preactjs.com/"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn Preact
        </a>
      </p>
    </>
  )
}
```

Running `npm run build` results in the following error:
```
node_modules/keen-slider/react.d.ts:1:19 - error TS2307: Cannot find module 'react' or its corresponding type declarations.

1 import React from 'react'
                    ~~~~~~~


Found 1 error.
```
