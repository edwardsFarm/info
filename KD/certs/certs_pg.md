---
layout:    BASE
permalink: certificates
title:    "Certificates of Analysis"
navLinks:
   #- "age verif": "/"
   - about: "about"
   - "certificates of analysis": "#"
   - contact: "contact"
fetch_path: "KD/certs"
extList: [.jpeg, .jpg, .png, .webp, .pdf]
certTypes: ['potency', 'pathogens', 'cannabinoids', 'terpenes', 'pesticides']
---

<style type="text/css">
:root{
  --edsGrey:      #231F20;
  --edsWhite:     #FFFFFF;
  --edsTan:       #DAB677;
  --edsTanRgb:     218, 182, 119;
  --edsTanVryLgt: #f7e9d0;
  --edsTanLgt:    #fcd186;
  --edsTanDark:   #634004;
}
.accordion{
  --bs-accordion-color:        var(--bs-body-color);
  --bs-accordion-active-color: var(--bs-primary-text-emphasis);
  --bs-accordion-bg:           var(--bs-body-bg);
  --bs-accordion-active-bg:    var(--bs-primary-bg-subtle);
  --bs-accordion-border-color:    var(--edsGrey);
  --bs-accordion-border-width:    1px;
  --bs-accordion-btn-color:       var(--edsGrey);
  --bs-accordion-btn-bg:          var(--edsTan);
  /*--bs-accordion-btn-icon:        var(--edsGrey);*/
  /*--bs-accordion-btn-active-icon: var(--edsGrey);*/
  /*--bs-accordion-active-color:    green;*/
  --bs-accordion-active-bg:       var(--edsTan);
  --bs-accordion-btn-focus-border-width: 1px;
  --bs-accordion-btn-focus-border-color: var(--edsGrey);
  --bs-accordion-btn-focus-box-shadow:   0 0 0 0px rgba(var(--edsTanRgb), .01);/*edsTan == rgb(218, 182, 119)*/
}
  object.pdf_embed{
    width:   100%;
    height:  600px;
    margin:  auto;
    display: flex;
    border: 2px solid black;
  }
  summary{
    font-size: calc(1.375rem + 1.5vw); /*h1*/
  }

  .wrapStrnHdr h4, .wrapStrnHdr img{
    display: inline-block;
  }
  h1.yrHdr{
    margin-top: 20px;
  }
  h4.strnHdr{
    margin-top: 10px;
    font-style: italic;
  }
  img.arrow{
    height: 20px;
    width: 40px;
    margin: 0px 0px 8px -45px;
    /*preserveAspectRatio:none*/
  }

  .wrapCerts{
    margin: 0px 0px 5px 60px;
  }
  .strnTxt{
    margin: 0px 0px 0px 20px;
    font-weight: 300;
  }
  .strnSpan{
    margin-right: 8.1px;
  }
  .pdfLink{
    margin-right: 5px;
  }

</style>

<div class="wrapCerts">

{%- comment -%}<!-- IMPORTANT: loop reqs path struc as follows: YYYY-MM-DD/My Strain Name/my_cert_filename.ext -->{%- endcomment -%}

{%- include fetchers/site.static_files/imgsAndPdfs--dateInPath--newFirst--RTNR.md -%}

{%- comment -%}<!-- IMPORT sortedImgAndPdfArr, extList, dateStrArr_SORTED, yrsSortedUniqArr  -->{%- endcomment -%}
{%-  assign yrHdrChkrArr   = yrHdrChkrArr   | split:"" -%}
{%-  assign strnHdrChkrArr = strnHdrChkrArr | split:"" -%}
{%- for CERT in sortedImgAndPdfArr -%}
   {%- assign trmdPath    = CERT.path | remove:page.fetch_path | replace: "//","/" -%}
   {%- assign trmdPathArrSlc0 = trmdPath | slice:0 -%}
   {%- if trmdPathArrSlc0 == "/" -%}
      {%- assign trmdPath = trmdPath | remove_first: "/" -%}
   {%- endif -%}
   {%- assign trmdPathArr = trmdPath | split:"/" -%}
   {%- assign yrStr       = trmdPathArr[0] | truncate: 4,"" -%}
   {%- assign dateStr     = trmdPathArr[0] -%}
   {%- assign strnStr     = trmdPathArr[1] -%}
   {%- assign nameStr     = trmdPathArr[2] -%}

   {%- assign lookAheadPath     = sortedImgAndPdfArr[forloop.index].path -%}
   {%- assign lookAheadPathTrmd = lookAheadPath | remove:page.fetch_path | remove: "/" -%}
   {%- assign lookAheadYrStr    = lookAheadPathTrmd | truncate: 4,"" -%}
   {%- assign closePrvYrCont    = null -%}
   {%- if lookAheadYrStr < yrStr -%}
     {%- assign closePrvYrCont = "closeNow" -%}
   {%- endif -%}

  {%- assign makeYrHdr = false -%}
  {%- unless yrHdrChkrArr contains yrStr -%}
      {%- assign yrHdrChkrArr = yrHdrChkrArr | push:yrStr -%}
    {%- if yrHdrChkrArr.size == 1 -%}
      {%- assign makeYrHdr    = "curYr" -%}
    {%- elsif yrHdrChkrArr.size == 2 -%}
      {%- assign makeYrHdr    = "lastYr" -%}
    {%- else -%}
      {%- assign makeYrHdr    = "prevYrs" -%}
    {%- endif -%}
      {%- assign curHdrInLoop = makeYrHdr -%}
  {%- endunless  -%}

  {%- assign strnHdrChkrStr = "" | append: dateStr | append: "/" | append: strnStr -%}
  {%- assign makeStrHdr = false -%}
  {%- unless strnHdrChkrArr contains strnHdrChkrStr -%}
      {%- assign strnHdrChkrArr = strnHdrChkrArr | push: strnHdrChkrStr -%}
      {%- assign makeStrHdr = strnStr -%}
  {%- endunless  -%}

{%- assign nameStrChkr = nameStr | downcase -%}
{%- assign certType = null -%}
{%- assign certTypCountr = 0 -%}

{%- for crtTyp in page.certTypes -%}
  {% assign certTypTrmd = crtTyp | split:"" | pop:2 | join:"" %}
  {%- if nameStrChkr contains certTypTrmd -%}
   {%- if certTypCountr == 0 -%}
    {%- assign certType = crtTyp -%}
    {%- assign certTypCountr = certTypCountr | plus:1 -%}
   {%- else -%}
    {%- assign certType = certType | append:", " | append: crtTyp -%}
   {%- endif -%}
  {%- endif -%}
{%- endfor -%}

{%- unless certType != null -%}
  {%- assign certType = "Lab Results" -%}
{%- endunless -%}

  {%- if makeYrHdr == curHdrInLoop -%}
   {%- unless    curHdrInLoop == "curYr" -%}
   <hr>
   {%- endunless -%}
   <h1 class="yrHdr">{{yrStr}}</h1>
   {%- endif -%}
   {%- if makeStrHdr -%}
   <div class="wrapStrnHdr">
     <img class="arrow" src="{{ 'assets/svgs/arrow.svg' | relative_url }}">
     <h4  class="strnHdr">{{strnStr | upcase }}</h4>
   </div>
   {%- endif -%}
   <p class="strnTxt"><span class="strnSpan">{{certType | upcase}}</span><a href="{{CERT.path}}" class="pdfLink" target="_blank"><i>(LINK TO PDF)</i></a>
   </p>
{%- endfor -%}
</div>
