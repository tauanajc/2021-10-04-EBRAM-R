---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "Encontro Brasileiro de Malacologia"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "br"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "pt"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "0"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "0"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "04-05 Out, 2021"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "13h - 17h BRT"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2021-10-04      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2021-10-05        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Tauana J. Cunha"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Brunno H. B. Alves"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["CunhaT@si.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: https://pad.carpentries.org/XXVII-EBRAM-R # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
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
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
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


<h2 id="general">Informa????es Gerais</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
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

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.

{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}
{% endcomment %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
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
  <strong>Onde:</strong> Esse minicurso ser?? online. Passaremos o link de conex??o por email aos participantes registrados pelo site do EBRAM.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>Quando:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Pr??-requisitos:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Os participantes precisar??o de um computador com sistema operacional
    Mac, Linux, ou Windows no qual tenham permiss??o para instalar novos programas.
  {% endif %}
  Siga as <a href="#setup">instru????es de instala????o</a> dos programas abaixo.
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibilidade:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody.  For workshops at a physical location, the workshop organizers have checked that:
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
  Queremos que esse minicurso seja um ambiente positivo e acess??vel a todos. Por favor entre em contato antes da data de in??cio se houver alguma coisa que possamos fazer para tornar o evento mais acess??vel para voc??.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contato:</strong>
  Escreva para Tauana Cunha
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
  para mais informa????es.
</p>

{% comment %}
<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>
{% endcomment %}

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information
{% endcomment %}
  
<p id="who-can-attend">
    <strong>Quem pode participar?:</strong>
    <a href="https://www.even3.com.br/xxviiebram2021/#atividades">Inscri????o</a> nesse minicurso ?? aberta para participantes do <a href="https://www.even3.com.br/xxviiebram2021">XXVII EBRAM</a>.
</p>


<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}

<h2 id="code-of-conduct">C??digo de Conduta</h2>

<p>
Espera-se que todos os participantes respeitem o <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">C??digo de Conduta</a> do The Carpentries.
</p>

{% comment%}
<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Reporte uma Viola????o do C??digo de Conduta</button>
  </a>
</p>
<hr/>
{% endcomment %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS

<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
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
{% endcomment %}

{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Programa</h2>

{% include custom-schedule.html %}

{% comment %}
{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "incubator" %}
This workshop is teaching a lesson in [The Carpentries Incubator](https://carpentries-incubator.org/).
Please check [the lesson homepage]({{ site.incubator_lesson_site }}) for a list of lesson sections and estimated timings.
{% endif %}
{% endcomment %}

{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please [contact the workshop organisers](#contact) if you would like more information about the planned schedule.
{% endif %}

<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Caderno de Notas Colaborativo</h2>

<p>
Vamos usar esse <a href="{{ page.collaborative_notes }}">documento colaborativo</a> para tomar notas, compartilhar links e c??digo.
</p>
<hr/>
{% endif %}


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Prepara????o necess??ria antes do minicurso</h2>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.


{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "incubator" %}
Please check the "Setup" page of
[the lesson site]({{ site.incubator_lesson_site }}) for instructions to follow
to obtain the software and data you will need to follow the lesson.
{% endif %}
{% endcomment %}

#### R and RStudio

R e RStudio s??o instalados separadamente. R ?? o ambiente
de programa????o por tr??s do RStudio, mas usar o R sozinho
?? pouco pr??tico. RStudio ?? uma interface gr??fica que faz
o uso do R mais f??cil e interativo. ?? necess??rio instalar o R antes de
instalar o RStudio. Depois da instala????o dos dois programas, temos que baixar tamb??m
um pacote espec??fico de R. Siga as instru????es abaixo de acordo com seu sistema operacional,
e depois veja ao fim da p??gina sobre como instalar o pacote **`tidyverse`**.

Uma lista de erros comuns que podem ocorrer durante a instala????o ?? encontrada nessa p??gina (em ingl??s) do The Carpentries: <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.


#### Windows

> ## Se voc?? j?? tem R e RStudio instalados
>
> * Abra o RStudio e clique em "Help" > "Check for updates". Se uma nova vers??o estiver dispon??vel,
> feche o RStudio e baixe a ??ltima vers??o.
> * Para checar qual vers??o do R voc?? est?? usando, abra o RStudio e a primeira mensagem
> que aparece no console indica a sua vers??o atual.
> Digitar `sessionInfo()` no console tamb??m mostrar?? a vers??o do R.
> Cheque no [site do CRAN](https://cran.r-project.org/bin/windows/base/) se uma vers??o
> de R mais recente est?? dispon??vel. Caso sim, baixe e instale essa nova vers??o.
> Caso queira, voc?? pode ver [como remover vers??es antigas do R](https://cran.r-project.org/bin/windows/base/rw-FAQ.html#How-do-I-UNinstall-R_003f)
> do seu computador.
>
> * Siga os [passos para todos](#para-todos) no final dessa p??gina.
{: .solution}

> ## Se voc?? n??o tem R e RStudio instalados
>
> * Baixe o R do
>  [site do CRAN](https://cran.r-project.org/bin/windows/base/release.htm).
> * Abra o arquivo `.exe` que foi baixado.
> * Visite a [p??gina de download do RStudio](https://www.rstudio.com/products/rstudio/download/#download).
> * Na se????o *Installers*, selecione **RStudio x.yy.zzz - Windows Vista/7/8/10** (onde x, y, and z representam o n??mero da vers??o)
> * Clique no link para instalar.
> * Uma vez instalado, abra o RStudio para garantir que est?? funcionando e que nenhuma mensagem de erro aparece.
>
> * Siga os [passos para todos](#para-todos) no final dessa p??gina.
{: .solution}


#### macOS

> ## Se voc?? j?? tem R e RStudio instalados
>
> * Abra o RStudio e clique em "Help" > "Check for updates". Se uma nova vers??o estiver dispon??vel,
> feche o RStudio e baixe a ??ltima vers??o.
> * Para checar qual vers??o do R voc?? est?? usando, abra o RStudio e a primeira mensagem
> que aparece no console indica a sua vers??o atual.
> Digitar `sessionInfo()` no console tamb??m mostrar?? a vers??o do R.
> Cheque no [site do CRAN](https://cran.r-project.org/bin/macosx/) se uma vers??o
> de R mais recente est?? dispon??vel. Caso sim, baixe e instale essa nova vers??o.
>
> * Siga os passos [para todos](#para-todos) no final dessa p??gina.
{: .solution}

> ## Se voc?? n??o tem R e RStudio instalados
>
> * Baixe o R do
>  [site do CRAN](https://cran.r-project.org/bin/macosx/).
> * Selecione o arquivo `.pkg` para a vers??o mais recente.
> Clique no arquivo que foi baixado no seu computador para instalar o R.
> Tamb??m ?? uma boa ideia baixar o [XQuartz](https://www.xquartz.org/), usado por alguns pacotes.
> * Visite a [p??gina de download do RStudio](https://www.rstudio.com/products/rstudio/download/#download).
> * Na se????o *Installers*, selecione **RStudio x.yy.zzz - Mac OS X 10.6+ (64-bit)** (onde x, y, and z representam o n??mero da vers??o)
> * Clique no arquivo que foi baixado no seu computador para instalar o RStudio.
> * Uma vez instalado, abra o RStudio para garantir que est?? funcionando e que nenhuma mensagem de erro aparece.
>
> * Siga os passos [para todos](#para-todos) no final dessa p??gina.
{: .solution}

#### Linux

> ## Instru????es Linux
> * Siga as instru????es para sua distribui????o a partir do
> [CRAN](https://cloud.r-project.org/bin/linux), onde ?? fornecida informa????o
> para baixar a vers??o mais recent do R para as distribui????es mais comuns. Para a maioria das
> distribui????es, voc?? pode usar seu gerenciador de programas (e.g., para Debian/Ubuntu use
> `sudo apt-get install r-base`, e para Fedora `sudo yum install R`), mas n??s n??o recomendamos
> essa estrat??gia porque as vers??es dispon??veis normalmente est??o desatualizadas.
> * Visite a [p??gina de download do RStudio](https://www.rstudio.com/products/rstudio/download/#download).
> * Na se????o *Installers*, selecione a vers??o compat??vel com sua distribui????o e
> instale com seu m??todo preferido (e.g., com Debian/Ubuntu `sudo dpkg -i
> rstudio-x.yy.zzz-amd64.deb` no terminal).
> * Uma vez instalado, abra o RStudio para garantir que est?? funcionando e que nenhuma mensagem de erro aparece.
>
> * Siga os passos [para todos](#para-todos) no final dessa p??gina.
{: .solution}

#### Para todos

* Depois de ter instalado o R e o RStudio, vamos instalar o pacote `tidyverse`. Abra o RStudio clicando no ??cone do programa
  no seu computador e digite: `install.packages("tidyverse")`. Voc?? tamb??m pode instalar pacotes indo em
  Tools -> Install Packages e digitando o nome do pacote.


{% comment %}
Recursos adicionais
{% endcomment %}

<h2 id="recursos">Recursos adicionais</h2>
<p>
Abaixo est??o links para livros online, tutoriais, comunidades de discuss??o, e galerias de gr??ficos para servir de inspira????o e fonte de c??digo.
</p>

Livros:
* [Big Book of R, por Oscar Baruffa](https://www.bigbookofr.com)
* [R for Beginners, por Emmanuel Paradis](https://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf)
* [R para Principiantes, por Emmanuel Paradis](https://cran.r-project.org/doc/contrib/rdebuts_es.pdf)
* [Introdu????o ao R, por Sergio Miranda Freire](http://lampada.uerj.br/arquivosdb/_book2/introducaoR.html)
* [R for Data Science - R4DS](https://r4ds.had.co.nz)

Galerias de gr??ficos ggplot2:
* [The R Graph Gallery](https://www.r-graph-gallery.com) - v?? em ALL no menu para ver todos direto na tela!
* [Top 50 ggplot2 Visualizations - The Master List (With Full R Code)](http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html)
* [ggplot2 extensions - gallery](https://exts.ggplot2.tidyverse.org/gallery/)

Onde buscar ajuda:
* [Stack Overflow](https://stackoverflow.com) (com frequ??ncia ?? um dos primeiros resultados quando procuramos ajuda direto no Google)
* [Rseek](https://rseek.org)
