# Cygnus Trio website

## 2022-06-20 last update:

### tasks

- restructure folder so content goes into _data/content.
- the rest of the files in _data are for the working and structure of the site. 


USE PAGE FRONT MATTER!!!! 
for bits of text to show on page!!!

like in concerts page, the more info link and the show/hide button, the past/upcoming concerts titles.

contact form in contact page

the bits in the homepage.

even for the videos in videos page??? maybe not that...

#### html lang atttribute

Then, in order to emphase the actual version, just use CSS (you need to declare the lang attribute on the html, with <html lang="{{ page.lang }}"> in the layout). For instance, if you want to bold it:

.en:lang(en), .fr:lang(fr), .zh:lang(zh){
    font-weight: bold;
}
 maybe better to have both languages as links in the lang switch




#### logic

replace this:
{% if page.lang=="es" %}{{ include.data.title_es }}{% else %}{{ include.data.title }}{% endif %}

with this: 
{ include.data.title[page.lang] }

where the data is structured like this:
title: 
    en: "xxxxx"
    es: "yyyyy"

update nov 2022, nav still using csv data file

### homepage

index.html files now empty. 
homepage layout has all the html code.
text taken from _data/content/home-content.yml, except for text inside caledar wigdet which is from first item in concerts.yml.
n.b. there is not {{ content }} tag in homepage.html layout.

### about page

about-page layout has everything except the biography. 
The biography is what is captured in the {{content}}, but it is not in the about.html page file. It is in an include. 
The include in in md and only has paragraphs. 
This is so that it can be edited without touching any html.
It would also work to make the about page files markdown, and have the biographies there, but this way the biographies live in one folder. 

The following code does it: 
  {% capture biography %}{% include biographies/trio-biography.md %}{% endcapture %}
  {{ biography | markdownify }}

The capture tag assings the variable name biography to everything between the opening and closeing capture tags.
The markdownify liquid filter makes sure it is parsed as markdown. 

### videos page

the videos page now also empty and no {{content}} tag in videos-page layout.

Before there was an include. The old code: 
	<!-- as an include below. hardcoded above. seems to work now? -->
	{% for video in site.data.videos %}
	{% include youtube-video-embed.html data=video %}
	{% endfor %}
but now it's all coded into the layout. 

The youtube-embed include is not in use at the moment. 

The data is taken from _data/content/videos.yml, not from videos.csv any more. 

### concerts page

concerts-page layout 


### contact page

contact-page layout has the contact form, takes text from _data/content/contact-form
{{content}} is the text with out emails. 


## CSS

### background colors

- main (and buttons)
- header and footer (and box shadow)
- card and contact form

### text colors

- h1
- links
- header text: white
- footer text 
- header lang switcher
- button text (and border)

### other colors

- button border (same as but)

## typography

fonts: 


