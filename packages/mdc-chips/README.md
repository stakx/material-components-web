<!--docs:
title: "Chips"
layout: detail
section: components
excerpt: "Chips are compact elements that represent an attribute, text, entity, or action."
iconId: chip
path: /catalog/chips/
-->

# Chips

<!--<div class="article__asset">
  <a class="article__asset-link"
     href="https://material-components-web.appspot.com/chips.html">
    <img src="{{ site.rootpath }}/images/mdc_web_screenshots/chips.png" width="363" alt="Chips screenshot">
  </a>
</div>-->

Chips are compact elements that allow users to enter information, select a choice, filter content, or trigger an action.

## Design & API Documentation

<ul class="icon-list">
  <li class="icon-list-item icon-list-item--spec">
    <a href="https://material.io/guidelines/components/chips.html">Material Design guidelines: Chips</a>
  </li>
  <li class="icon-list-item icon-list-item--link">
    <a href="https://material-components-web.appspot.com/chips.html">Demo</a>
  </li>
</ul>

## Installation
```
npm install --save @material/chips
```

## Usage

### HTML Structure

```html
<div class="mdc-chip-set">
  <div class="mdc-chip" tabindex="0">
    <div class="mdc-chip__text">Chip content</div>
  </div>
  <div class="mdc-chip" tabindex="0">
    <div class="mdc-chip__text">Chip content</div>
  </div>
  <div class="mdc-chip" tabindex="0">
    <div class="mdc-chip__text">Chip content</div>
  </div>
</div>
```

#### Leading and Trailing Icons

You can optionally add a leading icon (i.e. thumbnail) and/or a trailing icon to a chip. To add an icon, add an `i` element with your preferred icon, give it a class of `mdc-chip__icon`, and a class of either `mdc-chip__icon--leading` or `mdc-chip__icon--trailing`. If you're adding a trailing icon, also set `tabindex="0"` and `role="button"` to make it accessible by keyboard and screenreader.

##### Leading icon

```html
<div class="mdc-chip">
  <i class="material-icons mdc-chip__icon mdc-chip__icon--leading">event</i>
  <div class="mdc-chip__text">Add to calendar</div>
</div>
```

##### Trailing icon

```html
<div class="mdc-chip">
  <div class="mdc-chip__text">Jane Smith</div>
  <i class="material-icons mdc-chip__icon mdc-chip__icon--trailing" tabindex="0" role="button">cancel</i>
</div>
```

### CSS Classes

CSS Class | Description
--- | ---
`mdc-chip-set` | Mandatory. Indicates the set that the chip belongs to
`mdc-chip-set--choice` | Optional. Indicates that the chips in the set are choice chips, which allow a single selection from a set of options.
`mdc-chip` | Mandatory.
`mdc-chip__text` | Mandatory. Indicates the text content of the chip
`mdc-chip__icon` | Optional. Indicates an icon in the chip
`mdc-chip__icon--leading` | Optional. Indicates a leading icon in the chip
`mdc-chip__icon--trailing` | Optional. Indicates a trailing icon in the chip

> _NOTE_: Every element that has an `mdc-chip__icon` class must also have either the `mdc-chip__icon--leading` or `mdc-chip__icon--trailing` class.

### Sass Mixins

To customize the colors of any part of the chip, use the following mixins. 

Mixin | Description
--- | ---
`mdc-chip-set-spacing($gap-size)` | Customizes the amount of space between each chip in the set
`mdc-chip-corner-radius($radius)` | Customizes the corner radius for a chip
`mdc-chip-fill-color-accessible($color)` | Customizes the background fill color for a chip, and updates the chip's ink and ripple color to meet accessibility standards
`mdc-chip-fill-color($color)` | Customizes the background fill color for a chip
`mdc-chip-ink-color($color)` | Customizes the text ink color for a chip, and updates the chip's ripple color to match
`mdc-chip-activated-ink-color($color)` | Customizes text ink color and updates the ripple opacity of a chip in the _activated_ state
`mdc-chip-stroke($width, $style, $color)` | Customizes the border stroke properties for a chip
`mdc-chip-stroke-width($width)` | Customizes the border stroke width for a chip
`mdc-chip-stroke-style($style)` | Customizes the border stroke style for a chip
`mdc-chip-stroke-color($color)` | Customizes the border stroke color for a chip

> _NOTE_: `mdc-chip-set-spacing` also sets the amount of space between a chip and the edge of the set it's contained in.

> _NOTE_: `mdc-chip-ink-color` also updates the chip's text ink color for _hover_ and _activated_ states, and updates the ripple opacity of the chip in the _activated_ state.

### `MDCChip` and `MDCChipSet`

The MDC Chips module is comprised of two JavaScript classes: 
* `MDCChip` defines the behavior of a single chip
* `MDCChipSet` defines the behavior of chips within a specific set. For example, chips in an entry chip set behave differently from those in a filter chip set.

To use the `MDCChip` and `MDCChipSet` classes, [import](../../docs/importing-js.md) both classes from `@material/chips`.

#### `MDCChip`

Method Signature | Description
--- | ---
`toggleActive() => void` | Proxies to the foundation's `toggleActive` method

Property | Value Type | Description
--- | --- | ---
`ripple` | `MDCRipple` | The `MDCRipple` instance for the root element that `MDCChip` initializes

#### `MDCChipSet`

Property | Value Type | Description
--- | --- | ---
`chips` | Array<`MDCChip`> | An array of the `MDCChip` objects that represent chips in the set

### Adapters: `MDCChipAdapter` and `MDCChipSetAdapter`

#### `MDCChipAdapter`

Method Signature | Description
--- | ---
`addClass(className: string) => void` | Adds a class to the root element
`removeClass(className: string) => void` | Removes a class from the root element
`hasClass(className: string) => boolean` | Returns true if the root element contains the given class
`registerInteractionHandler(evtType: string, handler: EventListener) => void` | Registers an event listener on the root element
`deregisterInteractionHandler(evtType: string, handler: EventListener) => void` | Deregisters an event listener on the root element
`notifyInteraction() => void` | Emits a custom event "MDCChip:interaction" denoting the chip has been interacted with, which bubbles to the parent `mdc-chip-set` element

#### `MDCChipSetAdapter`

Method Signature | Description
--- | ---
`hasClass(className: string) => boolean` | Returns whether the chip set element has the given class
`registerInteractionHandler(evtType, handler) => void` | Registers an event handler on the root element for a given event
`deregisterInteractionHandler(evtType, handler) => void` | Deregisters an event handler on the root element for a given event

### Foundations: `MDCChipFoundation` and `MDCChipSetFoundation`

#### `MDCChipFoundation`

Method Signature | Description
--- | ---
`toggleActive() => void` | Toggles the activated class on the chip element

#### `MDCChipSetFoundation`
None yet, coming soon.
