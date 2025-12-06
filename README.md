<!DOCTYPE html>
<html>
<head>
  <title>Mapa Personalizado</title>
  <script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyBRUQq2kEZsfrR_aYWdEWAbpzW-Fn5WoZU"></script>
  <script>
    function initMap() {
      const map = new google.maps.Map(document.getElementById('map'), {
        center: { lat: -34.6037, lng: -58.3816 }, // por ejemplo, Buenos Aires
        zoom: 10
      });

      const puntos = [
        { lat: -34.60, lng: -58.38, image: 'https://ejemplo.com/imagen1.jpg' },
        // Más puntos aquí
      ];

      puntos.forEach(punto => {
        const marker = new google.maps.Marker({
          position: { lat: punto.lat, lng: punto.lng },
          map: map
        });

        if (punto.image) {
          const infowindow = new google.maps.InfoWindow({
            content: `<img src="${punto.image}" alt="Imagen" style="width:150px;">`
          });

          marker.addListener('click', () => {
            infowindow.open(map, marker);
          });
        }
      });
    }
  </script>
</head>
<body onload="initMap()">
  <div id="map" style="height: 500px; width: 100%;"></div>
</body>
</html>
