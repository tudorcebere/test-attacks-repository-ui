---
layout: main
title: Privacy Attacks Repository
order: 1
class: privacy-attacks
permalink: /privacy-attacks/
---

<div class="home-page privacy-attacks-page">
<div class="main-content" markdown="1">

{% if page.icon %}
    <i class="fa-solid fa-2xl {{ page.icon }} page-icon"></i>
{% endif %}
{% if page.title %}
<header>
    <h1 class="post-title">{{ page.title | escape }}</h1>
</header>
{% endif %}

<button>
    <a download="privacy-attacks.tsv" id="download-tsv">Download TSV</a>
</button>
<script>
</script>
<script type="module" src="{{ '/assets/js/download-tsv.js' | relative_url }}"></script>

<!-- Filters Section -->
<div class="filters-container">
    <div style="white-space: nowrap">Privacy Attacks</div>
    <div class="filter-row" style="justify-content: right">
        <div class="filter-group">
            <input type="text" id="search-filter" placeholder="Search">
        </div>
        <div class="filter-group">
            <select id="visible-filters">
                <option value="">Filters</option>
            </select>
        </div>
        <div class="filter-actions">
            <button id="clear-filters" title="Clear all filters">Clear</button>
        </div>
    </div>
</div>

<div class="filters-container" style="margin-top: 0.5rem">
    <div class="filter-row">
        <div class="filter-group" id="datatype-filter-group" style="display: none;">
            <label for="datatype-filter">Data Type (Inputs):</label>
            <select id="datatype-filter">
                <option value="">All Data Types</option>
            </select>
        </div>
        <div class="filter-group" id="release-filter-group" style="display: none;">
            <label for="release-filter">Type of Data Release (Outputs):</label>
            <select id="release-filter">
                <option value="">All Release Types</option>
            </select>
        </div>
        <div class="filter-group" id="objective-filter-group" style="display: none;">
            <label for="objective-filter">Attacker Objectives:</label>
            <select id="objective-filter">
                <option value="">All Objectives</option>
            </select>
        </div>
        <div class="filter-group" id="researchtype-filter-group" style="display: none;">
            <label for="researchtype-filter">Research Type:</label>
            <select id="researchtype-filter">
                <option value="">All Research Types</option>
            </select>
        </div>
        <div class="filter-group" id="year-filter-group" style="display: none;">
            <label for="year-filter">Year:</label>
            <select id="year-filter">
                <option value="">All Years</option>
            </select>
        </div>
    </div>
</div>

<div class="table-container">
<table id="attacks-table">
    <thead>
        <tr>
            <th style="width: 22%;">Title</th>
            <th style="width: 18%;">Authors</th>
            <th style="width: 6%; min-width: 60px;">Year</th>
            <th style="width: 14%; min-width: 120px">Data Type (Inputs)</th>
            <th style="width: 14%; min-width: 120px">Type of Data Release (Outputs)</th>
            <th style="width: 16%; min-width: 120px">Attacker Objectives</th>
            <th style="width: 8%; min-width: 120px">Research Type</th>
            <th style="width: 2%; min-width: 80px">Links</th>
        </tr>
    </thead>
    <tbody>
    {% for rec in site.data.attacks %}
        {% assign a = rec[1] %}
        <tr class="attack-row" data-index="{{ forloop.index0 }}">
            <td><div style="color: #181818; font-weight: 500; margin-bottom: 4px">{{ a.Title }}</div></td>
            <td>{{ a.Authors }}</td>
            <td>{{ a["Publication Year"] }}</td>
            <td>{{ a["Data Type"] }}</td>
            <td>{{ a["Type of Release"] }}</td>
            <td>{{ a["Threat Model --- Attacker Objective"] }}</td>
            <td>{{ a["Research Type"] }}</td>
            <td>{% if a.URL %}<a href="{{ a.URL }}" target="_blank">Paper</a>{% endif %}</td>
        </tr>
    {% endfor %}
    </tbody>

</table>
</div>

</div>

<div class="side-panel-container">
    <div class="side-panel">
        <div class="side-panel-content" id="attack-details">
        </div>
    </div>
</div>
</div>

<!-- Hidden attack data for JavaScript -->
<script type="application/json" id="attacks-data">
[
{% for rec in site.data.attacks %}
    {% assign a = rec[1] %}
    {{ a | jsonify }}{% unless forloop.last %},{% endunless %}
{% endfor %}
]
</script>
<script>
window.attacks = JSON.parse(document.getElementById('attacks-data').textContent);
</script>

{% include attack-filter-script.html %} 