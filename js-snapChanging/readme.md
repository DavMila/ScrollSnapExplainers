# JS `snapchanging` event

### Status of this Document
This document is intended as a starting point for engaging the community and standards bodies in developing collaborative solutions fit for standardization. As the solutions to problems described in this document progress along the standards-track, we will retain this document as an archive and use this section to keep the community up-to-date with the most current standards venue and content location of future work and discussions.
* This document status: **Active**
* Expected venue: [CSSWG](https://drafts.csswg.org/)
* Current version: this document

## Introduction

CSS scroll snap points are often used as a mechanism to create scroll interactive "selection" components, where selection is determined with javascript with intersection observers and a scroll end guestimate. By creating a built-in event, the invisible state will become actionable, at the right time, and always correct.

## Goals

Help developers sychronize a snapped scroll item with the rest of their interface elements efficiently and effectively.

<br>

## Use Cases

Scroll centric selection:
- Date / Time picker
- Carousel
- Tabs
- State / Country picker

<br>

## Proposed Solution

A new javascript event for scroll snap container elements called `snapchanging`

- Should fire every time, and as soon as, the UA has determined a new snap child during ongoing scroll operation.  

<br>

**Type**: snapchanging (inspired by [`snapped` comment](https://github.com/w3c/csswg-drafts/issues/156#issuecomment-695085852))  
**Interface**: SnapEvent  
**Sync / Async**: Async  
**Bubbles**: No  
**Trusted Targets**: Element, Document
**Cancelable**: No  
**Composed**: Yes  
**Default action**: None  
**Context (trusted events):** 

<br>

- `Event.target`: scroll container the event target is in
- `SnapEvent.snappedList`: an object with 2 keys for each axis, each key returns an array of snapped targets
- `SnapEvent.snappedTargetsList`: an object with 2 keys for each axis, each key returns an array of the aggregated snap children
- `SnapEvent.invokedProgrammatically`: a boolean informing developers if a user or script invoked scroll that caused `snapchanged`
- `SnapEvent.smoothlyScrolled`: a boolean informing developers if the snap change was instant or interpolated

<br>

- `Event.target`: scroll container the event target is in
- `SnapEvent.snappedTargetBlock`: element which has been newly selected to be snapped to in the block axis.
- `SnapEvent.snappedTargetInline`: element which has been newly selected to be snapped to in the inline axis.
<br>

```
interface SnapEvent {
  readonly attribute EventTarget target;

  readonly attribute Node? snappedTargetBlock;
  readonly attribute Node? snappedTargetInline;
};
```

<br>

## Examples

#### 1: Carousel is about to change selection

```js
carouselSnapContainer.addEventListener('snapchanging', event => {
  console.info(`will snap to ${event.snapTargetBlock.id}`);
})
```

#### 2: Tabs have begun snapping to a new element

```js
tabsSnapContainer.onsnapchanging = event = > {
  console.info(`will snap to ${event.snapTargetInline.id}`);
}
```

<br>

## Privacy and Security Considerations

### Privacy

There are no known privacy impact of this feature.

### Security

There are no known security impacts of this feature.

## Contributing
For now, please use this [Discussion](https://github.com/argyleink/ScrollSnapExplainers/discussions/1) for comments and questions, or a Pull Request to offer changes 🙏
