---
title: Knak Email Signature Builder
date: 2018-10-25 20:47:18
excerpt: An Email signature builder built in Vue.js to keep employees across the company sending consistent emails
type: work
work: true
preview: /knak-signature-builder.jpg
tags:
    - HTML
    - Vue
    - Email Development
---

## Email Signature Solution

I was tasked with finding a way to create a consistent, unified email signature that properly represented our brand, so I set out to develop an email signature generator that would deliver the goods.

Our Former Email Signature was plain, inconsistent and (way too) simple
 
Knak - Old Email Signature

Our old signature was fairly uninspired. The basic signature was created and shared manually, and it wasn’t consistent across Knak and Revenue Pulse, our two brands. We emphasize the importance of consistent branding to our clients, so we wanted to demonstrate that we’re practicing what we preach.

We also wanted to give each of our employees a clear and simple method for uploading their own signature within brand guidelines, while giving them the freedom to decide which contact fields to include.

### Design & Refine
 

Email Signature Generator

To get started, our graphic designer developed a few mockups using Sketch. Once our management team had narrowed it down to a few top choices, we solidified the fields we wanted to include. I then built the user interface around those fields. I included a variety of fields, like LinkedIn, Calendly, and Twitter, but made most of them optional so our employees can include only what they want to share.

I built out the emai HTML into a template that could be used in our signature builder app and developed the signature builder using Vue.js. As the employee fills out the form, the values populate the corresponding variable field in the signature, and column width automatically adjusts based on the number of characters in the field.

Once we had a solid prototype in place, we started testing. We hosted the app on AWS so our team could try it out internally across a variety of email clients. As it turns out, Apple Mail makes it difficult to add a signature, so we adjusted the instructions to fit their specifications. Once the app worked smoothly with Outlook, Gmail, Apple Mail, etc, we rolled it out to our entire team.

Final Product: A Consistent Brand
 



Now, our signatures are consistent and professional across our entire brand. Signatures are set up during the onboarding process, and any updates to our branding are easily shared with the whole team through the app – no individual updates required.

The app can also be repurposed for any of our clients as a custom build and we are considering adding it as a standalone product in Knak. Now that we’ve refined the process, designing a custom signature can be done in a flash.

Your email signature is probably one of your most visible branding opportunities. Take a look at yours. Does it properly represent who you are? If not, perhaps it’s time to give it a makeover.