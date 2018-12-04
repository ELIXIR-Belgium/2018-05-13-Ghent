---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "dc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc")
venue: "ELIXIR-BE"        # brief name of host site without address (e.g., "Euphoric State University")
address: "Overwale 3, 9000 Gent. Clemenspoort: Zaal Neumann"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "be"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "51.033718,3.706540"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use https://www.latlong.net/)
humandate: "May 13-14, 2019"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 am - 5:00 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2019-05-13      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2019-05-14        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Mateusz Kuzak", "Toby Hodges"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Christof De Bo"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["bits@vib.be"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:             # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
  HEADER

  Edit the values in the block above to be appropriate for your workshop.
  If the value is not 'true', 'false', 'null', or a number, please use
  double quotation marks around the value, unless specified otherwise.
  And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
  EVENTBRITE

  This block includes the Eventbrite registration widget if
  'eventbrite' has been set in the header.  You can delete it if you
  are not using Eventbrite, or leave it in, since it will not be
  displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}

<h2 id="general">General Information</h2>

{% comment %}
  INTRODUCTION

  Edit the general explanatory paragraph below if you want to change
  the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use https://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
  DATE

  This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  SPECIAL REQUIREMENTS

  Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges
  on. They should have a few specific software packages installed (listed
  <a href="#setup">below</a>). They are also required to abide by
  {% if page.carpentry == "swc" %}
  Software Carpentry's
  {% elsif page.carpentry == "dc" %}
  Data Carpentry's
  {% elsif page.carpentry == "lc" %}
  Library Carpentry's
  {% endif %}
  <a href="{{site.swc_site}}/conduct.html">Code of Conduct</a>.
</p>

{% comment %}
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.

<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody.
  The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
{% endcomment %}
<p>
  Digital materials can be found linked to the schedule. If we can help making learning easier for
  you please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        or
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>
    {% endfor %}
  {% else %}
    to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment %} 
 SURVEYS - DO NOT EDIT SURVEY LINKS 
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
{% if site.carpentry == "swc" %} 
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "dc" %}
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "lc" %}
<p><a href="{{ site.lc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.lc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
  SCHEDULE

  Show the workshop's schedule.  Edit the items and times in the table
  to match your plans.  You may also want to change 'Day 1' and 'Day
  2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Schedule</h2>

