# Introduction

*Duration is 15 min* *<div style="text-align: right">Last Updated: 13/01/2020</div>*

This timezone tutorial shows the current time, timezone in leaflet using HERE maps.Click on each country to display the results.

# What We Will Be Making {#making}

We create a  map to display the timezones. 

# Prerequisites {#prerequisites}

* Knowledge on the JavaScript/HTML
* HERE Developer account [developer.here.com](https://developer.here.com/sign-up?create=Freemium-Basic&keepState=true&step=account)

# Display timezone using HERE maps with leaflet  {#display-timezone-using-HERE-maps-with-leaflet}

Add the following to `<head>` section of the `index.html`
```html
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.2.0/dist/leaflet.css"
		integrity="sha512-M2wvCLH6DSRazYeZRIm1JnYyh22purTM+FDB5CsyxtQJYeKq83arPe5wgbNmcFXGqiSH2XR8dT/fJISVA1r/zQ=="
		crossorigin="" />
	<script src="https://unpkg.com/leaflet@1.2.0/dist/leaflet.js"
		integrity="sha512-lInM/apFSqyy1o6s89K4iQUKg6ppXEgsVxT35HbzUupEVRh2Eu9Wdl4tHj7dZO0s1uvplcYGmt3498TtHq+log=="
		crossorigin=""></script>
	<script src="timezones.js"></script> <!-- plugin -->

```

# Creating a timezone map using leaflet and here api {#creating-a-timezone-map-using-leaflet-and-here-apsi }

```html
Paste the below code in body of the index.html page

<div id="mapid"></div>
	<script>
        var mymap = L.map('mapid').setView([51.505, -0.09], 2.5);  //13
        L.tileLayer('https://1.base.maps.ls.hereapi.com/maptile/2.1/maptile/newest/reduced.day/{z}/{x}/{y}/512/png8?apiKey={YOUR_API_KEY}', {
            maxZoom: 10
        }).addTo(mymap);
        L.timezones.bindPopup(function (layer) {
            console.log({ layer });
            let time_zone = new Date().toLocaleString("en-GB", { timeZone: layer.feature.properties.tz_name1st, timeZoneName: "short" });
            let time_zone_name = layer.feature.properties.tz_name1st
            return `TimeZoneName: ${time_zone_name} </br> Data&LocalTime: ${time_zone}`;   //.time_zone
        }).addTo(mymap);

	</script>


```

