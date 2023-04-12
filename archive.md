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

<ul>
<li><a href="/so2023/reff/materi/Andrew_S._Tanenbaum--Modern_Operating_Systems.pdf" title="Andrew_S._Tanenbaum--Modern_Operating_Systems" target="_blank">Andrew_S._Tanenbaum--Modern_Operating_Systems.pdf</a></li>
<li><a href="/so2023/reff/materi/Buku_Ajar_SISTEM_OPERASI.pdf" title="Buku_Ajar_SISTEM_OPERASI" target="_blank">Buku_Ajar_SISTEM_OPERASI.pdf</a></li>
<li><a href="/so2023/reff/materi/Modul-Sistem-Operasi.pdf" title="Modul-Sistem-Operasi" target="_blank">Modul-Sistem-Operasi.pdf</a></li>
<li><a href="/so2023/reff/materi/Operating_System_Concepts_10th_Edition.pdf" title="Operating_System_Concepts_10th_Edition" target="_blank">Operating_System_Concepts_10th_Edition.pdf</a></li>
</ul>

***
By: Ikhwan@fedora37.linux