---
title: "About me"
layout: about
actions:
  - label: "Buy me a coffee"
    icon: paypal
    url: "https://paypal.me/marlonjrbm"
  - label: "Follow me on Twitter"
    icon: twitter
    url: "https://twitter.com/marlonjrbm"
  - label: "Follow me on LinkedIn"
    icon: linkedin
    url: "https://www.linkedin.com/in/marlonjrbm/"
---

Brazilian living in France, I'm a software developer in the EDA industry. I have experience with low-level and high-level systems, having worked with a variety of programming languages, such as C++, Python, Ruby on Rails and ASP.NET. I'm interested in topics such as software engineering, computer security and personal/professional development. My current professional focus is on the EDA (Electronic Design Automation) industry and my skill set include, among others:

- C++ Development
- Revision Control (Git and Perforce)
- Build Automation
- Software Refactoring
- Architectural and Design Patterns
- Software Testing (automated unit and integration testing)
- Algorithm design and analysis (computational complexity, etc)
- Development experience in UNIX-like systems and their associated scripting languages
- Understanding of Software Development Life Cycle (SLDC)
- Knowledge of Software Development Methodologies (Agile, Scrum, etc)
- Experience with Compiler Development
- Experience with EDA Hardware Emulation Tools
- Experience with ML (Machine Learning) algorithms

Being the "social creature" that I am, this site/blog is an attempt of mine of becoming a "social developer", stay tuned!

{% if page.actions %}
  <ul class="intro-actions">
    {% for action in page.actions %}
      <li><a href="{{ action.url }}" class="btn">{% if action.icon %}<span class="icon">{% include {{ action.icon | prepend: 'icon-' | append: '.svg' }} %}</span>{% endif %}{{ action.label }}</a></li>
    {% endfor %}
  </ul>
{% endif %}
