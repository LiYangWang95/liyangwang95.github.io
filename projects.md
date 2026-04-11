---
layout: default
title: Projects
---
# Projects

<div id="projects-container">
{% assign sorted_projects = site.projects | sort: "date" | reverse %}
{% for project in sorted_projects %}
  <div class="project-item" style="margin-bottom: 40px;">
    <h2><a href="{{ project.url }}">{{ project.project_title }}</a></h2>
    <div class="projectBox">
      <table>
        <tr>
          <th class="imageColumn"><img src="{{ project.project_image }}" class="projectImg"></th>
          <th class="textColumn">{{ project.description }}</th>
        </tr>
      </table>
    </div>
  </div>
{% endfor %}
</div>

<div id="project-pagination" style="text-align: center; margin-top: 20px;"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const itemsPerPage = 5;
    const items = document.querySelectorAll('.project-item');
    const totalPages = Math.ceil(items.length / itemsPerPage);
    const nav = document.getElementById('project-pagination');

    function showPage(p) {
        items.forEach((item, i) => {
            item.style.display = (i >= (p-1)*itemsPerPage && i < p*itemsPerPage) ? 'block' : 'none';
        });
        renderButtons(p);
    }

    function renderButtons(activePage) {
        if (totalPages <= 1) return;
        nav.innerHTML = '';
        for (let i = 1; i <= totalPages; i++) {
            let btn = document.createElement('button');
            btn.innerHTML = i;
            btn.style.cssText = "margin: 0 5px; padding: 5px 10px; cursor: pointer; border: 1px solid #ddd; background: " + (i === activePage ? "#333" : "#fff") + "; color: " + (i === activePage ? "#fff" : "#333") + ";";
            btn.onclick = () => { showPage(i); window.scrollTo(0,0); };
            nav.appendChild(btn);
        }
    }
    showPage(1);
});
</script>