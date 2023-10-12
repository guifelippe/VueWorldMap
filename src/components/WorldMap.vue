<template>
    <div class="map-container">
      <div ref="map" class="map"></div>
    </div>
</template>
  
<script>
  import L from 'leaflet';
  import 'leaflet/dist/leaflet.css';
  
  export default {
    mounted() {
        const map = L.map(this.$refs.map, {
            maxBounds: L.latLngBounds(L.latLng(-85, -180), L.latLng(85, 180))
        }).setView([0, 0], 2.5);
    
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);

        var greenIcon = L.icon({
            iconUrl: require('@/assets/icon.png'),

            iconSize:[50, 50],
        });

        const wonders = [
            {
                name: 'Great Wall of China',
                location: [40.4319077, 116.5703744],
                description: 'The Great Wall of China is a series of fortifications made of stone, brick, tamped earth, wood, and other materials. It is the world\'s longest wall and an iconic symbol of China.',
            },
            {
                name: 'Christ the Redeemer in Rio de Janeiro, Brazil',
                location: [-22.951389, -43.210833],
                description: 'Christ the Redeemer is an iconic statue of Jesus Christ located atop the Corcovado mountain in Rio de Janeiro. It is one of the New Seven Wonders of the World.',
            },
            {
                name: 'Machu Picchu in Peru',
                location: [-13.163136, -72.545197],
                description: 'Machu Picchu is an Inca citadel located in the Andes Mountains of Peru. It is one of the most famous and well-preserved archaeological sites in the world.',
            },
            {
                name: 'Chichén Itzá in Mexico',
                location: [20.684288, -88.568944],
                description: 'Chichén Itzá is a large pre-Columbian archaeological site in Yucatán, Mexico. It is known for its pyramid, temples, and other ancient structures.',
            },
            {
                name: 'Roman Colosseum, Italy',
                location: [41.890169, 12.492269],
                description: 'The Roman Colosseum, also known as the Flavian Amphitheatre, is an ancient amphitheater located in the center of Rome, Italy. It is one of the most iconic and well-preserved ancient Roman structures.',
            },
            {
                name: 'Taj Mahal in India',
                location: [27.175144, 78.042142],
                description: 'The Taj Mahal is a white marble mausoleum in Agra, India. It was built by Mughal Emperor Shah Jahan in memory of his beloved wife Mumtaz Mahal.',
            },
            {
                name: 'Petra in Jordan',
                location: [30.328611, 35.442222],
                description: 'Petra is an archaeological and historical city in southern Jordan. It is famous for its rock-cut architecture and water conduit system.',
            },
            {
                name: 'Great Pyramid of Giza, Egypt',
                location: [29.9792345, 31.1342023],
                description: 'The Great Pyramid of Giza is the oldest and largest of the three pyramids in the Giza pyramid complex. It is one of the Seven Wonders of the Ancient World.',
            },
            {
                name: 'Hanging Gardens of Babylon, Iraq',
                location: [32.536111, 44.427778],
                description: 'The Hanging Gardens of Babylon are one of the Seven Wonders of the Ancient World. They were described as a remarkable feat of engineering with an ascending series of tiered gardens.',
            },
            {
                name: 'Statue of Zeus at Olympia, Greece',
                location: [37.6384527, 21.629832],
                description: 'The Statue of Zeus at Olympia was a giant seated figure of the Greek god Zeus, made by the sculptor Phidias. It was located in the Temple of Zeus at Olympia, Greece.',
            },
            {
                name: 'Temple of Artemis at Ephesus, Turkey',
                location: [37.9489587, 27.364141],
                description: 'The Temple of Artemis at Ephesus was a Greek temple dedicated to the goddess Artemis. It was one of the Seven Wonders of the Ancient World.',
            },
            {
                name: 'Mausoleum at Halicarnassus, Turkey',
                location: [37.036204, 27.430583],
                description: 'The Mausoleum at Halicarnassus was a tomb built between 353 and 350 BC at Halicarnassus for Mausolus, a satrap in the Persian Empire.',
            },
            {
                name: 'Colossus of Rhodes, Greece',
                location: [36.451741, 28.225825],
                description: 'The Colossus of Rhodes was a statue of the Greek sun god Helios, erected on the Greek island of Rhodes in 280 BC. It was one of the Seven Wonders of the Ancient World.',
            },
            {
                name: 'Lighthouse of Alexandria, Egypt',
                location: [31.2156491, 29.8856611],
                description: 'The Lighthouse of Alexandria, sometimes called the Pharos of Alexandria, was a lighthouse built by the Ptolemaic Kingdom during the reign of Ptolemy II Philadelphus.',
            },
            {
                name: 'Statue of Liberty, USA',
                location: [40.689247, -74.044502],
                description: 'The Statue of Liberty is a colossal neoclassical sculpture on Liberty Island in New York Harbor within New York City, in the United States.',
            },
            {
                name: 'Eiffel Tower, France',
                location: [48.8588443, 2.2943506],
                description: 'The Eiffel Tower is a wrought-iron lattice tower in Paris, France. It is one of the most recognizable structures in the world and a symbol of France.',
            },
            {
                name: 'Big Ben, United Kingdom',
                location: [51.5007292, -0.1246254],
                description: 'Big Ben is the nickname for the Great Bell of the clock at the north end of the Palace of Westminster in London. It is one of London\'s most famous landmarks.',
            },
            {
                name: 'Kremlin, Russia',
                location: [55.751244, 37.618423],
                description: 'The Kremlin is a historic fortified complex at the heart of Moscow. It includes several palaces, cathedrals, and the official residence of the President of Russia.',
            },
        ];

        wonders.forEach(wonder => {
            const marker = L.marker(wonder.location, { icon: greenIcon }).addTo(map);
            marker.bindPopup(`<strong>${wonder.name}</strong><br>${wonder.description}`);
        });
    }
  };
</script>
  
<style scoped>
  .map-container {
    height: 100vh;
    width: 100vw;
  }
  
  .map {
    height: 100%;
    width: 100%;
  }
</style>