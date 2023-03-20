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
            <a href="{{ post.url | prepend: site.baseurl }}">{{ post.date | date: "%-d %B %Y" }} - {{ post.title }} [ {{ post.author }} ] </a>
        </li>


    {% endfor %}
</ul>





***
By: Ikhwan@fedora37.linux