---
title: Knak Pricing Page
date: 2018-10-25 20:47:18
excerpt: A wordpress page custom built in Flexbox to show Knak pricing
type: work
work: true
preview: /work/knak-pricing-page.png
tags:
    - HTML
    - CSS
    - Wordpress
---

## Knak Pricing Page

In my first few months at knak I was tasked with creating a pricing page to showcase a price comparison for our new Enterprise product. I was sent a beautiful Sketch file containing the desktop view of a 3 column table for each of our products.

<div style="text-align:center"><img src="/work/knak-pricing-desktop.png" alt="Pricing Page Desktop" style="width:800px;max-width:100%;"/></div>

The design looked great and I was excited to start work on implementing the visuals on our Wordpress site. Having a background in email development has given me a good amount of awareness on the difficulties of having complex tables while maintaining a responsive layout when using the standard table HTML syntax. We also wanted to have control over showcasing our flagship product first on the mobile view. Without a mobile design assigned to me I decided to come up with some suggestions to bring back to the designer and our team with some suggestions.

Fortunately this [CSS Tricks article](https://css-tricks.com/accessible-simple-responsive-tables/) on Accessible, Simple, Responsive Tables helped provide inspiration for creating a table layout but using flexbox for responsiveness. I decided that a tab based solution would probably make sense so that we could default to Enterprise on mobile and allow site visitors to easily switch between pricing models and then also toggle down sections to see more information.

I drafted up an initial build in [Codepen](https://codepen.io/jsteele883/pen/JgWLwy) to get buy in before proceeding with the additional work to add the new page to our Wordpress site. The team and our designer were happy with the mobile adjustments.

I built the page out in Wordpress and now visitors to our site get a clear concise view of our pricing model no matter what device they're on.
