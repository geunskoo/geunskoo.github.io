---
title: "운영체제"
layout: archive
permalink: categories/os
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories["운영체제"] %}
{% for post in posts %}
    {% include archive-single2.html type=page.entries_layout %}
{% endfor %}