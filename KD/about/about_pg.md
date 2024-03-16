---
layout:    BASE
permalink: about
title:    "About Edward's Farms"
navLinks:
   #- "age verif": "/"
   - about: "#"
   - "certificates of analysis": "certificates"
   - contact: "contact"
fetch_path: "/KD/about/2022_zebsPics/"
###
about_img: "KD/about/2022_paraPics/sunny_spray_SML.jpg"
about_hdr: Vermont Sun Grown
about_sub: No pesticides or inorganic fertilizers, just labor & love.
about_txt:
   - "We do this for the love. We do this for cannabis history and culture. At Edward's our plants are grown from seed under the open sun, the way nature intended. Proudly grown on the same hill in the Green Mountains I was raised on. For this, we give thanks."
   - "With Love, Edward's."
---

<style type="text/css">
  .aboutWrap img{
    float: left;
    margin: 4px 8px 0px 0px;
    /*margin-bottom: 30px;*/
  }
  .aboutWrap p{
    margin: 0px 0px 8px 0px;
    padding: 0px;
    line-height: 1.35rem;
  }
  .aboutWrap p:last-child {
    margin: 0px;
  }
  .aboutWrap h3 {
    margin-bottom: 0px;
    padding-bottom: 0px;
    font-size: 1.5rem;
  }
  hr{
    margin: .25rem;
  }
  .aboutWrap.hdr,.aboutWrap.sub {
    margin-bottom: 0px;
    padding-bottom: 0px;
    text-align: left;
    line-height: 1rem;
  }
  .topWrap{
    height: 100%;
    min-height: 260px;
  }

  .carouselWrap{
    height: 100%;
    margin-top: 50px;
  }
</style>

{% include fetchers/site.static_files/imgsAndPdfs--extFromFileOrDir--RTNR.md %}

<div class="topWrap">
  <div class="aboutWrap hdr">
    <h3> {{ page.about_hdr }}</h3>
  </div>
  <div class="aboutWrap sub">
    <!-- <h5> {{ page.about_sub }}</h5> -->
    <hr>
  </div>
  <div class="aboutWrap">
    <img class src="{{ page.about_img | relative_url }}" alt="Keith picks flower" width="300" height="">
    {% for para in page.about_txt %}
     <p>{{ para }}</p>
    {% endfor %}
  </div>
</div>

<div class="carouselWrap">
  <div id="caroIndic" class="carousel slide">
   <div class="carousel-indicators">
 {% for IMG in sortedImgAndPdfArr %}
   {% assign slideIdxr = forloop.index %}
   {% assign indicIdxr = slideIdxr | minus:1 %}
   {% if forloop.index == 1 %}
     <button type="button" data-bs-target="#caroIndic" data-bs-slide-to="{{indicIdxr}}" class="active" aria-current="true" aria-label="Slide {{slideIdxr}}"></button>
   {% else %}
     <button type="button" data-bs-target="#caroIndic" data-bs-slide-to="{{indicIdxr}}" aria-label="Slide {{slideIdxr}}"></button>
   {% endif %}
 {% endfor %}
   </div>
   <div class="carousel-inner">
 {% for IMG in sortedImgAndPdfArr %}
   {% if forloop.index == 1 %}
     <div class="carousel-item active">
       <img src="{{IMG.path | relative_url}}" class="d-block w-100" alt="ERROR fecthing img @ {{IMG.path}}">
     </div>
   {% else %}
     <div class="carousel-item">
       <img src="{{IMG.path | relative_url}}" class="d-block w-100" alt="ERROR fecthing img @ {{IMG.path}}">
     </div>
   {% endif %}
 {% endfor %}
   </div>
   <button class="carousel-control-prev" type="button" data-bs-target="#caroIndic" data-bs-slide="prev">
     <span class="carousel-control-prev-icon" aria-hidden="true"></span>
     <span class="visually-hidden">Previous</span>
   </button>
   <button class="carousel-control-next" type="button" data-bs-target="#caroIndic" data-bs-slide="next">
     <span class="carousel-control-next-icon" aria-hidden="true"></span>
     <span class="visually-hidden">Next</span>
   </button>
  </div>
</div>
