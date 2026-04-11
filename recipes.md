---
layout: default
title: Recipes
---
# Recipes

<div id="recipes-container">
{% assign sorted_recipes = site.recipes | sort: "date" | reverse %}
{% for item in sorted_recipes %}
  <div class="recipe-item" style="margin-bottom: 40px;">
    <h2><a href="{{ item.url }}">{{ item.recipe_title }}</a></h2>
    <div class="projectBox">
      <table>
        <tr>
          <th class="imageColumn"><img src="{{ item.recipe_image }}" class="recipeImg"></th>
          <th class="textColumn">{{ item.description }}</th>
        </tr>
      </table>
    </div>
  </div>
{% endfor %}
</div>

<div id="recipe-pagination" style="text-align: center; margin-top: 20px;"></div>

<script>

document.addEventListener("DOMContentLoaded", function() {
    const itemsPerPage = 5;
    const items = document.querySelectorAll('.recipe-item');
    const totalPages = Math.ceil(items.length / itemsPerPage);
    const nav = document.getElementById('recipe-pagination');

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