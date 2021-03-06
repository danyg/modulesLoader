modulesLoader
=============

Require JS Plugin, for do hMVC

#Use

The idea of this component is to do hMVC (Hierarchical Model View Controller) pattern with some additions.
Principally thinked for use with knockout and/or backbone, but now is adapted for Durandal. But can be used
alone.

## You need to follow this directory struture

- **${baseUrl}**/modules
	- **${ModuleName}**
		- controllers
			- **${ModuleName}**.js ```Principal file to be loaded when you require module!${ModuleName}```
		- models ```optional you can reach the files inside here using model!${fileName} see #Important```
			- **${fileName}**.js
		- helpers ```optional you can reach the files inside here using helper!${fileName} see Important```
			- **${fileName}**.js
		- views ```optional you can reach the files inside here using view!${fileName} see #Important```
			- **${fileName}**.js
		- templates ```optional you can reach the files inside here using template!${fileNameWext} see #Important```
			- **${fileName}**.html
		- widget ```optional you can reach the files inside here using widget!${widgetName} see #Important```
			- **${WidgetName}**.js
			- **${WidgetName}**.html ```widget!**${widgetName}**.html in progress```

### The basic structure is this
- Module (Hierarchical)
	- Controllers
	- Views			(Classes opr Objects)
	- Models
	- Helpers
	- Templates		(html things)
	- Widgets		(Durandal Aproach)

### Important
Everything is private by design.
_The idea is think in little applications communicated by APIs, defined on the Controllers_
- Private things
  - models
  - views
  - helpers
  - templates
  - widgets

## Examples

You can find better examples on the unit tests
/tests/mocks/modules

```javascript

define(['module!Employees'], function(Employees){

	// ...
	
	Employees.getItems();

});

// **${baseUrl}**/modules/Employees/controllers/Employees.js

define(['model!employees', 'model!companies'], function(employeesModel, companiesModel){

	return {
	
		getItems: function(){
			var items = employeesModel.getAll(),
				companies = companiesModel.getAll(),
				i
			;
			for(i = 0; i ${ items.length; i++){
				// put companies inside items
			}
			
			return items;
		}
	}

});

// The models are Privates elements, only can be reached by the module Employees
// **${baseUrl}**/modules/Employees/models/employees.js
// **${baseUrl}**/modules/Employees/models/companies.js
```

# How to run the tests

To run the tests you need npm in your system (part of nodejs).

- ```git clone https://github.com/danyg/modulesLoader.git```
- ```cd modulesLoader```
- ```npm install```
- ```npm test```

in this moment a nodewebkit application appears with jasmine for run the tests.

The tests specs are defined on /tests/specs/

Every file that is contained on that folder will be loaded as a spec definition. (May be you need to restart the application to see the additon).

[![Analytics](https://ga-beacon.appspot.com/UA-47717226-1/modulesLoader/home)](https://github.com/igrigorik/ga-beacon)
