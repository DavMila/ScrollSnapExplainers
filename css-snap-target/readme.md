# CSS :snapped-inline-target & :snapped-block-target pseudo-classes

### Status of this Document
This document is intended as a starting point for engaging the community and standards bodies in developing collaborative solutions fit for standardization. As the solutions to
problems described in this document progress along the standards-track, we will retain this document as an archive and use this section to keep the community up-to-date with the
most current standards venue and content location of future work and discussions.
* This document status: **Active**
* Expected venue: [CSSWG](https://drafts.csswg.org/)
* Current version: this document

## Introduction

todo

### Goals

* todo

### Use Cases

todo

<br>

## Proposed Solution

```css
.inlineSnapScroller > .card:snapped-inline-target {
  ...
}

.verticalSnapScroller > .card:snapped-block-target {
  ...
}
```

### Example 1: todo

todo

```css
:snapped-inline-target {
  --shadow-distance: 30px; /* raised size */
}
```

## Privacy and Security Considerations

### Privacy

There are no known privacy impact of this feature.

### Security

There are no known security impacts of this feature.

## Contributing
For now, please use this [Discussion](https://github.com/argyleink/ScrollSnapExplainers/discussions/5) for comments and questions, or a Pull Request to offer changes 🙏