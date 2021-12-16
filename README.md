<!DOCTYPE html>
<html>

  <head>
    <meta charset='utf-8' />
    <title>University of Oregon Mapping</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <!--    The Mapbox JavaScript here in the <head> of the page    -->
      <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.js'></script>
    <!--    The Mapbox CSS here in the <head> of the page    -->
      <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.css' rel='stylesheet' />
      
      <!--   Link to Google font-->
   <link rel="preconnect" href="https://fonts.gstatic.com">
   <link href="https://fonts.googleapis.com/css2?family=Martel&display=swap" rel="stylesheet">
      
    <style>
        /* CSS code between the <style> tags */
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%;}
        
        /* Overrides the pop-up width slightly bigger min-width than the default Mapbox CSS*/
         .mapboxgl-popup {
            min-width: 600px;
            /*add the css for the popup font here */
            font-family: 'Verdana',sans-serif;
        }
        /*add the css for the container font and general properties here */
          #container {
    position: relative;
    height: 100%;
    border-style: solid;
    border-color: white;
    background: #006666;
    color: aliceblue;
    font-family: 'Verdana',sans-serif;
    text-align: center;
    text-shadow:4px 4px 8px #000000;
    }
          #footer {
    position: absolute;
    bottom: 0;
    }
        /* The CSS for the "Fly" buttons  */
        .fly {
            display: inline-block; /* displays over the map */
            position: relative; /* displays over the map */
            margin: 0px auto; 
            width: 12%;  /* width of parent div */
            padding: 5px;
            border-style: solid;
            border-color: oldlace;
            border-radius: 15px; /* rounded corners */
            font-size: 0.75em;
            text-align: center;
            font-weight: bold;
            color: black;
            background: LightBlue;
            cursor:pointer;
            text-shadow:2px 2px 4px #ffffff;
        }
        
        /* Insert the CSS for the image here */
        .popupImage{
            width:100%;
        }
        /* Insert the CSS for the button here */
        button {
     font-family: 'Martel', serif;
     font-weight: 600;
        }
        /* Insert the CSS for the Creative Commons license here */
        #license{
            display: inline-block;
            position: relative;
            top: 800px;
            height: 10%;
            width: 10%;
        }

    </style>
  </head>

  <body>
      <!--  The map div -->
      <div id='map'></div>
     <!--  The container div that shows the title and explains what the website is -->
       <div id="container">

    <h1>COASTAL TOWNS TO VISIT IN OREGON</h1>

<p>Fly to Cities on the Oregon Coast by Clicking on the corresponing buttons below<br> (They are listed from Northernmost to Southernmost)</p> 

</div>
     
       <!--  Insert the button elements here  -->

      <button class='fly' id='AstoriaButton'>Astoria</button>
      <button class='fly' id='TillamookButton'>Tillamook</button>
      <button class='fly' id='LincolnCityButton'>Lincoln City</button>
      <button class='fly' id='NewPortButton'>Newport</button>
      <button class='fly' id='WaldButton'>Waldport</button>
      <button class='fly' id='FlorenceButton'>Florence</button>
      <button class='fly' id='CoosBayButton'>Coos-Bay</button>
      <button class='fly' id='PortOrfordButton'>Port-Orford</button>
      <button class='fly' id='FullmapButton'>BACK TO OREGON</button>
