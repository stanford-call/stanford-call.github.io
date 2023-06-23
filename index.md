---
title: Stanford Compilers and Languages Lab (CaLL)
layout: home
---

<img src="/assets/call_group.png" width="100%">

<h2 class="tableheading">Members</h2>

<ul>
  <li><a href="https://fredrikbk.com">Fredrik Kjolstad</a> (PI)</li>
  <li>James Dong (PhD)</li>
  <li><a href="https://weiya711.github.io/">Olivia Hsu</a> (PhD)</li>
  <li><a href="https://www.linkedin.com/in/praneeth-kolichala-ba4a73165/">Praneeth Kolichala</a> (UG/MS)</li>
  <li>Scott Kovach (PhD)</li>
  <li><a href="https://www.linkedin.com/in/lrubens">Rubens Lacouture</a> (PhD)</li>
  <li><a href="https://rootjalex.github.io/">Alexander Root</a> (PhD)</li>
  <li><a href="https://shivsundram.github.io/">Shiv Sundram</a> (PhD)</li>
  <li><a href="https://sillycross.github.io/about/">Haoran Xu</a> (PhD)</li>
  <li><a href="https://rohany.github.io/">Rohan Yadav</a> (PhD)</li>
  <li><a href="https://bobbyy.org/">Bobby Yan</a> (PhD)</li>
</ul>

<h2 class="tableheading">Alumni</h2>

<ul>
  <li><a href="https://manya-bansal.github.io">Manya Bansal</a> (UG)</li>
  <li><a href="https://www.linkedin.com/in/timothygu/">Timothy Gu</a> (MS)</li>
</ul>

<h2 class="tableheading">Publications</h2>

<table border="0">
  {% for pub_keyval in site.data.publications %}
    <tr>
      {%- assign pub = pub_keyval[1] -%}
      <td>
        <b><a href="{{pub_keyval[0]}}.html" style="color: #464646">{{ pub.title }}</a></b><br/>
        {%- for author in pub.authors -%}
          {%- if forloop.last == true and forloop.length > 1 %}
            and
          {%- endif %}
          <a href="{{- site.data.authors[author].site -}}" style="color: #464646">{{ site.data.authors[author].name }}</a>
          {%- if forloop.last == false and forloop.length > 2 -%}
            ,
          {%- endif %}
        {%- endfor -%}<br/>
        <i>{{ pub.venue }}
        {%- if pub.venuenote %}
        ({{ pub.venuenote }})
        {%- endif -%}
        {%- if pub.volume -%}
        , Volume {{ pub.volume }}
        {%- endif -%}
        {%- if pub.issue -%}
        , Issue {{ pub.issue }}
        {%- endif -%}
        </i>, {{ pub.month }} {{ pub.year }}<br/>
        {%- if pub.award -%}
          <span style="color:#0096FF"><b>{{ pub.award }}</b></span><br/>
        {%- endif -%}
      </td>
      <td valign="top" width="20">
        {% if pub.pdf %}
            <a href="{{ pub.pdf }}"><img src="/assets/pdf.png" alt="pdf" /></a>
	{% elsif pub.url %}
            <a href="{{ pub.url }}"><img src="/assets/pdf.png" alt="pdf" /></a>
        {% endif %}
        {% if pub.movie %}
          <a href="{{ pub.movie }}"><img src="/assets/movie.png" alt="youtube" /></a>
        {% endif %}
      </td>
    </tr>
{% endfor %}
</table>

<script>
const desiredRepo = "stanford-call.github.io"
const monthNames = ["January", "February", "March", "April", "May", "June",
  "July", "August", "September", "October", "November", "December"
];

var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    let repos = JSON.parse(this.responseText);
    repos.forEach((repo)=>{
      if (repo.name == desiredRepo)
      {
        var lastUpdated = new Date(repo.pushed_at);
        var day = lastUpdated.getUTCDate();
        var month = lastUpdated.getUTCMonth();
        var year = lastUpdated.getUTCFullYear();
        siteUpdate.innerHTML += (`<em>Site Last Updated ${monthNames[month]} ${year}</em><br>`);
      }
    });
  }
};
xhttp.open("GET", "https://api.github.com/users/stanford-call/repos", true);
xhttp.send();
</script>