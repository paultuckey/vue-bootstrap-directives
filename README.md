# Vue 3 Plugin for Bootstrap 5

# ALPHA ALPHA ALPHA ALPHA ALPHA ALPHA ALPHA ALPHA

This plugin is designed to add directives to Vue 3 that can be used to create and control Bootstrap 5 JavaScript 
objects.

This is not intended to be a Bootstrap-Vue component library, but rather a plugin to allow easier control of Bootstrap
objects from Vue.

 - This library has zero dependencies (you inject Bootstrap yourself).
 - Supports Vue 3.x and Bootstrap 5.x

## Install

```shell
npm install vue3-plugin-bootstrap5
```

In your `main.js`:
```javascript

import { createVbPlugin } from 'vue3-plugin-bootstrap5'
import { Modal, Offcanvas, Tooltip } from 'bootstrap'

let vbPlugin = createVbPlugin({ Modal, Offcanvas, Tooltip })

app.use(vbPlugin)
```

See example [main.js](examples/basic/src/main.js)


# Bootstrap Components in Vue

## Alerts

Add `v-vb-is:alert` to your alert element.

On close buttons replace `data-bs-dismiss="alert"` with `v-vb-dismiss:alert`

Listen for events on your alert element with: `v-vb-on:close.bs.alert="someMethod"` and 
`v-vb-on:closed.bs.alert="someMethod"`.

See [AlertExamples.vue](examples/basic/src/components/AlertExamples.vue)



## Carousel

Add `v-vb-is:carousel` to your alert element.

Specify as normal: `data-bs-target`, `data-bs-ride`, `data-bs-slide`, `data-bs-slide-to`, `data-bs-interval`, 
`data-bs-touch`.

Listen for events on your carousel element with: `v-vb-on:slide.bs.carousel="someMethod"` and 
`v-vb-on:slide.bs.carousel="someMethod"`.


## Collapse

TODO


## Dropdowns

TODO


## Modal

See [ModalExamples.vue](examples/basic/src/components/ModalExamples.vue)


## Offcanvas

See [OffcanvasExamples.vue](examples/basic/src/components/OffcanvasExamples.vue)


## Popover

See [PopoverExamples.vue](examples/basic/src/components/PopoverExamples.vue)


## ScrollSpy

TODO


## Tab (Listgroup, Navs)

TODO


## Toast

TODO


## Tooltip

Replace this `<button data-bs-toggle="tooltip" title="Hello World" ...`

With `<button v-vb-toggle:tooltip="'Hello World'" ...`

See [TooltipExamples.vue](examples/basic/src/components/TooltipExamples.vue)


# General

## Bootstrap JavaScript Objects

When `v-vb-is` is added to an element, this plugin will assign the raw Bootstrap object(s) to `$vb` the property.

```html
    <div v-vb-is:modal class="modal" ...>
        ...
    </div>
```

```javascript

    // when `v-vb-is` is used on an element, add a ref (eg ref="exampleEl") then use $vb like this:
    this.$refs.exampleEl.$vb.modal.hide()

    // note, this is same as: bootstrap.Modal.getInstance(this.$refs.exampleEl).hide()

```


## Events

Are added to an element using `@vb-[eventName]="methodToCall""`.  Your method will be called by bootstrap when the 
event it triggered by Bootstrap.

```html
<div ref="exampleModalEvents" 
     v-vb-is:modal 
     @vb-hidden-bs-modal="modalHiddenMethod">...</div>
 ```

Bootstrap events are supported (so long as `@vb-` is specified the same element as `v-vb-is:`).  See bootstrap 
documentation for the full list for each component.


## Cheat Sheet

