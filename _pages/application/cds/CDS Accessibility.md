# CDS Accessibility

CDS identifies service standards and has a [priority 1 checklist for accessibility](https://resources.alpha.canada.ca/resource/a11y-product-lifecycle/).   Accessibility compliance is measures throughout the agile product phases (discovery, alpha, beta, live)

## Discovery

Incorporate accessibility in user research, recognize bias, follow ethical practices, actively listen, test with people, build inclusive personas, offer different ways to engage.

## Alpha

Validate service:

Automated tools to test:

- [All form inputs have explicit labels](https://accessibility.18f.gov/forms/).
- [Text has sufficient color contrast](https://accessibility.18f.gov/color/): All text has a contrast ratio of 4.5:1 with the background.
- [Form instructions are associated with inputs](https://accessibility.18f.gov/forms/).
- [Language is set](https://accessibility.18f.gov/language/) for the page. For sections on the page that differ from the site, language is set.

Manually test:

- - [Site is keyboard accessible](https://accessibility.18f.gov/keyboard/): All interactions can be accessed with a keyboard.
  - [Site is free of keyboard traps](https://accessibility.18f.gov/keyboard/#keyboard-trap): The keyboard focus is never trapped in a loop.
  - [All relevant images use an img tag](https://accessibility.18f.gov/images/).
  - [All images have alt attributes](https://accessibility.18f.gov/images/).
  - [Multimedia is tagged](https://accessibility.18f.gov/multimedia/): All multimedia has appropriate captioning and audio description.
  - If you use color gradients or background images check [text has sufficient color contrast](https://accessibility.18f.gov/color/): All text needs a contrast ratio of 4.5:1 in all display modes (desktop, tablet & mobile).
  - [Site](https://accessibility.18f.gov/keyboard/) [never loses focus](https://accessibility.18f.gov/keyboard/): Focus is always visible when moving through the page with the keyboard.
  - [Tab order is logical](https://accessibility.18f.gov/keyboard/) - The Accessibility Insights tool is useful for this.
  - [Site doesn't timeout unexpectedly](https://accessibility.18f.gov/timeouts/): Identify elements that may "timeout" and verify that the user can request more time.
  - [Tables are coded properly](https://accessibility.18f.gov/tables/): Tables have proper headers and column attributes.
  - [Headings are nested properly](https://accessibility.18f.gov/headings/): Heading elements are nested in a logical way.
  - Audio and video have appropriate captions, transcriptions and described video where necessary.
  - Identifying content only by its shape or location, or using graphical symbol alone to convey information.
  - Use of colour: No colour is used alone to convey meaningful information.
  - Skip links: Are available to bypass blocks of content that are repeated on multiple [Web pages](https://www.w3.org/TR/WCAG21/#dfn-web-page-s).

  Enable adaptive technology for the most common technologies:

  - ask the recognized experts, community of practice, or reach out to Accessibility, Accommodation and Adaptive Computer Technology ([AAACT](https://www.canada.ca/en/shared-services/corporate/aaact-program.html)) program at Shared Services Canada (SSC) to learn about adaptive technology
  - include tools such as voice-over, NVDA (screen reader), zoom test, high contrast

## Beta / Live

- Accessibility audit before you move to public beta.
- ensure you meet priority 2 and 3 checklist for Beta and LIve phases respectively ([more information on CDS accessibility](https://resources.alpha.canada.ca/resource/a11y-product-lifecycle/))