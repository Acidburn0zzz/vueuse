---
category: Utilities
---

# useAsyncState

Reactive async state. Will not block your setup function and will trigger changes once the promise is ready.

## Usage

```ts
import axios from 'axios'
import { useAsyncState } from '@vueuse/core'

const { state, ready } = useAsyncState(
  axios
    .get('https://jsonplaceholder.typicode.com/todos/1')
    .then(t => t.data),
  { id: null },
)
```


<!--FOOTER_STARTS-->
## Type Declarations

```typescript
export interface AsyncStateOptions {
  /**
   * Delay for executing the promise. In milliseconds.
   *
   * @default 0
   */
  delay?: number
  /**
   * Excute the promise right after the function is invoked.
   * Will apply the delay if any.
   *
   * When set to false, you will need to execute it manually.
   *
   * @default true
   */
  immediate?: boolean
  /**
   * Callback when error is caught.
   */
  onError?: (e: Error) => void
}
/**
 * Reactive async state. Will not block your setup function and will triggers changes once
 * the promise is ready.
 *
 * @link https://vueuse.org/useAsyncState
 * @param promise         The promise / async function to be resolved
 * @param initialState    The initial state, used until the first evaluation finishes
 * @param options
 */
export declare function useAsyncState<T>(
  promise: Promise<T> | (() => Promise<T>),
  initialState: T,
  options?: AsyncStateOptions
): {
  state: Ref<T>
  isReady: Ref<boolean>
  /** @deprecated, use isReady instead */
  ready: Ref<boolean>
  error: Ref<
    | {
        name: string
        message: string
        stack?: string | undefined
      }
    | undefined
  >
  execute: (delay?: number) => Promise<void>
}
```

## Source

[Source](https://github.com/vueuse/vueuse/blob/main/packages/core/useAsyncState/index.ts) • [Demo](https://github.com/vueuse/vueuse/blob/main/packages/core/useAsyncState/demo.vue) • [Docs](https://github.com/vueuse/vueuse/blob/main/packages/core/useAsyncState/index.md)


<!--FOOTER_ENDS-->
