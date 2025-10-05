---
layout: single
title: "Data: Watercolor Painting and dbt"
date: 2023-04-15
categories: Data
header:
  teaser: /images/blog/data/painting.jpg
---

When I first started working with dbt, I felt a rush of excitement as I learned new ways of coding. I particularly enjoyed the use of macros, a tool to use the same snippet of code in multiple locations of your project. Eventually I submitted some code to a peer for review and received feedback that my extensive use of macros made the code confusing to read. Several weeks later, I received feedback that I should have implemented more macros to make the code less repeatable. Receiving contradictory pieces of advice like this can be frustrating but is an essential part of the learning process. In this essay, I paint a picture of common dilemmas that can trip up new dbt developers and advice on how to deal with them.

It has always been my mother's dream to watercolour paint in her retirement. She even bought a set of expensive watercolour paints and paper as she neared retirement. During the pandemic, I spent some of my newly abundant free time painting with my mom's materials. Eventually, I had more experience water colour painting than her and she asked me to teach her.

![My mother's and my watercolor creation](/images/blog/data/painting.jpg)

It's always been a dream of mine to code for work. I even coded in engineering university courses where coding was completely out of place. Recently, I joined a rapidly growing team of analytics engineers. As new people joined our team, I found myself teaching dbt concepts to others.

Like any painter, my mom wanted to produce beautiful paintings, but starting with a completely blank canvas was too daunting. There were too many steps between a blank sheet of paper and a finished painting. As the teacher, I was familiar with all the steps and could even explain them in a short period of time. First you lightly sketch your painting with a pencil, then you experiment with colours on a separate sheet of paper, then you paint 1 object at a time. Still, to start moving forward, I did the sketching and chose the colours, so that my mom could focus only on painting the three houses along the right border of the above painting. Biting off a manageable chunk of the overall painting was key.

A new developer named Logan had just joined our team. He wanted to write code and build tools of value to our users. Our current dbt project was recently conceived and laced with advanced concepts like macros and state capture. I could summarize the steps required for developers to contribute to the project; plan your code changes on paper, pull the latest version of code, write and test your changes, then push to the repository; but this entire process required many skills that were new to Logan. To overcome this, Logan and I worked together on planning the code changes and pulling the latest code. Then we broke down the step "write and test your changes" into 7 smaller steps. I showed Logan the pre-written macros he would need to perform state capture. This absolved Logan from having to confront an overwhelming number of new concepts. Logan was still working with new concepts like dbt and Jinja, but they were manageable, allowing him to focus on writing SQL, a skill set he already had. Within days of first encountering dbt and joining a new team, Logan was developing entire models and pushing code to our project repository. Minimizing the number of new concepts to just a few was key to helping Logan learn and contribute.

Although my mom made quick progress with some painting techniques, she struggled with others and became frustrated. I noticed that the skills which were frustrating her were not as repeatable as those she had acquired quickly. After only a brief explanation of how much paint to apply to the paper, and how this varies with dark and light colours, my mom was correctly putting this principle into practice while painting the three houses. Then we moved to painting the sky and the ocean which required overlapping as well as mixing dark and light colours. Doing this well requires slightly different ratios of paint depending on what colours where interacting with each other. I could explain the principles to her, that dark colours over power light ones and some combinations can't be made lighter after too much dark paint has been applied, but learning the nuance of this technique requires practice. My mom would master the combination of one set of colours and then minutes later struggle with a different set. She had to apply her judgement to each new set of colours. Skills like mixing different coloured paints are what make watercolour painting an art rather than a science. Learned principles are required but so is circumstantial judgement.

New analytics engineer eventually encounter stylistic decisions which lack clear-cut answers. A classic example of this type of decision is "Should I create a macro for this or not?". Other examples include:

- Should I break up this large model into multiple smaller ones?
- Have I spent enough time understanding the business problem and the data sources?
- This solution works now but might not scale well later. Do I ship it or redesign it?
- Am I striking the right balance between quantity and quality of work. Is this enough documenting, commenting, and testing?

Answers these types of questions requires practice over many repetitions. Wrestling with the uncertainty can cause frustration, but it is a necessary part of the journey for new dbt developrs.

To new developers, I offer this advice. 1) It is okay to struggle with some decisions. There may, in fact, be no right answer. Be patient and curious. 2) Don't let perfection become the enemy of progress. Putting your work out there can be intimidating, but it's also the only way to get feedback from others. 3) Seek feedback out from others instead of waiting to receive it. 4) Teach others, and read others code.

For those teaching new develops, remember that biting off manageable chunks of work is key. When my mom and I were painting the sky in the above painting, mixing certain colours was too tricky for my mom, so I mixed them on the side and she applied them. Monitor motivation levels regularly. At the same time, it's equally important for pupils to sit with the uncertainty of ambiguous problems to build the muscle of circumstantial judgement.

Footnote: Thank you to my teammate Christine Gaudet for helping me generate the main ideas of this essay.