<!-- Insert the DIV for the creative commons license here -->
<div>
       <a id="license" rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><a rel="license" href="http://creativecommons.org/licenses/by/4.0/"></a>.
      </div>
    <script>
        // Insert the JavaScript within the <script> tags, within the body   
        // Start with the Mapbox access token
        mapboxgl.accessToken = 'pk.eyJ1Ijoiam9tZXJzb24iLCJhIjoiY2o1bXE2bHlyMnJhZDMzbnpyMnhlODdpcSJ9.QJMJ_cTFCY050aZfSn1umQ';

        // Initialize the map
        var map = new mapboxgl.Map({
            container: 'map', // id of a div on your page, where the map will be inserted
            style: 'mapbox://styles/mapbox/navigation-night-v1', // stylesheet location
            bearing: 90,
            center: [-121.95859,43.938812], // starting position [lng, lat] eg. [-122.6788, 45.5212]
            zoom: 6, // starting zoom 
            pitch: 20
        });

        /***  POPUPS  ***/
            // popups go here
         /***  POPUPS  ***/
        
 // Popup for marker 1  
 var popup1_content = '<h2><u>Port Orford</u></h2><br>';
 popup1_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/Rcf0iqhBwfU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup1_content += 'Port Orford is the oldest town on the Oregon Coast and the western most town in the contiguous states! Incorporated in 1911, its home to around 1,150 residents.<br>'; 
 popup1_content += 'Source: Wollertz Photography, <a href="https://www.youtube.com/channel/UCAcdlzHRF9GUym7ryB-CClw">YouTube</a>';       
 var popup1 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup1_content);
       
 // Popup for marker 2  
 var popup2_content = '<h2><u>Coos Bay</u></h2><br>';
 popup2_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/p2tmvB-10Is" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup2_content += 'Coos Bay is one the most affordable towns to live in on the Oregon Coast. Founded in 1891, the town is home to about 16,000 residents.<br>';
 popup2_content += 'Source: HOMEiA, <a href="https://www.youtube.com/channel/UC9HpnPuENo3FxYQqsRsA9VA"> Youtube </a>';
 var popup2 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup2_content);

    
 // Popup for marker 3  
 var popup3_content = '<h2><u>Florence</u></h2><br>';   
 popup3_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/iArhV0hWQWM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup3_content += 'Incorporated in 1893, Florence is home to around 8,921 residents. Florence has hosted the annual Rhododendron Festival since 1908!<br>';
 popup3_content += 'Source: Florence Oregon Coast, <a href="https://www.youtube.com/channel/UC2ycZn9rTjH03OC6QILB6ng">Youtube</a>';
 var popup3 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup3_content);
        
//Popup for marker 4
 var popup4_content = '<h2><u>Waldport</u></h2><br>';
 popup4_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/iWoYeeo0u7o" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>' ;
 popup4_content += 'Founded by German immigrants, Wald means Forest in German. Its no wonder the towns nickname is: Where the Forest Meets the Sea. Incorporated in 1911, Waldport is home to 2,200 residents.<br>';
 popup4_content += 'Source: The David Rush Travel Show, <a href="https://www.youtube.com/channel/UCtchsyz77lve1Ru07-AHUGA">Youtube</a>';
 var popup4= new mapboxgl.Popup({ minWidth:'300px' })
        .setHTML(popup4_content);
        
// Popup for marker 5 
 var popup5_content = '<h2><u>Newport</u></h2><br>';
 popup5_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/g6qHiAwnvXU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup5_content += 'The land we now call Newport and Yaquina Bay was home to the Yacona tribe of Natives for 3000 years. Incorporated in 1882, Newport is now home to over 10,000 residents.<br>';
 popup5_content += 'Source: DVDesigns, <a href="https://www.youtube.com/channel/UCrXhZaeTtge85xz9zOC1YRw">YouTube</a>';       
 var popup5 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup5_content);
        
// Popup for marker 6 
 var popup6_content = '<h2><u>Lincoln City</u></h2><br>';
 popup6_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/iP6NINUm0Hc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup6_content += 'Named in honor of former US President Abraham Lincoln, the town wasnt incorporated until 1965. Today its home to around 10,000 residents.<br>';
 popup6_content += 'Source: StatManStudios, <a href="https://www.youtube.com/channel/UCi0h-ueQ-1VoiaKUyPUtVEQ">YouTube</a>';     
 var popup6 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup6_content);
        
// Popup for marker 7
 var popup7_content = '<h2><u>Tillamook</u></h2><br>';
 popup7_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/5lNYAlTsGiU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup7_content += 'The city is named after the Tillamook nation of indigenous people. Incorporated in 1891, its now home to over 5,00 residents and Tillamook Country Creamery.<br>'
 popup7_content += 'Source: HomeStar Video Tours, <a href="https://www.youtube.com/channel/UCdHKowOa5WB9soOR-wQHuTg">YouTube</a>';       
 var popup7 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup7_content);
        
