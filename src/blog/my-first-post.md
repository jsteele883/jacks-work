---
title: Building My Portfolio
date: 2018-11-03 20:47:18
excerpt: Deciding on a solution for easily sharing and keeping a record of my work.
type: post
blog: true
tags:
    - HTML
    - CSS
    - JavaScript
---

## Time for a refresh

So I had a Portfolio that I built back in 2016 using a jQuery and HTML template. It did the job, it looked ok but to be honest I found it a little arduous to update every time I wanted to share a new project. Updates involved digging into the HTML files and making manual uploads to AWS S3 everytime I wanted to make a change. With this new project I wanted to create something more scalable and easy for me to maintain without having to write HTML and rearrange the layout with every new piece of work I added.

### Step 1: Design

I would not consider design to be my speciality but I do love being involved in the design process. I also always take good design into consideration with the technical implementations that I work on and I'm always looking to improve my design skills. I recently took an online course on frontend masters called [Design for Developers](https://frontendmasters.com/courses/design-for-developers/) by Sarah Drasner. This course had awesome explanations and examples on creating layouts, CSS Grid, SVG and much much more.

Before starting the design process for this Portfolio project I had a long list of bookmarks and a folder of screenshots of Portfolio's that I liked. I would highly recommend checking out websites of admirable design agencies if you're looking for similar inspiration.

Once you have the inspiration it can be tempting to start coding straight away based on sites that inspire you but in this case I decided to formulate some ideas around the design before even looking at the practical implementation. This would allow me to come up with something more original which I could then refer back to during development to keep me on track with my original intentions.

As a starting point I put together a simple layout composition in sketch.

<div style="text-align:center"><img src="/blog/portfolio-design.png" alt="Blog Design" style="width:800px;max-width:100%;"/></div>

Very Simple... but it gave me enough to start creating my grid composition without having to use any placeholder content gather any assets or write a single line of code. I still refer back to this now to keep me on track.

### Step 2: Concepting

I started concepting how this layout might translate to code by using CodePen. I created multiple pens to cover a range of different views. Colour palettes and typography are something that I struggle to visualize prior to having a layout in place so I kept things very simple to begin with:
