---
layout: default
title: Recipes
---
# Recipes

<div style="margin-bottom: 30px;">
  <input type="text" id="recipe-search" placeholder="使用食譜名搜尋 Search recipes by title..." 
         style="width: 100%; padding: 12px; font-size: 16px; border: 1px solid #ddd; border-radius: 4px;">
</div>

<div id="recipes-container">
{% assign sorted_recipes = site.recipes | sort: "date" | reverse %}
{% for item in sorted_recipes %}
  <div class="recipe-item" style="margin-bottom: 40px;">
    <h2><a href="{{ item.url }}">{{ item.title }}</a></h2>
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
    
    // Stores the list of items that match the current search query
    let filteredItems = allItems;

    /**
     * Updates the visible items based on the current page
     * @param {number} p - The page number to display
     */
    function updateDisplay(p) {
        // First, hide all items to reset the view
        allItems.forEach(item => item.style.display = 'none');
        
        // Calculate the slice of filtered items for the current page
        const start = (p - 1) * itemsPerPage;
        const end = start + itemsPerPage;
        const pageItems = filteredItems.slice(start, end);
        
        // Show only the items belonging to this page
        pageItems.forEach(item => item.style.display = 'block');
        
        renderButtons(p);
    }

    /**
     * Generates pagination buttons based on the number of filtered items
     * @param {number} activePage - The currently active page
     */
    function renderButtons(activePage) {
        const totalPages = Math.ceil(filteredItems.length / itemsPerPage);
        nav.innerHTML = '';

        // Do not render buttons if there is only one page or no results
        if (totalPages <= 1) return;

        for (let i = 1; i <= totalPages; i++) {
            let btn = document.createElement('button');
            btn.innerHTML = i;
            // Inline styling to maintain visual consistency with your site
            btn.style.cssText = "margin: 0 5px; padding: 5px 10px; cursor: pointer; border: 1px solid #ddd;";
            btn.style.backgroundColor = (i === activePage) ? "#333" : "#fff";
            btn.style.color = (i === activePage) ? "#fff" : "#333";
            
            btn.onclick = () => { 
                updateDisplay(i); 
                window.scrollTo(0, 0); // Scroll back to top after page switch
            };
            nav.appendChild(btn);
        }
    }

    // Event listener for the search input
    searchInput.addEventListener('input', function(e) {
        const query = e.target.value.toLowerCase();
        
        // Filter items where the title includes the search query
        filteredItems = allItems.filter(item => {
            const title = item.querySelector('h2').innerText.toLowerCase();
            return title.includes(query);
        });

        // Always reset to the first page after a new search
        updateDisplay(1); 
    });

    // Initial load: show page 1 on site entry
    updateDisplay(1);
});
</script>