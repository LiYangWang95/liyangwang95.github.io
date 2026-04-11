---
layout: default
title: Recipes
---
# Recipes

{% for item in paginator.documents %}
  <div class="projectBox" style="margin-bottom: 40px;">
    <h2><a href="{{ item.url }}">{{ item.recipe_title }}</a></h2>
    <table>
      <tr>
        <th class="imageColumn"><img src="{{ item.recipe_image }}" class="recipeImg"></th>
        <th class="textColumn">{{ item.description }}</th>
      </tr>
    </table>
  </div>
{% endfor %}

<div class="pagination" style="text-align: center; margin-top: 30px;">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}" style="padding: 8px 12px; border: 1px solid #ddd;">&laquo; Prev</a>
  {% endif %}
  <span style="margin: 0 15px;">Page {{ paginator.page }} of {{ paginator.total_pages }}</span>
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}" style="padding: 8px 12px; border: 1px solid #ddd;">Next &raquo;</a>
  {% endif %}
</div>