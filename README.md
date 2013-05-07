MyCookbook
==========

Description of service:
My Cookbook is a data service will allow individuals interested in cooking and baking to post their own recipes online 
or search other cooks' recipes. Users can add new cook profiles and add recipes for each cook. Information used to
describe the cooks includes the cook name and a description of the cook. When creating a new recipe, information about 
recipes such as: time to prepare, name of recipe, and dish type will be entered using the add or update recipe form.

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


Part IV:
To create a bucket I would use the ÒPOSTÓ method. For example if I wanted to create a resource for a new recipe called Òblueberry pancakes,Ó IÕd type: POST www.yummyfood.com/h to create that new resource. If I wanted to update blueberry pancakes, IÕd need to use PUT to send a new representation to the URI. Suppose, I wanted to update the cook time, I would PUT the entire new recipe including the new cook time. I could also use PATCH to just change cook time. If I were to want to look at the blueberry pancake recipe, then IÕd use the http method GET to retrieve the representation. If I decided that I no longer liked the blueberry pancake recipe, IÕd use DELETE to delete it from my recipes buckets. If I were to just want to retrieve the header metadata about this representation (content type, server, content location, etc.), I would use the HEAD method.

Root would support: POST, GET, PATCH, PUT, DELETE and HEAD. I can create a new bucket (POST(), I can get the data for this representation (GET), I could change this representation (PATCH/PUT), I could retrieve the header metadata (HEAD), and delete this representation (DELETE).

With the buckets: /(bucket letter), I could perform all the methods mentions above but POST because I cannot create a new bucket from this bucket. Buckets would be created at the root level. 

Buckets grouped by meal or diet type (/(meal)) would be primarily using the GET method of retrieving the representations that fit the search criteria. I would be able DELETE and then POST/PUT to change these categories. If I wanted to modify the recipes included in these groups, I would have to go to the individual bucket level and modify each recipe through PATCH or PUT.

The buckets identified through search (/search?q=(term)), would primarily use the GET method and possibly DELETE, but delete probably would not be used often unless to save space. In an ideal search situation these URIs could be created automatically when someone enters a search term at the root level.

Part V:
Resources and Representations
Root: in the HTML/text format, URI: www.yummyfood.com
Recipe Buckets: would be in HTML/text format, URI: www.yummyfood.com/(id), would have <title>, <author>, <ingredients>, <time>, <servings>, <instructions>
Meal Groups: would be in HTML/text format, URI: www.yummyfood.com/(meal), each group would be represented by an index or recipe titles and author that the user could see and use to select. Clicking on a recipe title, would lead the user to the recipeÕs URI (see above).
Keyword Search Results: would be HTML/text format, URI: www.yummyfood.com/search/q=(term a)+(term b), would also be represented by an index of titles and author that the user could see and use to select a recipe to view. 

Root would be represented in HTML and text and would have the location of www.yummyfood.com. If the root page were down, the client could receive a 404 not found error when using the GET method. When the root was first created, the creator would receive a 201 created message. To create the root page, the POST method would be used. 

When a recipe bucket is added the creator would get a 201 created message. In order to add a recipe, the POST method would need to be used A user trying to download the recipe could possibly get a 206 partial content message if the page froze in the middle of loading. If the user were to try to GET a recipe that had been deleted, he or she might receive a 404 not found or a 410 gone message. If the administrator were to successfully delete a recipe using the DELETE method, he or she would get the 200 OK message if he or she were to try to delete the recipe again. If a non-administrator were to try to delete a recipe, he or she would receive the 403 forbidden message. If an admin or user were to try to use the OPTIONS method, he or she would receive the 405 method not allowed message. To update the recipes the PATCH or PUT method would need to be used. If the PATCH or PUT was successful a 200 OK method would be sent to the client. If the PATCH or PUT was unsuccessful due to something on the server side, a 500 Internal Server Error. 

The Meal Groups representation would have similar methods and errors to recipe buckets. 

The Keyword Search representation would primarily rely on the GET method which could result in a 404 not found error or 400 bad request error. 
