# bpm'online sublime text snippets

## Entity schema queries
### select
```
var selectContact = Ext.create("Terrasoft.EntitySchemaQuery", {
	rootSchemaName: "Contact"
});
selectContact.addMacrosColumn(Terrasoft.QueryMacrosType.PRIMARY_COLUMN, "Id");
selectContact.addMacrosColumn(Terrasoft.QueryMacrosType.PRIMARY_DISPLAY_COLUMN, "Name");
selectContact.getEntityCollection(function(response) {
	if (response.success === true) {
		
	}
}, this);
```
### update
```
var updateContact = Ext.create("Terrasoft.UpdateQuery", {
	rootSchemaName: "Contact"
});
// TODO Add filters here
updateContact.setParameterValue("Column", "NewValue", Terrasoft.DataValueType.TEXT);
updateContact.execute(function(response) {
	if (response.success === true) {
		
	}
}, this);
```
### delete
```
var deleteContact = Ext.create("Terrasoft.DeleteQuery", {
	rootSchemaName: "Contact"
});
// TODO Add filters here
deleteContact.execute(function (result) {
	if (result.success) {
		
	}
}, this);
```
### filter
```
esq.filters.add(esq.createColumnFilterWithParameter(
	Terrasoft.ComparisonType.EQUAL,
	"Column",
	Value));
```
## Viewmodel helpers
### schema
```
define("ContactPage", ["ContactPageResources"], function(resources) {
	return {
		attributes: {},
		messages: {},
		methods: {},
		rules: {},
		diff: /**SCHEMA_DIFF*/ [
		] /**SCHEMA_DIFF*/
	};
});
```
### viewmodel
```
define("ViewModel", ["ViewModelResources"],
	function(resources) {
		/**
		 * @class Terrasoft.model.ViewModel
		 * Description.
		 */
		Ext.define("Terrasoft.model.ViewModel", {
			extend: "Terrasoft.BaseModel",
			alternateClassName: "Terrasoft.ViewModel",

			Ext: null,

			Terrasoft: null,

			mixins: {},

			columns: {}

			//region Methods: Protected

			//endregion
		});
		return Terrasoft.ViewModel;
	});
```
### asyncvalidate
```
/**
 * @inheritdoc Terrasoft.BasePageV2#asyncValidate
 * @protected
 * @overridden
 */
asyncValidate: function(callback, scope) {
	this.callParent([function(response) {
		if (!this.validateResponse(response)) {
			return;
		}
		// your methods here
		callback.call(scope, response);
	}, this]);
}
```
### set
```
this.set("Attribute", Value);
```
### get
```
this.get("Attribute");
```
## Test helpers
### testmodule
```
define("Module_Package_Tests", ["sandbox", "SchemaTestsHelper"],
	function() {
	startTest(function(test) {

		test.setUp = function() {
		};

		test.tearDown = function() {
		};

		//Test methods

	});

	return {};
});
```
### testschema
```
define("Schema_Package_Tests", ["SchemaTestsHelper"], function() {
	var buildConfig = {
		schemaName: "Schema"
	};
	Terrasoft.SchemaTestsHelper.initTestsSchema(buildConfig, function(viewModelClass, viewConfig, schema) {
		startTest(function(test) {
			test.setUp = function() {
				var testData = test.data;
				testData.schema = schema;
				testData.viewConfig = viewConfig;
				testData.viewModel =
					Terrasoft.SchemaTestsHelper.createSchemaViewModel(viewModelClass);
			};

			test.tearDown = function() {
				var testData = test.data;
				testData.viewModel.destroy();
				delete testData.viewModel;
				Terrasoft.SchemaTestsHelper.clearAllHandlers();
			};

			//Test methods

		});
	}, this);
	return {};
});
```
### testmethod
```
test.diag("someFunction");

test.testMethod({
	name: "someFunction - if called",
	setup: function() {
	},
	method: function() {
		var testName = this.name;
		var testData = test.data;
		//place some test code here
		test.testMethodDone();
	},
	tearDown: function() {
	}
});
```
