# whatnow

## Angular
### The Service Recipe
--- root.js
angular.module("root", ["services"])
	.controller("index", ["$scope", "multiplier",
		function ($scope, multiplier) {
			$scope.product = multiplier.multiply(2);
		}]);
--- services.js
angular.module("services", [])
	.value("factor", 6)
	.service("multiplier", ["factor", Multiplier]);
--- multiplier.js
function Multiplier(valueFactor) {
	this.multiply = function (controllerFactor) {
		return valueFactor * controllerFactor;
	};
}
