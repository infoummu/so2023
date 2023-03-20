---
layout: page
title: Penelitian
description: Penelitian
---

<!-- BODY -->

<div class="tocContainer">
	<a href="#"  onclick="showx('i3e')">Links Utama</a>
	&nbsp;|&nbsp;<a href="#"  onclick="showx('bab1')">Bab I</a>
	&nbsp;|&nbsp;<a href="#"  onclick="showx('reff')">Refferensi</a>

<!--
	&nbsp;|&nbsp;<a href="#"  onclick="showx('reff-tes')">Tes Video Url</a>
	&nbsp;|&nbsp;<a href="#"  onclick="showx('reff-tes')">Tes Video Url</a>
-->
</div>

<div id="i3e" style="display:block" border="0" class="tocContainer">

	{% include ie-url.html %}

</div>
<div id="bab1" style="display:none" border="0">
	<h4> BAB I </h4>

	{% include penelitian/bab1.html %}

</div>
<div id="reff" style="display:none" border="0">
	<h4> Referensi Papers | <a href="#" id="cl" onclick="rowtc()">Column</a><a href="#" id="rw" onclick="ctrow()">Rows</a>
</h4>

	{% include penelitian/reff-ts.html %}

</div>
<!--
<div id="reff-tes" style="display:none" border="0">
	<h4>Tes Video Url </h4>
<ul>

</ul>

</div>
-->
<!--



<button onclick="topFunction()" id="myBtn" title="Go to top">xxx-Top</button>
-->
