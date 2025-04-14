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

### Materi Referensi Andrew S. Tanenbaum (per bab):

<ul>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_01-Introduction.pdf">Andrew_S.T._OS_01-Introduction.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_02-Process-and-Threads.pdf">Andrew_S.T._OS_02-Process-and-Threads.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_03-Memory-Management.pdf">Andrew_S.T._OS_03-Memory-Management.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_04-File-Systems.pdf">Andrew_S.T._OS_04-File-Systems.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_05-Input-Output.pdf">Andrew_S.T._OS_05-Input-Output.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_06-Deadlock.pdf">Andrew_S.T._OS_06-Deadlock.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_07-Virtualization-and-the-Cloud.pdf">Andrew_S.T._OS_07-Virtualization-and-the-Cloud.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_08-Multiple-Processor-System.pdf">Andrew_S.T._OS_08-Multiple-Processor-System.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_09-Security.pdf">Andrew_S.T._OS_09-Security.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_10-Case-Study-Linux-Unix-Android.pdf">Andrew_S.T._OS_10-Case-Study-Linux-Unix-Android.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_11-Case-Study-Windows.pdf">Andrew_S.T._OS_11-Case-Study-Windows.pdf</a></li>
  <li><a href="/so2023/reff/materi/andrew/Andrew_OS_12-Operating-System-Design.pdf">Andrew_S.T._OS_12-Operating-System-Design.pdf</a></li>
</ul>

***
By: Ikhwan@fedora42.linux