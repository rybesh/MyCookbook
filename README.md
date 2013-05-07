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

The recipe schema was used in the one-recipe.ejs temple as follows:

    <dl>
      <div itemscope itemtype="http://schema.org/Recipe">
      <dt><span itemprop="name">Recipe Name</span></dt>
      <dd><%=item.name%></dd>
      <dt>Cook</dt>
      <dd><span itemprop="author"><a href="/cooks/<%=item.cook%>"><%=item.cook%></a></span></dd>
      <% if (item.image) { %>
      <dt>Image URL</dt>
      <dd><img itemprop="image" src="<%=item.image%>" alt="<%=item.image%>"></dd>
      <% } %>
      <dt>Cook Time</dt>
      <dd><span itemprop="cookTime"><%=item.cooktime%></span></dd>
      <dt>Meal Type: </dt><dd><span itemprop="recipeCategory"><%=item.meals%></span></dd>
      <dt>Cuisine: </dt><dd><span itemprop="recipeCuisine"><%=item.dish%></span></dd>
      <dt><span itemprop="ingredients">Ingredients</span></dt>
      <dd><%=item.ingredients%></dd>
      <dt>Directions</dt>
      <dd><span itemprop="recipeInstructions"><%=item.directions%></span></dd>
      </div>
    </dl>
    
The schema.org framework uses the following attributes:
+ itemscope - indicates a new item
+ itemtype - specifies the type
+ itemprop - specifies the properties and values


The schema was referenced using 'itemscope' to indicate that a schema was going to be used and 'itemtype' was used to specify, by referencing the schema.org recipe URL, that the recipe schema was going to be used.

Then itemprop was used to add the following recipe properties:
+ name - 'the name of the item,' which in this case is the name of the recipe.
+ author - 'the author of this content,' which in this case is the cook.
+ image - 'URL of of an image of the item,' which in this case is the picture of the recipe.
+ cookTime - 'The time it takes to actually cook the dish, in ISO 8601 duration format,' which fits well with our recipe data.
+ recipeCategory - 'The category of the recipe—for example, appetizer, entree, etc.,' another piece of data we wanted to capture in our service.
+ recipeCuisine - 'The cuisine of the recipe (for example, French or Ethopian),' which we instead used to describe the type of dish (cakes, breads, ets.)
+ ingredients - 'An ingredient used in the recipe,' another essential piece of information about the recipes.
= recipeInstructions  - 'The steps to make the dish,' which we referred to as "directions" in our service. 
