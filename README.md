 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive World Map</title>
    <style>
        /* Basic styling */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 50px;
        }

        .map {
            width: 80%;
            max-width: 1000px;
            margin: 20px;
            cursor: pointer;
        }

        .info-box {
            margin-top: 20px;
            padding: 20px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 8px;
            width: 80%;
            max-width: 500px;
            display: none;
        }

        .info-box h3 {
            margin-top: 0;
        }

        .state-list {
            list-style-type: none;
            padding: 0;
        }

        .state-list li {
            cursor: pointer;
            padding: 5px;
            background-color: #f0f0f0;
            margin: 5px 0;
            border-radius: 4px;
            text-align: center;
        }

        .state-list li:hover {
            background-color: #ddd;
        }

        /* Simple SVG styling */
        svg path {
            fill: #ffcc00;
            stroke: #000;
            stroke-width: 2;
        }

        svg path:hover {
            fill: #ff9900;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- World map (simplified version) -->
        <div id="world-map" class="map">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600" width="800" height="600">
                <g id="world">
                    <!-- India (example region) -->
                    <path id="india" d="M300,200 L350,200 L350,250 L300,250 Z" />
                    <!-- Pakistan (example region) -->
                    <path id="pakistan" d="M350,200 L400,200 L400,250 L350,250 Z" />
                    <!-- Australia (example region) -->
                    <path id="australia" d="M500,400 L550,400 L550,450 L500,450 Z" />
                    <!-- Russia (example region) -->
                    <path id="russia" d="M600,100 L650,100 L650,150 L600,150 Z" />
                </g>
            </svg>
        </div>

        <!-- Info Box -->
        <div id="info-box" class="info-box">
            <h3>Click on a country to view more details</h3>
            <div id="state-list-container"></div>
        </div>
    </div>

    <script>
        // Define states and places data
        const data = {
            india: {
                states: ["Maharashtra", "Karnataka", "Tamil Nadu", "Delhi"],
                places: {
                    Maharashtra: ["Mumbai", "Pune", "Nagpur"],
                    Karnataka: ["Bengaluru", "Mysuru", "Hubli"],
                    Tamil Nadu: ["Chennai", "Coimbatore", "Madurai"],
                    Delhi: ["Connaught Place", "Qutub Minar", "Red Fort"]
                }
            },
            pakistan: {
                states: ["Sindh", "Punjab", "Khyber Pakhtunkhwa", "Balochistan"],
                places: {
                    Sindh: ["Karachi", "Hyderabad", "Sukkur"],
                    Punjab: ["Lahore", "Rawalpindi", "Multan"],
                    Khyber Pakhtunkhwa: ["Peshawar", "Abbottabad", "Mardan"],
                    Balochistan: ["Quetta", "Gwadar", "Kalat"]
                }
            },
            australia: {
                states: ["New South Wales", "Queensland", "Victoria", "Western Australia"],
                places: {
                    "New South Wales": ["Sydney", "Newcastle", "Wollongong"],
                    Queensland: ["Brisbane", "Gold Coast", "Cairns"],
                    Victoria: ["Melbourne", "Geelong", "Ballarat"],
                    "Western Australia": ["Perth", "Bunbury", "Mandurah"]
                }
            },
            russia: {
                states: ["Moscow", "Saint Petersburg", "Kazan", "Sochi"],
                places: {
                    Moscow: ["Red Square", "Kremlin", "Gorky Park"],
                    "Saint Petersburg": ["Hermitage Museum", "Nevsky Prospect", "Peterhof Palace"],
                    Kazan: ["Kazan Kremlin", "Bauman Street", "Kul Sharif Mosque"],
                    Sochi: ["Sochi Park", "Olympic Village", "Rosa Khutor"]
                }
            }
        };

        // Map click handler
        document.querySelectorAll('path').forEach(path => {
            path.addEventListener('click', function() {
                const country = this.id;
                displayStates(country);
            });
        });

        // Display states in a country
        function displayStates(country) {
            const infoBox = document.getElementById('info-box');
            const stateListContainer = document.getElementById('state-list-container');
            stateListContainer.innerHTML = ''; // Clear previous content
            const states = data[country]?.states || [];

            if (states.length > 0) {
                const ul = document.createElement('ul');
                ul.classList.add('state-list');
                states.forEach(state => {
                    const li = document.createElement('li');
                    li.textContent = state;
                    li.onclick = () => displayPlaces(country, state);
                    ul.appendChild(li);
                });
                stateListContainer.appendChild(ul);
                infoBox.style.display = 'block';
            } else {
                alert('No data available for this country');
            }
        }

        // Display places in a state
        function displayPlaces(country, state) {
            const places = data[country]?.places[state] || [];
            alert(`Places in ${state}: ${places.join(", ")}`);
        }
    </script>

</body>
</html>

