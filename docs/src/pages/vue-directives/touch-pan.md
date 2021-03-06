---
title: Touch Pan Directive
related:
  - /vue-directives/touch-swipe
  - /vue-directives/touch-hold
---
Quasar offers full-featured Vue directives that can totally replace libraries like Hammerjs: `v-touch-pan`, `v-touch-swipe`, `v-touch-hold` and even `v-touch-repeat`.

> **These directives also work with mouse events, not only touch events**, so you are able to build cool functionality for your App on desktops too.

We will be describing `v-touch-pan` on the lines below.

## Installation
<doc-installation directives="TouchPan" />

## Usage
Click then pan in a direction with your mouse on the area below to see it in action.
Page scrolling is prevented, but you can opt out if you wish.

<doc-example title="All directions" file="TouchPan/Basic" />

Panning works both with a mouse or a native touch action.
You can also capture pan to certain directions (any) only as you'll see below.

Example on capturing only horizontal panning.
Notice that on touch capable devices the scrolling is automatically not blocked, since we are only capturing horizontally.

<doc-example title="Horizontally" file="TouchPan/Horizontal" />

Example on capturing only vertically panning. Page scrolling is prevented, but you can opt out if you wish.

<doc-example title="Vertically" file="TouchPan/Vertical" />

Example on capturing panning on custom directions. For this, use modifiers: `up`, `down`, `left`, `right`. Page scrolling is prevented, but you can opt out if you wish.

<doc-example title="Custom directions" file="TouchPan/Custom" />

### Handling Mouse Events
When you want to handle mouse events too, use the `mouse` modifier:

``` html
<!--
  directive will also be triggered by mouse actions
-->
<div v-touch-pan.mouse="userHasPanned">...</div>
```

### Preventing Scroll (on touch capable devices)
By default, the directive does not block page scrolling. If you want to prevent scrolling, then use the `prevent` modifier.

``` html
<div v-touch-pan.prevent="userHasPanned">...</div>
```

### Inhibiting TouchPan
When you want to inhibit TouchPan, you can do so by stopping propagation of the `touchstart`/`mousedown` events from the inner content:

``` html
<div v-touch-pan.mouse="userHasHold">
  <!-- ...content -->
  <div @touchstart.stop @mousedown.stop>
    <!--
      TouchPan will not apply here because
      we are calling stopPropagation() on touchstart
      and mousedown events
    -->
  </div>
  <!-- ...content -->
</div>
```

However, if you are using `capture` or `mouseCapture` modifiers then events will first reach the TouchPan directive then the inner content, so TouchPan will still trigger.

### Note on HMR
Due to performance reasons, when doing HMR updates, all modifiers EXCEPT for direction ones (`left`, `right`, `up`, `down`, `horizontal`, `vertical`) are NOT updated, so you will require a window refresh.

## API
<doc-api file="TouchPan" />