{% if page.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>

{% comment %}
  SYLLABUS

  Show what topics will be covered.

  1. If your workshop is R rather than Python, remove the comment
     around that section and put a comment around the Python section.
  2. Some workshops will delete SQL.
  3. Please make sure the list of topics is synchronized with what you
     intend to teach.
  4. You may need to move the div's with class="col-md-6" around inside
     the div's with class="row" to balance the multi-column layout.

  This is one of the places where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
  SETUP

  Delete irrelevant sections from the setup instructions.  Each
  section is inside a 'div' without any classes to make the beginning
  and end easier to find.

  This is the other place where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a Data Carpentry workshop,
  you will need working copies of the software described below.
  Please make sure to install everything and try opening it to make sure it works
  <em>before</em> the start of your workshop. If you run into any problems,
please feel free to email the instructor or arrive early to your workshop on
the first day.
Participants should bring and use their own laptops to insure the proper setup of
tools for an efficient workflow once you leave the workshop.
</p>

<h3 id="platform_specfic">Platform-specific Notes</h3>
<p>This workshop will be using the software outlined in the install instructions below.
Please see the section for your operating system for those directions.
</p><ul>
<li><a href="#windows">Windows</a>
</li><li><a href="#mac">Mac</a>
</li><li><a href="#linux">Linux</a>
</li></ul>

<h3 id="windows">Windows</h3>
<p>
Please go through all the installation steps below and make sure that
you not only installed them, but start them up to make sure they're working.
If you have any problems, don't hesitate to email the instructors to
ask for help, or arrive early on the first day of the workshop to
get help.
</p>
<div class="row-fluid">
<ol>
<li><b>A spreadsheet program</b></li>
<br>For this workshop you will need a spreadsheet program. Many people already have
Microsoft Excel installed, and if you do, you're set!
<br>
If you need a spreadsheet
program, there are a few other options, like OpenOffice and LibreOffice. Install
instructions for LibreOffice, which is free and open source, are here.
       <ul>
          <li><b>Download the Installer</b>
        <br>Install LibreOffice by going to the <a href="https://www.libreoffice.org/download/libreoffice-fresh/">installation page</a>. The version for Windows
should automatically be selected. Click <b>Download Version 6.0.3 or later</b>. You
will go to a page that asks about a donation, but you don't need to make one.
Your download should begin automatically.
          </li><li><b>Install LibreOffice</b>
            <br>Once the installer is downloaded, double click on it and it should install.
</li><li>To use LibreOffice, double click on the icon and it will open.
</li></ul>
	
<li><b>Putty</b></li>
<br>You will need a terminal program to access the AWS Cloud/HPC cluster.
<ul>
<li>Go to the Putty <a href="http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html">download
page</a>
</li><li>Click on <i>putty.exe</i> link to download the install file
</li><li>To use it, double-click on the downloaded file
</li><li>Follow any installation instructions, if any
</li></ul>

<li><b>FTP Client (Filezilla)</b></li>
<br>An FTP client will help you transfer files easily between your computer and the cloud.
<ul>
<li>Go to the Filezila <a href="https://filezilla-project.org/download.php?show_all=1">download
page</a>
</li><li>Chose the download link appropriate to your system
</li><li>To use it, double-click on the downloaded file
</li><li>Follow any installation instructions, if any
</li><li>At the workshop we will give you additional information (e.g. host, username, port) to connect
</li></ul>


<li><b>IGV</b></li>
<br>If time permits, we will use The Broad Institute's IGV (Integrated Genome Viewer) for
looking at SAM and BAM files, SNPs, and variant calls.
<ul>
<li>To download IGV, please visit
<a href="https://www.broadinstitute.org/software/igv/log-in">this page</a>
 and log in. Please register if you do not already have a login.</li>
<li>Click on the large button for the Download Binary Distribution</li>
<li>Find the zip archive on your computer and expand it</li>
<li>To run IGV, double-click on the IGV.bat file.</li>
</ul>

</ol></div>

<h3 id="mac">Mac</h3>
<p>
Please go through all the installation steps below and make sure that
you not only installed them, but start them up to make sure they're working.
If you have any problems, don't hesitate to email the instructors to
ask for help, or arrive early on the first day of the workshop to
get help.
</p><div class="row-fluid">
<ol>
    <li><b>A spreadsheet program</b></li>
    <br>For this workshop you will need a spreadsheet program. Many people already have
Microsoft Excel installed, and if you do, you're set!
    <br>If you need a spreadsheet
program, there are a few other options, like OpenOffice and LibreOffice. Install
instructions for LibreOffice, which is free and open source, are here.
      <ul>
        <li><b>Download the Installer</b>
        <br>Install LibreOffice by going to the <a href="https://www.libreoffice.org/download/libreoffice-fresh/">installation page</a>. The version for Mac
should automatically be selected. Click <b>Download Version 6.0.3 or later</b>. You
will go to a page that asks about a donation, but you don't need to make one.
Your download should begin automatically.</li>
	 <li><b>Install LibreOffice</b>
         <br>Once the installer is downloaded, double click on it and it should install.</li>
	 <li>To use LibreOffice, double click on the icon and it will open.</li>
      </ul>

   <li><b>FTP Client (Filezilla)</b></li>
<br>An FTP client will help you transfer files easily between your computer and the cloud.
<ul>
<li>Go to the Filezila <a href="https://filezilla-project.org/download.php?show_all=1">download
page</a>
</li><li>Chose the download link appropriate to your system
</li><li>To use it, double-click on the downloaded file
</li><li>Follow any installation instructions, if any
</li><li>At the workshop we will give you additional information (e.g. host, username, port) to connect
</li></ul>


<li><b>IGV</b></li>
<br>If time permits, we will use The Broad Institute's IGV (Integrated Genome Viewer) for
	looking at SAM and BAM files, SNPs, and variant calls.</p>
<ul>
<li>To download IGV, please visit
<a href="https://www.broadinstitute.org/software/igv/log-in">this page</a>
 and log in. Please register if you do not already have a login.</li>
<li>Click on the large button for the Download Binary Distribution</li>
<li>Find the zip archive on your computer and expand it</li>
<li>To run IGV, double-click on the IGV.bat file.</li>
</ul>

</ol>
</div>


<h3 id="linux">Linux</h3>
<p>
Please go through all the installation steps below and make sure that
you not only installed them, but start them up to make sure they're working.
If you have any problems, don't hesitate to email the instructors to
ask for help, or arrive early on the first day of the workshop to
get help.
</p>
<div class="row-fluid">
<ol>
<li><b>A spreadsheet program</b></li>
<br>For this workshop you will need a spreadsheet program. Many people already have
Microsoft Excel installed, and if you do, you're set!
<br>
If you need a spreadsheet
program, there are a few other options, like OpenOffice and LibreOffice. Install
instructions for LibreOffice, which is free and open source, are here.
       <ul>
          <li><b>Download the Installer</b>
        <br>Install LibreOffice by going to the <a href="https://www.libreoffice.org/download/libreoffice-fresh/">installation page</a>. The version for Linux
should automatically be selected. Click <b>Download Version 6.0.3 or later</b>. You
will go to a page that asks about a donation, but you don't need to make one.
Your download should begin automatically.
          </li><li><b>Install LibreOffice</b>
            <br>Once the installer is downloaded, double click on it and it should install.
</li><li>To use LibreOffice, double click on the icon and it will open.
</li>
</ul>

<li><b>FTP Client (Filezilla)</b></li>
<br>An FTP client will help you transfer files easily between your computer and the cloud.
<ul>
<li>Go to the Filezila <a href="https://filezilla-project.org/download.php?show_all=1">download
page</a>
</li><li>Chose the download link appropriate to your system
</li><li>To use it, double-click on the downloaded file
</li><li>Follow any installation instructions, if any
</li><li>At the workshop we will give you additional information (e.g. host, username, port) to connect
</li></ul>


<li><b>IGV</b></li>
<br>If time permits, we will use The Broad Institute's IGV (Integrated Genome Viewer) for
looking at SAM and BAM files, SNPs, and variant calls.
<ul>
<li>To download IGV, please visit
<a href="https://www.broadinstitute.org/software/igv/log-in">this page</a>
 and log in. Please register if you do not already have a login.</li>
<li>Click on the large button for the Download Binary Distribution.</li>
<li>Find the zip archive on your computer and expand it.</li>
<li>To run IGV, double-click on the IGV.bat file.</li>
</ul>


</ol>
</div>


