---
title: "Bad AI Ideas: Legal Admin Tool"
description: "In our 'Bad AI Ideas' series, we start with a cautionary tale from the legal sector. 
A potential client's request for a flawless, AI-powered deadline manager serves as a perfect case study for identifying unrealistic project goals and understanding the critical need for human oversight in high-stakes AI applications."
publishDate: "2025-06-22"
tags: ["AI", "Legal", "Admin Tool", "Bad AI Ideas"]
seriesId: "bad_ai_ideas"
orderInSeries: 1
draft: false
---

As you may already know, everyone is talking about AI and how it will change the way we work.
There's a lot of people that want to build AI tools for different industries, either to help their clients or to help themselves.
However, there are certain cases where the lack of knowledge about the current AI capabilities and limitations can lead to bad AI ideas and implementations.
In this blog post, I'll share a real example of an idea in the legal domain, which I consider a bad idea.

# The Project Request

Recently (June 2025), a potential client reached out to me with the following request:

"I want to build a legal AI admin tool.
It's core function centers on automated deadline extraction from US court management orders using OCR and LLMs, and then these deadlines will be added to a calendar (Google, Microsoft, Cal, etc) automatically.
Currently, we have a validated prototype built with low-code tools + OpenAI API calls, but now we need to develop it in a scalable stack, and we need to have 100% accuracy in the deadline extraction and calendar integration.
The project is moving from MVP to fully deployed application, so we have to start in mid-July and we need to do the final launch by the end of August..."

The conversation went on for a while, and finally we arrived to these requirements:

- The tool must be able to extract deadlines from US court management orders.
- The deadlines should be added to a calendar (Google, Microsoft, Cal, etc).
- Calendar integration must enable direct additions to Google and Microsoft calendars, as opposed to individual invites.
- The tool should handle 15-30 deadlines in approximately 10-page documents.
- There are two deadline extraction methods identified: direct dates (e.g., explicitly specified court dates) and calculated dates (e.g., deadlines based on other dates).
- The court documents are in protected/secure PDF format, without any direct text extraction capabilities (copy and paste is not an option), so we need to use OCR to extract the text from the documents.
- 4 weeks of development time, plus 2 weeks of testing and deployment.
- The tool should work automatically and autonomously, without any manual intervention besides uploading the documents and configuring the calendar.
- The accuracy of the deadline extraction must be 100%, and all the deadlines must be added to the calendar.

# The problem

Do you see the problem (or the problems) here?
If you've been in the AI industry for a while (actually building, not yapping about it or hyping it), you probably see the (main) problem immediately.
The 100% accuracy requirement, with automatic and autonomous execution, is the biggest concern here. And from the clients' perspective, I get it. Imagine if the tool misses a U.S. court management order deadline date.
 ``These deadlines, often part of a Case Management Order (CMO), dictate timelines for discovery, motions, and other pretrial procedures. Failure to meet these deadlines can result in sanctions from the court.``
 But, from an AI technical perspective, achieving that 100% accuracy is likely unnattainable. 
 Additionally, considering the "~1 month" deadline that leaves almost no room for testing the possible diverse document formats, the unstructured nature of the text, the relative dates (e.g. "100 days before the trial date"), and the possible dependence on Optical Character Recognition (OCR), which is not always 100% perfect, meeting the overall accuracy target might be prove to be impossible with the current AI capabilities that we dispose of.
As it has been teached by Bryan Bischof[https://x.com/bebischof] and Hamel Husain[https://x.com/hamelhusain], "You have to stop conceiving and managing AI projects like traditional software projects". Rigid roadmaps and fixed deadlines are not the way to go when building AI projects. Instead, we should establish clear and measurable objectives, and build AI products through iterative experiments


Given all these potential problems, and a foreseable failure in achieving the 100% accuracy and autonomy targets, I decided to tell the client that the project is not feasible.
But then, how could I have made this project work? What would be a better way of implementing a solution to the deadline extraction problem?

# How I would have approached this problem

Instead of trying to build a 100% accurate and autonomous system, I would have focused on building a system that is accurate enough to be useful, and that can be used by a human, to reduce the time and effort it takes to extract the deadlines from the documents and create the calendar entries. 

This is a list of changes that I would have made to the project requirements, in order to build a usable AI product:

- **Introduce a human review step.** The 100% accuracy goal is not feasible with current AI capabilities. A human must verify all extracted deadlines before they are finalized. The AI's role is to assist the user as much as possible, not to completely replace them.

- **Build a verification focused interface.** The core of the application should be a user interface designed for rapid verification. It would show the original document on one side and the AI's extracted deadlines on the other. The user could then quickly confirm, edit, or delete the suggestions. The goal is to make the human reviewer faster and more accurate, not to eliminate them.

- **Adopt an iterative development model.** A rigid, one month development timeline for an AI project is a recipe for failure. We should have started with a small, well defined set of documents. We would build a system that works for those first. Then, we would gradually expand its capabilities based on continuous testing and user feedback. This allows for learning and adjustment.

- **Simplify the initial scope.** Instead of building integrations for Google Calendar, Microsoft Calendar, and others from the start, we could begin by generating a standard calendar file, like an `.ics` file. This file can be imported into almost any calendar program. This would focus the initial effort on solving the difficult extraction problem first. Direct integrations can be added later.


By reframing the project this way, we shift the goal from creating an impossible, fully autonomous system to building a powerful assistance tool. This approach respects the limitations of AI while delivering value to the users. It reduces risk, manages expectations, and sets the project on a path to successful adoption.










