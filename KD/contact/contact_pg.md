---
layout:    BASE
permalink: contact
title:    "Contact"
navLinks:
   #- "age verif": "/"
   - about: "about"
   - "certificates of analysis": "certificates"
   - contact: "#"
fetch_path: "/KD/contact"
###
edwards:
  "CONTACT US":
    name: "GENERAL INQUIRIES"
    email: "Info@EdwardsFarmVT.com"
vendors:
  "WHERE TO FIND US":
    - name: "GASTON WEED COMPANY"
      website: www.gastonvt.com
    # email:
      phone: "(802) 494-4111"
      address: "100 Center Rd. Essex, Vermont 05452"
    #- name: "DePOT SHOP"
    #  website: www.depotshopvt.com
    #  address: "25 Depot Ave. Windsor, Vermont 05089"
    - name: "GARCIA'S CANNABIS COLLECTIVE"
      website: www.garciascannabis.com
      phone: "(802) 658-5737"
      address: "97 Church St, Burlington, VT 05401"
    - name: "NINNY GOAT & CO"
      website: www.ninnygoat.co
      phone: "(802) 222-6105"
      address: "512 US-5, Fairlee, VT 05045"
    - name: "WINTERLAND HAZE"
      website: www.winterlandhaze.com
      phone: "(802) 613-5031"
      address: "68 Main St, Montpelier, VT 05602"
    - name: "THE TEA HOUSE"
      website: www.teahousevt.com
      phone: "(802) 332-6043"
      address: "50 Woodstock Rd. White River Junction, Vermont 05001"
insta:
  hdr: "Follow us on Instagram"
  path: inclu_rel/instaWithCptn.md
---

<!-- page.fetch_path -> { page.fetch_path }} -->
<style>
  main a{
    margin: 2px 10px;
  }
  a.www{
  }
  a.eml{
  }
  a.phn{
  }
  a.adr{
    font-weight: 300;
  }
  @media (max-width: 538px) {
  }
  h6{
    border-bottom: solid 1px black;
    margin-top: 20px;
  }
  .contactItm{
    margin: 0px;
  }
  .contactItm.name{
    /*margin-bottom:10px;*/
  }
  .contactItm.last{
    margin-bottom:10px;
  }
</style>

<!-- #### This is {{page.url}} -->

###### {{page.edwards.first.first}}

{% assign edsObj = page.edwards.first[1] %}
<p class="contactItm name">
  {{edsObj.name}}
</p>
<p class="contactItm">
  {% if edsObj.email %}<a class="eml" href="mailto:{{vendr.email}}">{{edsObj.email}}</a>{%endif%}
</p>

###### {{page.vendors.first.first}}
{% for vendr in page.vendors.first[1] %}

{% if vendr.name %}{%endif%}
<p class="contactItm name">
  {{vendr.name }}
</p>
<p class="contactItm">
  {% if vendr.website %}<a class="www" target="_blank" href="https://{{vendr.website}}">{{vendr.website}}</a>{%endif%}
</p>
<p class="contactItm">
  {% if vendr.email   %}<a class="eml" href="mailto:{{vendr.email}}">{{vendr.email}}</a>{%endif%}
  {% if vendr.email and vendr.phone %} / {%endif%}
  {% if vendr.phone   %}<a class="phn" href="tel:{{vendr.phone|remove:' '|remove:'('|remove:')'|remove:'.'|remove:'-'|remove:':'}}">{{vendr.phone}}</a>{%endif%}
</p>
<p class="contactItm last">
  {% if vendr.address %}<a class="adr" target="_blank" href="http://maps.google.com/?q={{vendr.address}}">{{vendr.address}}</a>{%endif%}
</p>
{% endfor %}

<style>
  .instaContr{
    width:  538px;
    height: 100%;
    margin: auto;
    margin-top: 30px;
  }
  @media (max-width: 538px) {
    .instaContr{
      width: 98%;
      /*padding: 0px 10px;*/
      /*margin: auto;*/
    }
  }
</style>

###### {{page.insta.hdr | upcase}}

{% if page.insta.path %}
<div class="instaContr">
  {% include_relative {{page.insta.path}} %}
</div>
{% endif %}
