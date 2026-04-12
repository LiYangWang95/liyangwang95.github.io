---
layout: default
title: Recipes
---
# Recipes

<div style="margin-bottom: 30px;">
  <input type="text" id="recipe-search" placeholder="使用食譜名/食材搜尋 Search by title or ingredients (e.g., pork, egg, potato)..." 
         style="width: 100%; padding: 12px; font-size: 16px; border: 1px solid #ddd; border-radius: 4px;">
</div>

<div id="recipes-container">
{% assign sorted_recipes = site.recipes | sort: "date" | reverse %}
  {% for item in sorted_recipes %}
    <div class="recipe-item" 
      data-title="{{ item.recipe_title | downcase }}"
      data-ingredients="{% if item.content contains '[//]: # (start_ingredients)' %}{{ item.content | split: '[//]: # (start_ingredients)' | last | split: '[//]: # (end_ingredients)' | first | strip_html | strip_newlines | downcase }}{% endif %}"
      style="margin-bottom: 40px;">
      <h2><a href="{{ item.url }}">{{ item.recipe_title }}</a></h2>
      <div class="projectBox">
        <table>
          <tr>
            <th class="imageColumn">
              <img src="{{ item.recipe_image }}" class="recipeImg">
            </th>
            <th class="textColumn">
              {{ item.description }}
            </th>
          </tr>
        </table>
      </div>
    </div>
  {% endfor %}
</div>

<div id="recipe-pagination" style="text-align: center; margin-top: 20px;"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    const searchInput = document.getElementById('recipe-search');
    const allItems = Array.from(document.querySelectorAll('.recipe-item'));
    const itemsPerPage = 5;
    const nav = document.getElementById('recipe-pagination');
    
    let filteredItems = allItems;

    function updateDisplay(p) {
        // Hide all items first
        allItems.forEach(item => item.style.display = 'none');
        
        // Calculate the slice for the current page
        const start = (p - 1) * itemsPerPage;
        const end = start + itemsPerPage;
        const pageItems = filteredItems.slice(start, end);
        
        // Show filtered items
        pageItems.forEach(item => item.style.display = 'block');
        
        renderButtons(p);
    }

    function renderButtons(activePage) {
        const totalPages = Math.ceil(filteredItems.length / itemsPerPage);
        nav.innerHTML = '';

        if (totalPages <= 1) return;

        for (let i = 1; i <= totalPages; i++) {
            let btn = document.createElement('button');
            btn.innerHTML = i;
            btn.style.cssText = "margin: 0 5px; padding: 5px 10px; cursor: pointer; border: 1px solid #ddd;";
            btn.style.backgroundColor = (i === activePage) ? "#333" : "#fff";
            btn.style.color = (i === activePage) ? "#fff" : "#333";
            
            btn.onclick = () => { 
                updateDisplay(i); 
                window.scrollTo(0, 0); 
            };
            nav.appendChild(btn);
        }
    }

    // Search logic: multi-keyword search (AND Logic)
    searchInput.addEventListener('input', function(e) {
        // Split search string into array
        const query = e.target.value.toLowerCase().trim();
        const keywords = query.split(/[ ,，、;；\s]+/).filter(k => k.length > 0);
        
        if (keywords.length === 0) {
            filteredItems = allItems;
        } else {
            filteredItems = allItems.filter(item => {
                const title = item.getAttribute('data-title') || "";
                const ingredients = item.getAttribute('data-ingredients') || "";
                
                // Merge searching text
                const searchableText = title + " " + ingredients;

                // AND search logic
                return keywords.every(kw => searchableText.includes(kw));
            });
        }

        updateDisplay(1); 
    });

    // Run on initial load
    updateDisplay(1);
});
</script>