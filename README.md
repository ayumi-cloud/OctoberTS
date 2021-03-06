# OctoberTS

TypeScript implementation of the October CMS Frontend Framework

## THIS IS A WORK IN PROGRESS

Do not use this in production. The code is still a mess so don't bother creating larger PRs since most of the code base will be refactored. Please open an issue detailing your implementation before you write code.

```bash
# install deps
yarn
# run tests
yarn test
```

## API

```ts
// Optional, adds IE11 support
import './src/polyfills'

// Import requried features.
import {Build, withAttachLoading, withRequest, withValidation} from './src'

// Attach Framework features to the DOM globally.
const framework = Build(
    withRequest(),       // data-request
    withValidation(),    // data-request-validate
    withAttachLoading(), // data-attach-loading
)

// Use on demand without global event listeners.
const framework = Build()
const response = framework.request('onUpdate')
```

## Implementation status

* [ ] global DOM events api
* [ ] on demand api

### Framework extras

* [x] data-request-validate
* [x] data-attach-loading
* [ ] Loading indicator
* [ ] Flash messages
* [ ] data-request-flash
  * [ ] Error handling
  * [ ] Flash handling

### Framework 

* [x] data-request
* [x] data-track-input


## Incompatibilities

* `eval` attributes are not supported (`data-eval-*`) by design and probably won't be in the future
* There are some limitations to the `data-request-update` syntax: The value has to be wrapped in `'` and functions or variables are not supported (no dynamic evaluation is done!). See [tests](https://github.com/OFFLINE-GmbH/OctoberTS/blob/master/src/utils.test.ts#L10-L35) for examples
* All event listeners need to get their data off of the `e.details` event property, instead of the multiple function attributes