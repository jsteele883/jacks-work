---
title: Building My Portfolio
date: 2019-11-08 20:47:18
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

<div style="text-align:center"><img src="/blog/simple-portfolio-codepen.png" alt="Blog Design" style="width:800px;max-width:100%;"/></div>

I used CSS grid to experiment with ideas based on what I had in Sketch.

<div style="text-align:center"><img src="/blog/colours-portfolio-codepen.png" alt="Colours Design" style="width:800px;max-width:100%;"/></div>

I like using SASS variables in Codepen to experiment with different colour palette options. I combined this with using [Coloors.co](https://coolors.co/) for inspiration. This allowed me to try out different palettes very easily by exporting SASS variables and just copying them into my Codepen to get an idea of how colours might work together.

<div style="text-align:center"><img src="/blog/sass-variables.png" alt="SASS Variables" style="width:400px;max-width:100%;"/></div>

Once I had a concept that I was happy with I was excited to start deciding on a technical solution.

### Step 3: Coding

For a long time I had been thinking that a simple CMS solution would be good to make it easy for me to update recent projects and style them accordingly. For this project I decided that a serverless app could be easier to manage. I also wanted to use Vue.js to code out the front end components. [Vuepress](https://vuepress.vuejs.org/) provides a pretty ideal custom solution for serving up Markdown files within Vue Components. Vue is a pleasure to work with and Markdown is super easy to update with new projects.

Over the past few weeks I have been adding projects and functionality to this site and intend to keep it up to date as a work in progress side project.

### Step 4: Hosting

For hosting and deployments I used [Netflify](https://www.netlify.com/) linked to my Github repo. This literally took 10 minutes to set up and allows me to easily deploy updates when I push to my repo. 
