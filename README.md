# whatnow

## Angular
### The Service Recipe
--- root.js<br>
<pre>angular.module("root", ["services"])
	.controller("index", ["$scope", "multiplier",
		function ($scope, multiplier) {
			$scope.product = multiplier.multiply(2);
		}]);</pre>
		
--- services.js<br>
<pre>angular.module("services", [])
	.value("factor", 6)
	.service("multiplier", ["factor", Multiplier]);</pre>
	
--- multiplier.js<br>
<pre>function Multiplier(valueFactor) {
	this.multiply = function (controllerFactor) {
		return valueFactor * controllerFactor;
	};
}</pre>
