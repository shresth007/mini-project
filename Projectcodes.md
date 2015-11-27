#Projectcodes
 <!DOCTYPE html> 

<head> 
   <meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
    <style type="text/css">
      html { height: 100% }
      body { height: 100%; margin: 0; padding: 0 }
      #map-canvas { width: 1400px; height: 60% }

    </style>
<style>
body  {
    background-image: url("http://santacruztrail.org/railtrail/wp-content/uploads/2014/11/063-1024x768.jpg");
    background-color: #cccccc;
}
</style>

  <script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=false"></script> 
  <script type="text/javascript">
      var geoResults = {};
      var geocoder;
      var map;
      var searchResults = [];
      function initialize() {
          geocoder = new google.maps.Geocoder();
          var latlng = new google.maps.LatLng(21.7679, 78.8718);
          var myOptions = {
              zoom: 6,
              center: latlng,
          }
          map = new google.maps.Map(document.getElementById("map-canvas"), myOptions);
      }

      function codeAddress(id) {
          var address = document.getElementById(id).value;
          geocoder.geocode({ 'address': address }, function (results, status) {
              if (status == google.maps.GeocoderStatus.OK) {
                  map.setCenter(results[0].geometry.location);
                  var marker = new google.maps.Marker({
                      map: map,
                      position: results[0].geometry.location
                  });

                  searchResults[id] = results[0].geometry.location;

              } else {
                  alert("Geocode was not successful for the following reason: " + status);
              }
          });


      }

       function drawLine() {
              var points = [searchResults.address1, searchResults.address2];
              var polyline = new google.maps.Polyline({
                  path: points,
                  strokeColor: '#ff0000',
                  strokeWeight: 5,
                  strokeOpacity: 0.7,
                  map: map
              });

          }

      function clearDiv1() {
          document.getElementById("address1").value = "";
      }

      function clearDiv2() {
          document.getElementById("address2").value = "";
      }

  </script> 
</head> 
<body onload="initialize()"> 

<h1 style= "color : blue ; font-family : verdana ; text-align : center ; font-size : 160%">Google Maps for Railway Enquiry</h1>

<div> 
  <p style= "color : maroon ; font-size : 100%">Enter Your Source : </p>
  <input id="address1" type="text">
  <button type="button" onclick="codeAddress('address1')">Source</button>
   <button type="button" onclick="clearDiv1()">Clear</button>
  </div> 
  <div> 
  <p style= "color : maroon ; font-size : 100%">Enter Your Destination : </p>
    <input id="address2" type="text""> 
  <button type="button" value="Destination" onclick="codeAddress('address2')">Destination</button>
         <button type="button" onclick="clearDiv2()">Clear</button>
  </div> 
    <div>
       <button type="button" onclick="drawLine()">Search</button>
    </div>

<FORM>
<p style ="color : red ; font-family : verdana ; font-size : 90%">Enter train number:<br></p>
<input type="number" name="enter train number">
<br>
<input type="BUTTON" Value="sumit" Onclick="window.location.href='http://enquiry.indianrail.gov.in/ntes/'">
</FORM>
  <div id="map-canvas"></div> 

<object width="1400" height="400" align ="top" data="http://www.indianrail.gov.in/7days_avlpress_jp.html">
</object>
<address style="font-size : 130%% ; text-align : center ; color : black ; font-family : verdana">
Submitted BY - <br>
Shresth Vats (43) <br>
Shitanshu Shekhar (41) <br>
5th Sem (IT) <br>
</body> 
