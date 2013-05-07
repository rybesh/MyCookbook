MyCookbook
==========

Description of service:
-----------------------
My Cookbook is a data service will allow individuals interested in cooking and baking to post their own recipes online 
or search other cooks' recipes. Users can add new cook profiles and add recipes for each cook. Information used to
describe the cooks includes the cook name and a description of the cook. When creating a new recipe, information about 
recipes such as: time to prepare, name of recipe, and dish type will be entered using the add or update recipe form.

Resource Templates:
-------------------
The My Cookbook API is constructed of two resources (cooks and recipes) that are represented by the following templates:
list-recipes.ejs, list-cooks.ejs, one-recipe.ejs, one-cook.ejs and index.ejs.
   
**Splash Page**
``http://inlscookbook.herokuapp.com/`` - takes you to the index.ejs page that prompts the user to enter the site. This page serves as an introduction and entrance to the My Cookbook API. The space page is represented by the index.ejs file.


**Home Page**
``http://inlscookbook.herokuapp.com/recipes/`` - home page, with links to view all recipes by name as well as links
to cooks who have authored the recipes listed on the page. This resource is represented by the list-recipes.ejs file. 
The recipe link will GET ``http://inlscookbook.herokuapp.com/recipes/{recipe name}/{ID - optional}`` and the individual 
cook link will GET ``http://inlscookbook.herokuapp.com/cooks/{name of cook}``. The button to add a new cook or recipe 
will GET ``http:\\inlscookbook.herokuapp.com/cooks``

**Recipe Profile**
``http://inlscookbook.herokuapp.com/recipes/{recipe name}/{ID - optional}`` - original URI for a recipe represented by
the recipe.ejs template.
   EX. ``http://inlscookbook.herokuapp.com/recipes/blueberry-pancakes/1``

**Cooks Index**
``http://inlscookbook.herokuapp.com/cooks/`` - contains all the cooks; cook link will GET: ``http://inlscookbook.herokuapp.com/cooks/{name of cook}``. 
The cooks index is represented by the list-cooks.ejs template.

**Cook Profile**
``http://inlscookbook.herokuapp.com/cooks/{name of cook}`` - is the profile page for cook; links to their posted recipes 
will be listed in the profile. The cook profile is represented by the one-cook.ejs template.
   EX. ``http://inlscookbook.herokuapp.com/cooks/jane-doe``

Metadata:
---------
The schema.org 'recipe' schema (http://schema.org/Recipe)  was used to embed microdata into the recipe templates.
