 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Globe World</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <!-- Include the Three.js library -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // Set up the scene, camera, and renderer
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        // Create a sphere geometry (the globe)
        const geometry = new THREE.SphereGeometry(5, 32, 32); // radius, width segments, height segments

        // Create a texture for the globe (Earth map)
        const texture = new THREE.TextureLoader().load('https://cdn.pixabay.com/photo/2014/11/18/16/56/earth-533157_960_720.jpg');
        const material = new THREE.MeshBasicMaterial({ map: texture });

        // Create a mesh with the geometry and material
        const globe = new THREE.Mesh(geometry, material);
        scene.add(globe);

        // Position the camera
        camera.position.z = 15;

        // Animation loop
        function animate() {
            requestAnimationFrame(animate);

            // Rotate the globe for a spinning effect
            globe.rotation.y += 0.001;

            // Render the scene
            renderer.render(scene, camera);
        }

        // Start the animation loop
        animate();

        // Adjust the renderer size when the window is resized
        window.addEventListener('resize', () => {
            renderer.setSize(window.innerWidth, window.innerHeight);
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
        });
    </script>
</body>
</html>



