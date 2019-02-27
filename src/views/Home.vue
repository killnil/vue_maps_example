<template>
  <div class="home">
    <div id="map"></div>
  </div>
</template>

<style>
#map {
  height: 500px;
}
</style>

<script>
export default {
  data: function() {
    return {
      
    };
  },
  created: function() {},
  methods: {},
  mounted: function() {
    var chicago = { lat: 41.881832, lng: -87.623177 };

    var map = new google.maps.Map(document.getElementById('map'), {
      center: chicago,
      zoom: 14
    });

    var places = [
                  { location: {lat: 41.8921364, lng: -87.6348295 }, description: '<h4>Actualize</h4>'},
                  { location: {lat: 41.8900446, lng: -87.6399496 }, description: '<h4>3 Greens Market</h4>'},
                  { location: {lat: 41.8901446, lng: -87.6328164 }, description: '<h4>Firecakes Donuts</h4>'},
                  { location: {lat: 41.890738,  lng: -87.6374355 }, description: '<h4>Blommer Chocolate Company</h4>'}
                  ];


    places.forEach(function(place) {
      var infowindow = new google.maps.InfoWindow({ content: place.description });

      var marker = new google.maps.Marker({
          position: place.location,
          map: map
        });

      marker.addListener('click', function() {
        infowindow.open(map, marker);
      });
    });

  }
};
</script>













