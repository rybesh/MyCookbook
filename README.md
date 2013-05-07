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
all-recipes.ejs, all-cooks.ejs, one-recipe.ejs, and one-cook.ejs.
   
Root: 
* www.mycookbook.com/ - home page, with links to view all recipes by meal, name, dish type; plus search function

Resources:
* www.mycookbook.com/recipes/ - contains all the recipes, listed alphebetically; recipe link will GET:
* www.mycookbook.com/recipes/{recipe name}/{ID - optional} - original URI for a recipe
       EX. www.mycookbook.com/recipes/blueberry-pancakes/1

* www.mycookbook.com/cooks/ - contains all the cooks, listed alphabetically; cook link will GET:
* www.mycookbook.com/cooks/{name of cook} - profile page for cook; links to their posted recipes will be listed here
       EX. www.mycookbook.com/cooks/jane-doe

* www.mycookbook.com/{category} - lists all the subtypes in the selected category; subtype link will GET:
* www.mycookbook.com/{category}/{subtype} - lists all the recipes that are classified under subtype
       EX. www.mycookbook.com/meal/breakfast
       Recipe link here will GET: www.mycookbook.com/recipes/{recipe name}

* www.mycookbook.com/recipes/q={search term 1}+{search term 2} - lists all recipes that match the search terms
       EX. www.mycookbook.com/recipes/q=cream+cheese 
OR
* www.mycookbook.com/q={search term 1}+{search term 2} - lists all recipes that match the search terms


Recipes to use for this project:


Subtypes of Meal to use for this project:
* www.mycookbook.com/meal/dessert  (all desserts)
* www.mycookbook.com/meal/dinner (all dinners)

Subtypes of Dish to use for this project:
* www.mycookbook.com/dish/pasta (all pasta dishes)
* www.mycookbook.com/dish/soup (all soup dishes)

Link to POST a new recipe will be coded into the template so it shows up on every page. Th action will POST to www.mycookbook.com/recipes. The search function will also be coded into the template.

Attributes:
-----------
###Class Attributes
###Name Attributes
###Rel Attributes:

Metadata:
---------
The schema.org 'recipe' schema (http://schema.org/Recipe)  was used to embed microdata into the recipe templates.
