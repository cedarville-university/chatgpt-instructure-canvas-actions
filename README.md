# ChatGPT Instructure Canvas Actions

This repository provides a **template for building custom GPTs that can directly interact with Instructure Canvas**. Think of it as a starter kit: you get a ready-made framework for connecting ChatGPT with your institution’s Canvas environment, so you can query data, take actions, and extend Canvas functionality with conversational AI.

---

## Why Use This?

Canvas provides great APIs, but you can't allow just any student to query them with an administrative API key embedded in a Canvas GPT (in fact, doing this may make your CISO's head explode 🤯). 

With this setup, you can enable students to:

* Ask natural-language questions about courses, assignments, annoucements, schedules, syllabi and other course information.
* Limit the resources a student or teacher can access by using Canvas's own OAuth authentication
* Extend ChatGPT with endpoints specific to your institution’s use of Canvas.

This template makes it easier to bridge the gap between conversational AI and the Canvas LMS.

---

## Features

* Ready-to-use template for building ChatGPT actions.
* Built-in support for **OAuth with Canvas**.
* Easy to extend with additional Canvas API endpoints.

---

## Getting Started

### Prerequisites

* Admin access to an Instructure Canvas instance.
* Access to a ChatGPT workspace where you can create custom GPTs with Actions
* A GitHub account (to fork and contribute).

### Setup

1. Clone or fork this repo.
2. Follow the [**Setup Instructions**](./setup.md) to connect your GPT to Canvas.
3. Test the included sample endpoints.
4. Start adding your own endpoints to expand functionality.

---

## OAuth Setup

Setting up OAuth is the trickiest part, so we’ve included detailed instructions here.

[**Setup Instructions**](./setup.md)

Once configured, your GPT will be able to securely interact with Canvas APIs on behalf of the user, using their own credentials.

---

## Contributing

We’d love for you to fork this repo and submit PRs! Contributions can include:

* Adding new Canvas API endpoints.
* Improving the OAuth instructions.
* Enhancing the developer experience.
* Sharing usage examples.

Please follow the standard GitHub flow:

1. Fork the repo.
2. Create a feature branch.
3. Test your new functionality in a Custom GPT
4. Commit your changes.
5. Open a Pull Request. 
   (Include screenshots of the intended functionality working in your GPT.)

---


## Maintainers

Maintained by **Cedarville University**. Contributions welcome from the community!