| Component  | Bootstrap 5 | Vue 3 with this plugin |
| -------------------- | --------------- | ------ | 
| TODO [Alerts](https://getbootstrap.com/docs/5.0/components/alerts/) | `new bootstrap.Alert(el)` | `v-vb-is:alert` | 
| | `data-bs-dismiss="alert"` | `v-vb-dismiss:alert` |
| | `close.bs.alert` | `@vb-close-bs-alert` |
| | `closed.bs.alert` | `@vb-closed-bs-alert` |
| TODO [Carousel](https://getbootstrap.com/docs/5.0/components/carousel/) | |
| | `data-bs-slide="next"` | `v-vb-slide:next` |
| | `data-bs-slide="prev"` | `v-vb-slide:prev` |
| | `data-bs-slide-to="0"` | `v-vb-slide-to` |
| | `slide.bs.carousel` | `@vb-slide-bs-carousel="someMethod"` |
| | `slid.bs.carousel` | `@vb-slid-bs-carousel="someMethod"` |
| TODO [Collapse](https://getbootstrap.com/docs/5.0/components/collapse/) | |
| | `show.bs.collapse` | `@vb-show-bs-collapse="someMethod"` |
| | `shown.bs.collapse` | `@vb-shown-bs-collapse="someMethod"` | 
| | `hide.bs.collapse` | `@vb-hide-bs-collapse="someMethod"` |
| | `hidden.bs.collapse` | `@vb-hidden-bs-collapse="someMethod"` |
| TODO [Dropdowns](https://getbootstrap.com/docs/5.0/components/dropdowns/) | | 
| | `show.bs.dropdown` | `@vb-show-bs-dropdown="someMethod"` |
| | `shown.bs.dropdown` | `@vb-shown-bs-dropdown="someMethod"` |
| | `hide.bs.dropdown` | `@vb-hide-bs-dropdown="someMethod"` |
| | `hidden.bs.dropdown` | `@vb-hidden-bs-dropdown="someMethod"` |
| TODO [List Group](https://getbootstrap.com/docs/5.0/components/list-group/) | | 
| | `show.bs.tab` | `@vb-show-bs-tab="someMethod"` |
| | `shown.bs.tab` |  `@vb-shown-bs-tab="someMethod"` |
| | `hide.bs.tab` | `@vb-hide-bs-tab="someMethod"` |
| | `hidden.bs.tab` | `@vb-hidden-bs-tab="someMethod"` |
| [Modal](https://getbootstrap.com/docs/5.0/components/modal/) | `new bootstrap.Modal(el, optionsObj)` | `v-vb-is:modal="optionsObj"` |
| | `show.bs.modal` | `@vb-show-bs-modal="someMethod"` |
| | `shown.bs.modal` | `@vb-shown-bs-modal="someMethod"` |
| | `hide.bs.modal` | `@vb-hide-bs-modal="someMethod"` |
| | `hidden.bs.modal` | `@vb-hidden-bs-modal="someMethod"` |
| | `hidePrevented.bs.modal` | `@vb-hidePrevented-bs-modal="someMethod"` |
| TODO [Navs & Tabs](https://getbootstrap.com/docs/5.0/components/navs-tabs/) |
| | `show.bs.tab` |  `@vb-show-bs-tab="someMethod"` |
| | `shown.bs.tab` | `@vb-shown-bs-tab="someMethod"` |
| | `hide.bs.tab` | `@vb-hide-bs-tab="someMethod"` |
| | `hidden.bs.tab` | `@vb-hidden-bs-tab="someMethod"` |
| [Offcanvas](https://getbootstrap.com/docs/5.0/components/offcanvas/) | `new bootstrap.Offcanvas(el, optionsObj)` | `v-vb-is:offcanvas="optionsObj"` |
| | `show.bs.offcanvas` | `@vb-show-bs-offcanvas="someMethod"` |
| | `shown.bs.offcanvas` | `@vb-shown-bs-offcanvas="someMethod"` |
| | `hide.bs.offcanvas` | `@vb-hide-bs-offcanvas="someMethod"` |
| | `hidden.bs.offcanvas` | `@vb-hidden-bs-offcanvas="someMethod"` |
| [Popover](https://getbootstrap.com/docs/5.0/components/popovers/) | `new bootstrap.Popover(el, optionsObj)` | `v-vb-is:popover="optionsObj"` |
| | `show.bs.popover` | `@vb-show-bs-popover="someMethod"` |
| | `shown.bs.popover` | `@vb-shown-bs-popover="someMethod"` |
| | `hide.bs.popover` | `@vb-hide-bs-popover="someMethod"` |
| | `hidden.bs.popover` | `@vb-hidden-bs-popover="someMethod"` |
| | `inserted.bs.popover` | `@vb-inserted-bs-popover="someMethod"` |
| TODO [Scrollspy](https://getbootstrap.com/docs/5.0/components/scrollspy/) | `new bootstrap.ScrollSpy(el, optionsObj)` | `v-vb-is:scrollspy="optionsObj"` |
| | `data-bs-spy="scroll"` | `v-vb-is:scrollspy="optionsObj"` |
| | `activate.bs.scrollspy` | `@vb-activate-bs-scrollspy="someMethod"` |




