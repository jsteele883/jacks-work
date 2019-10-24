---
title: Algonquin College Preference Center
date: 2018-04-23 20:47:18
excerpt: GDPR compliant Preference Center development
type: work
work: true
hero: algonquin-preference-center.png
preview: /work/algonquin-preference-center.png
tags:
    - HTML
    - CSS
    - JavaScript
    - Marketo
    - Preference Center
---

## Preference Center Development

Algonquin College, based in Ottawa, Ontario, is a progressive school, committed to being a global leader in personalized, digitally connected, experiential learning. Unfortunately, they were saddled with a preference center that was anything but progressive.

Algonquin had previously hired a consultancy firm to build their preference center, but what they got was monstrous: so big and complicated that their Marketing Operations team was never able to get it off the ground. They reached out to Revenue Pulse looking for something simple, clean, and most importantly, user-friendly.

We worked with their team to create a preference center that met brand requirements, regularly referring back to the stakeholders to ensure alignment with their strategy. Ultimately, they were able to launch a version that was in keeping with best practices, meets email compliance requirements, and communicates Algonquin’s progressive feel to their digital audience.

I carried out all the development and custom coding for the preference center. The client wanted to use a Marketo form to track preferences of their students. Marketo forms have some very messy inline CSS embedded by default so in order to style it I have a custom JS script that removes default styling from the form and allows me to apply my own custom style. This grid layout for checkboxes is not possible by default so I remove the inline pixel widths and wrap checkbox input and label to then use CSS grid for the layout.

### Custom Tooltips

It was also requested for custom tooltips to be managed from the form. I was able to map custom tooltips to the relevant input so that the copy for each tooltip can be controlled by the marketer from within Marketo.

<img src="/work/algonquin-tooltip.png" alt="Tooltip Example" style="width:600px;max-width:100%;"/>

### Custom Lightbox

A custom lightbox was also built into the preference center when a user Unsubscribed the fields of the form would be deselected and the user is informed of the outcome.

<img src="/work/algonquin-lightbox.png" alt="Lightbox Example" style="width:800px;max-width:100%;"/>

### Result

Algonquin College now has a well aligned subscription and preference program that meets their brand guidelines and allows their alumni to clearly choose the information that they want to receive. The whole program can also be managed on an ongoing basis by a marketer or a member of their team without touching any code.
