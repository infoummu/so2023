---
layout: page
title: Archive
description: This page displays all posts.
header: All Post
---

### Archive of All Post : 
<!-- 
*********************************************
FOR FD 2022  
*********************************************
-->

<!-- 
*********************************************
EXPERIMENT 2 : ??
*********************************************
-->
<!-- { if post.title == "Cybercrime Forensik Digital -" } -->
<ul>
    {% for post in site.posts %}

        <li>
            <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }} [ {{ post.author }} ] - {{ post.date | date: "%-d %B %Y" }}</a>
        </li>


    {% endfor %}
</ul>

### Referensi Materi Kuliah Sistem Operasi, File PDF:

    {% include files_colec.html folder="reff/materi" %}



***
By: Ikhwan@fedora37.linux