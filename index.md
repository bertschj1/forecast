<!DOCTYPE html>
<html>
<head>
	<title>Weather Forecast</title>
	<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>

</head>
<body>
<div id="forecast"></div>
<img id="ForecastIcon" src=""></img>


<script type="text/javascript">
	var available = {
    "url": "https://api.weather.gov/gridpoints/ILN/46,37/forecast",
    "method": "GET",
    } 

    $.ajax(available).done(function (response) {
    console.log(response);

    for (i = 0; i <= 14; i++){
	    var day = response.properties.periods[i].name;
	    var forecast = response.properties.periods[i].detailedForecast;
		var getIcon = response.properties.periods[i].icon;
		
		var img = new Image();   // Create new img element
		img.addEventListener('load', function() {
		  // execute drawImage statements here
		}, false);
		img.src = getIcon; // Set source path



	    $("#forecast").append("<h1>"+day+"<br>").append(img).append("<br>"+forecast+"<hr>");

}});



</script>
</body>
</html>
