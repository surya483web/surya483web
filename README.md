 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive World Map with Images</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            text-align: center;
        }

        .container {
            margin-top: 30px;
        }

        .map-container {
            width: 90%;
            max-width: 1000px;
            margin: 0 auto;
        }

        .info-box {
            margin-top: 30px;
            padding: 20px;
            background-color: white;
            border: 1px solid #ccc;
            border-radius: 8px;
            width: 80%;
            max-width: 600px;
            margin: 20px auto;
            display: none;
            text-align: left;
        }

        .info-box h2 {
            margin-top: 0;
        }

        .info-box img {
            width: 100%;
            height: auto;
            margin-top: 15px;
        }

        svg path {
            cursor: pointer;
            fill: #b0e0e6;
            stroke: #333;
            stroke-width: 0.5;
        }

        svg path:hover {
            fill: #00bcd4;
        }

        .placeholder-image {
            width: 100%;
            max-width: 300px;
            height: auto;
            margin-top: 15px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Interactive World Map with Images</h1>
        <div class="map-container">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600" width="800" height="600">
                <!-- Africa -->
                <path id="africa" d="M300,250 L350,250 L350,300 L300,300 Z" data-name="Africa" />
                <!-- Asia -->
                <path id="asia" d="M400,100 L450,100 L450,150 L400,150 Z" data-name="Asia" />
                <!-- Europe -->
                <path id="europe" d="M500,50 L550,50 L550,100 L500,100 Z" data-name="Europe" />
                <!-- North America -->
                <path id="north-america" d="M150,100 L200,100 L200,150 L150,150 Z" data-name="North America" />
                <!-- South America -->
                <path id="south-america" d="M150,300 L200,300 L200,350 L150,350 Z" data-name="South America" />
                <!-- Australia -->
                <path id="australia" d="M600,400 L650,400 L650,450 L600,450 Z" data-name="Australia" />
                <!-- Antarctica -->
                <path id="antarctica" d="M700,500 L750,500 L750,550 L700,550 Z" data-name="Antarctica" />
            </svg>
        </div>

        <div class="info-box" id="info-box">
            <h2 id="country-name">Country Info</h2>
            <p id="country-info">Click on a continent or country to see more information.</p>
            <img id="country-image" class="placeholder-image" src="" alt="Country Image">
        </div>
    </div>

    <script>
        // JavaScript to handle clicks on countries and continents
        const countryData = {
            africa: {
                name: 'Africa',
                info: 'Africa is the second largest continent in the world and is known for its diverse cultures, wildlife, and landscapes.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=Africa'
            },
            asia: {
                name: 'Asia',
                info: 'Asia is the largest continent, home to more than 4.6 billion people, and is rich in history and diverse cultures.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=Asia'
            },
            europe: {
                name: 'Europe',
                info: 'Europe is a continent known for its historical landmarks, cultural diversity, and its role in global politics.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=Europe'
            },
            'north-america': {
                name: 'North America',
                info: 'North America includes countries like the USA, Canada, and Mexico, and is known for its economic power and technological innovations.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=North+America'
            },
            'south-america': {
                name: 'South America',
                info: 'South America is home to the Amazon rainforest and diverse cultures, with countries like Brazil, Argentina, and Chile.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=South+America'
            },
            australia: {
                name: 'Australia',
                info: 'Australia is both a country and a continent, famous for its unique wildlife, the Great Barrier Reef, and beautiful beaches.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=Australia'
            },
            antarctica: {
                name: 'Antarctica',
                info: 'Antarctica is the southernmost continent, known for being covered by ice and home to research stations and wildlife like penguins.',
                image: 'https://via.placeholder.com/500x300/ffcc00/000000?text=Antarctica'
            }
        };

        // Function to show information and image when a country is clicked
        document.querySelectorAll('svg path').forEach(path => {
            path.addEventListener('click', function () {
                const countryId = this.id;
                displayCountryInfo(countryId);
            });
        });

        // Function to display country info and image
        function displayCountryInfo(countryId) {
            const country = countryData[countryId];
            if (country) {
                document.getElementById('country-name').textContent = country.name;
                document.getElementById('country-info').textContent = country.info;
                document.getElementById('country-image').src = country.image;
                document.getElementById('info-box').style.display = 'block';
            } else {
                alert('Country data not available.');
            }
        }
    </script>

</body>
</html>
