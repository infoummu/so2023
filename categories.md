---
layout: page
title: All Post
description: All Post Materi FD.
header: All Post
author: Ikhwan N. Elyas
---


### All Post Materi : 

<!-- { if post.title == "Cybercrime Forensik Digital -" } -->
<ul>
    {% for post in site.posts %}
         <!-- <li><a href="#">Site Author : {{ post.author }}</a></li> 
        { if post.title contains "Kuliah FORENSIK DIGITAL" or post.title contains "Cybercrime Forensik Digital  - 19000" or post.title contains "Hasil Tugas Pertemuan" }
        -->
        {% if post.author contains "Ikhwan" %}
            <!-- <li><a href="#">Site Author : {{ post.author }}</a></li> -->
            <li>
                <!-- 
                <a href="{{ post.url | prepend: site.url }}" target="_blank">{{ post.date | date: "%-d %B %Y" }} - {{ post.title }} [ {{ post.author }} ] </a> 
                -->
                <a href="{{ site.baseurl }}{{ post.url}}.html" target="_blank">{{ post.title }} [ {{ post.author }} ] - {{ post.date | date: "%-d %B %Y" }}</a> 
            </li>
        {% endif %}

    {% endfor %}
</ul>





***
By: Ikhwan@fedora37.linux