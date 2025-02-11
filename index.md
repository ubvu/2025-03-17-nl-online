---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "Radboud&nbsp;Universiteit, Universiteit&nbsp;Leiden, Vrije&nbsp;Universiteit, Tilburg&nbsp;University"
address: "online"
country: "nl"
language: "nl"
latitude: "0"
longitude: "0"
humandate: "Mar 17-18 & 24-25, 2025"
humantime: "09:00-12:00"
startdate: 2025-03-17
enddate: 2025-03-25
instructor: ["Kristina Hettne", "Levi Damsma", "Peter Verhaar", "Matthijs de Zwaan"]
helper:
email: ["k.m.hettne@library.leidenuniv.nl", "levi.damsma@ru.nl", "p.a.f.verhaar@library.leidenuniv.nl", "m.c.de.zwaan@vu.nl"]
collaborative_notes: https://pad.carpentries.org/2025-03-17-nl-online
eventbrite:
---

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}

<h2 id="general">Algemene informatie</h2>


{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
{% endif %}

{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}

<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>

{% elsif online == "true_public" %}

<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>

{% elsif online == "true_private" %}

<p id="where">
  <strong>Waar:</strong> Dit is een online training. Meer gedetailleerde informatie volgt na inschrijving. 
</p>
{% endif %}

{% if page.humandate %}
<p id="when">
  <strong>Wanneer:</strong>
  De ochtenden van 17, 18, 24, 25 maart 2025.
</p>
{% endif %}

<p id="requirements">
  <strong>Vereisten:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Om deel te nemen moet je een computer kunnen gebruiken met een Mac, Linux, of Windows besturingssysteem. Een tablet, Chromebook, etc., werkt niet goed. Je moet rechten hebben om software op de computer te installeren.  
  {% endif %}
  Voorafgaand aan de cursus vragen we je om een bepaalde software te installeren (zie <a href="#setup">hieronder</a>).
</p>

<p id="accessibility">
  <strong>Toegankelijkheid:</strong>
{% if online == "false" %}
  We are committed to making this workshop accessible to everybody.  For workshops at a physical location, the workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>
{% else %}
  Het lesmateriaal wordt voor het begin van de workshop beschikbaar gemaakt. Als op andere manieren het leren kan worden ondersteund, kan de organisatie proberen om dat te faciliteren. Neem daarvoor tijdig contact op.
</p>
{% endif %}

 <p id="contact">
  <strong>Contact</strong>
    Neem contact op met
    {% if page.email %}
    {% for email in page.email %}
    {% if forloop.last and page.email.size > 1 %}
    of
    {% else %}
    {% unless forloop.first %}
    ,    
    {% endunless %}
    {% endif %}
    <a href='mailto:{{ email }}'>{{ page.instructor[forloop.index0] }}</a>
    {% endfor %}
    {% else %}
    to-be-announced
    {% endif %}
    voor meer informatie.
</p>

<p id="roles">
  <strong>Rollen:</strong>
    Om meer te weten te komen over de verschillende rollen tijdens de workshop (wie doet wat) kun je de <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">Workshop FAQ</a> bekijken.  
</p>

<h2 id="code-of-conduct">Gedragscode</h2>

<p>
  Iedereen die deelneemt aan een activiteit van de Carpentries verplicht zich er toe zich te conformeren aan de <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Gedragscode</a> ("Code of Conduct", alleen in het Engels beschikbaar). Die gedragscode beschrijft ook hoe incidenten kunnen worden gemeld.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Rapporteer een schending van de gedragscode</button>
  </a>
</p>
<hr/>


{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Gezamenlijke notities</h2>

<p>
We zullen deze <a href="{{ page.collaborative_notes }}">samenwerkingsomgeving</a> gebruiken voor overleg, notities, het delen van URLs en korte stukjes computercode.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Vul deze vragenlijsten in vóór en na de workshop.</p>
{% if site.carpentry == "incubator" %}
<p><a href="{{ site.incubator_pre_survey }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.incubator_post_survey }}">Post-workshop Survey</a></p>
{% elsif site.incubator_pre_survey or site.incubator_post_survey %}
<div class="alert alert-danger">
WARNING: you have defined custom pre- and/or post-survey links for
a workshop not configured for The Carpentries Incubator
(the value of `curriculum` is not set to `incubator` in `_config.yml`).
Please comment out the `incubator_pre_survey` and `incubator_post_survey` fields
in `_config.yml` or, if this workshop is teaching a lesson in the Incubator,
change the value of `carpentry` to `incubator`.
</div>
{% else %}
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>

<h2 id="schedule">Programma</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include custom-schedule.html %}
{% elsif site.carpentry == "incubator" %}
This workshop is teaching a lesson in [The Carpentries Incubator](https://carpentries-incubator.org/).
Please check [the lesson homepage]({{ site.incubator_lesson_site }}) for a list of lesson sections and estimated timings.
{% endif %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please [contact the workshop organisers](#contact) if you would like more information about the planned schedule.
{% endif %}

<hr/>

<h2 id="setup">Setup</h2>

<p>
  Om deel te nemen aan deze 
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  is het nodig dat je onderstaande software voorafgaand aan de les installeert op je computer.
  Je hebt ook een moderne webbrowser nodig.
</p>
<p>
  De Carpentries houden een lijst bij van problemen die vaak voorkomen tijdens installatie van software: 
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

  {% if site.carpentry == "swc" %}
  {% include swc/setup.html %}
  {% elsif site.carpentry == "dc" %}
  {% include dc-install-instructions %}
  {% elsif site.carpentry == "lc" %}
  {% include lc/setup.html %}
  {% endif %}

{% comment %}
  Deze is ook te gebruiken voor openrefine maar moet dan vertaald worden
  {% include install_instructions/openrefine.html %}
{% endcomment %}