// Popup for marker 8
 var popup8_content = '<h2><u>Astoria</u></h2><br>';
 popup8_content += '<iframe width="560" height="315" src="https://www.youtube.com/embed/6hPpI-WobtY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
 popup8_content += 'Founded in 1811, Astoria is the oldest city in the state of Oregon, its also one of the rainiest with measurable precipitation 191 days out of the year. Its home to over 10,000 residents today.'
 popup8_content += 'Source: River Karaba, <a href="https://www.youtube.com/channel/UCUY1yQDzIYhCFbO3Kq7DZMQ">YouTube</a>';       
 var popup8 = new mapboxgl.Popup({ minWidth:'300px' })
     .setHTML(popup8_content);
/***  END POPUPS  ***/ 

        /***  END POPUPS  ***/  


        /***  MARKERS  ***/
            // markers go here
          /***  MARKERS  ***/
      // Marker 1 - PortOrford
     var marker1 = new mapboxgl.Marker({color:'LightBlue'})
        .setLngLat([-124.498981,42.751012]) // PortOrford 
	    .setPopup(popup1)
        .addTo(map);

        
    // Marker 2 - Coos Bay
    var marker2 = new mapboxgl.Marker({color:'LightBlue'})
       .setLngLat([-124.214056,43.373401]) // Coos Bay 
       .setPopup(popup2)
       .addTo(map);

        
    // Marker 3 - Florence
    var marker3 = new mapboxgl.Marker({color:'LightBlue'})
      .setLngLat([-124.108442,43.976086]) // Florence
      .setPopup(popup3)
      .addTo(map);
        
    //Marker 4 - Waldport
     var marker4= new mapboxgl.Marker({color:'LightBlue'})
      .setLngLat([-124.066667,44.427811]) // Waldport
      .setPopup(popup4)
      .addTo(map);
        
     //Marker 5 - Newport
     var marker5= new mapboxgl.Marker({color:'LightBlue'})
      .setLngLat([-124.057902,44.635510]) // Newport
      .setPopup(popup5)
      .addTo(map);
        
        //Marker 6 - Lincoln City
     var marker6= new mapboxgl.Marker({color:'LightBlue'})
      .setLngLat([-124.012403,44.976470]) // Lincoln City
      .setPopup(popup6)
      .addTo(map);
        
        //Marker 7 - Tillamook
     var marker7= new mapboxgl.Marker({color:'LightBlue'})
      .setLngLat([-123.87283,45.481192]) // Tillamook
      .setPopup(popup7)
      .addTo(map);
        
         //Marker 8 - Astoria
     var marker8= new mapboxgl.Marker({color:'LightBlue'})
      .setLngLat([-123.843222,46.186714]) // Astoria
      .setPopup(popup8)
      .addTo(map);
    /***  END MARKERS  ***/

        /***  END MARKERS  ***/


        /***  LISTENERS  ***/
            //listeners go here
        // Add a 'Listener' to the button element with the ID 'LondonButton'.
document.getElementById('CoosBayButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center: [-124.214056,43.373401], 
            zoom: 11,
            pitch: 60,
        });
});
        
// Add a 'Listener' to the button element with the ID 'PortlandButton'.
document.getElementById('PortOrfordButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-124.498981,42.751012], 
            zoom: 12,
            pitch: 60,
        });
});
        document.getElementById('FlorenceButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-124.108442,43.976086], 
            zoom: 12,
            pitch: 60,
        });
});
        document.getElementById('FullmapButton').addEventListener('click', function () {
        map.jumpTo({
            bearing: 90,
            center:[-120.55859,43.938812], 
            zoom: 6,
            pitch: 20,
        });
});
         document.getElementById('WaldButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-124.066667,44.427811],
            zoom: 12,
            pitch: 60,
        });
});
        document.getElementById('NewPortButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-124.057902,44.635510],
            zoom: 12,
            pitch: 60,
        });
});
        document.getElementById('LincolnCityButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-124.012403,44.976470],
            zoom: 12,
            pitch: 60,
        });
});
        document.getElementById('TillamookButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-123.87283,45.481192],
            zoom: 12,
            pitch: 60,
        });
});
        document.getElementById('AstoriaButton').addEventListener('click', function () {
        map.flyTo({
            bearing: 90,
            center:[-123.843222,46.186714],
            zoom: 11,
            pitch: 60,
        });
});
        //insert the code for the navigation panel in the bottom right corner
       const nav = new mapboxgl.NavigationControl();
     map.addControl(nav, 'bottom-right');
     var state = { panelOpen: true };

        /***  END LISTENERS  ***/
    </script>

  </body>

</html>

