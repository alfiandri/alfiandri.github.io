<!DOCTYPE html>
<html lang="id">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Virtual Tour 360°</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }

        #container {
            position: relative;
            width: 100vw;
            height: 100vh;
        }

        #panorama {
            width: 100%;
            height: 100%;
        }

        .controls {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 10px;
            z-index: 10;
        }

        .control-button {
            background-color: rgba(0, 0, 0, 0.6);
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 15px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }

        .control-button:hover {
            background-color: rgba(0, 0, 0, 0.8);
        }

        .hotspot {
            position: absolute;
            width: 30px;
            height: 30px;
            background-color: rgba(255, 255, 255, 0.7);
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
        }

        .hotspot:hover {
            background-color: rgba(255, 255, 255, 1);
            transform: scale(1.2);
        }

        .info-panel {
            position: absolute;
            top: 20px;
            left: 20px;
            background-color: rgba(0, 0, 0, 0.6);
            color: white;
            padding: 15px;
            border-radius: 5px;
            max-width: 300px;
            z-index: 10;
        }

        .loading {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            font-size: 24px;
            z-index: 20;
        }

        .fullscreen-button {
            position: absolute;
            top: 20px;
            right: 20px;
            background-color: rgba(0, 0, 0, 0.6);
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px;
            cursor: pointer;
            z-index: 10;
        }
    </style>
</head>

<body>
    <div id="container">
        <div id="panorama"></div>
        <div class="controls">
            <button class="control-button" id="prev-scene">Sebelumnya</button>
            <button class="control-button" id="next-scene">Berikutnya</button>
            <button class="control-button" id="zoom-in">Zoom In</button>
            <button class="control-button" id="zoom-out">Zoom Out</button>
        </div>
        <button class="fullscreen-button" id="fullscreen">Layar Penuh</button>
        <div class="info-panel">
            <h3 id="scene-title">Ruang Tamu</h3>
            <p id="scene-description">Selamat datang di tur virtual 360°. Silakan jelajahi dengan menggeser atau mengklik dan menarik panorama.</p>
        </div>
        <div class="loading" id="loading">Memuat...</div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Konfigurasi scenes
            const scenes = [{
                    id: 'scene1',
                    title: 'Ruang Tamu',
                    description: 'Ruang tamu modern dengan sofa nyaman dan pemandangan ke halaman.',
                    imageUrl: '/images/ruangtamu.png', // Placeholder untuk panorama 1
                    hotspots: [{
                        position: {
                            x: 0.7,
                            y: 0,
                            z: -0.5
                        },
                        targetScene: 'scene2',
                        tooltip: 'Ke Dapur'
                    }]
                },
                {
                    id: 'scene2',
                    title: 'Dapur',
                    description: 'Dapur minimalis dengan peralatan modern.',
                    imageUrl: '/images/dapur.png', // Placeholder untuk panorama 2
                    hotspots: [{
                            position: {
                                x: -0.7,
                                y: 0,
                                z: 0.5
                            },
                            targetScene: 'scene1',
                            tooltip: 'Kembali ke Ruang Tamu'
                        },
                        {
                            position: {
                                x: 0.8,
                                y: 0,
                                z: 0.3
                            },
                            targetScene: 'scene3',
                            tooltip: 'Ke Kamar Tidur'
                        }
                    ]
                },
                {
                    id: 'scene3',
                    title: 'Kamar Tidur',
                    description: 'Kamar tidur nyaman dengan jendela besar.',
                    imageUrl: '/images/tempattidur.png', // Placeholder untuk panorama 3
                    hotspots: [{
                        position: {
                            x: -0.8,
                            y: 0,
                            z: -0.3
                        },
                        targetScene: 'scene2',
                        tooltip: 'Kembali ke Dapur'
                    }]
                }
            ];

            // Variables
            let currentSceneIndex = 0;
            let camera, scene, renderer;
            let isUserInteracting = false;
            let onPointerDownMouseX = 0,
                onPointerDownMouseY = 0;
            let lon = 0,
                onPointerDownLon = 0;
            let lat = 0,
                onPointerDownLat = 0;
            let phi = 0,
                theta = 0;
            const distance = 50;
            const hotspotElements = [];

            init();

            // Inisialisasi
            function init() {
                // Setup Three.js
                camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 1, 1100);

                scene = new THREE.Scene();

                renderer = new THREE.WebGLRenderer();
                renderer.setPixelRatio(window.devicePixelRatio);
                renderer.setSize(window.innerWidth, window.innerHeight);

                const panoramaContainer = document.getElementById('panorama');
                panoramaContainer.appendChild(renderer.domElement);

                // Load scene pertama
                loadScene(scenes[currentSceneIndex]);

                // Event Listeners
                window.addEventListener('resize', onWindowResize);
                document.addEventListener('pointerdown', onPointerDown);
                document.addEventListener('pointermove', onPointerMove);
                document.addEventListener('pointerup', onPointerUp);
                document.addEventListener('wheel', onDocumentMouseWheel);

                // Kontrol navigasi
                document.getElementById('prev-scene').addEventListener('click', prevScene);
                document.getElementById('next-scene').addEventListener('click', nextScene);
                document.getElementById('zoom-in').addEventListener('click', zoomIn);
                document.getElementById('zoom-out').addEventListener('click', zoomOut);
                document.getElementById('fullscreen').addEventListener('click', toggleFullscreen);

                animate();
            }

            // Load scene
            function loadScene(sceneData) {
                // Update informasi
                document.getElementById('scene-title').textContent = sceneData.title;
                document.getElementById('scene-description').textContent = sceneData.description;

                // Tampilkan loading
                document.getElementById('loading').style.display = 'flex';

                // Hapus semua hotspot
                hotspotElements.forEach(hotspot => {
                    if (hotspot.parentNode) {
                        hotspot.parentNode.removeChild(hotspot);
                    }
                });
                hotspotElements.length = 0;

                // Bersihkan scene
                while (scene.children.length > 0) {
                    scene.remove(scene.children[0]);
                }

                // Load panorama baru
                const geometry = new THREE.SphereGeometry(500, 60, 40);
                geometry.scale(-1, 1, 1); // Membalik agar terlihat dari dalam

                // Gunakan placeholder untuk demo atau ganti dengan URL panorama asli
                const texture = new THREE.TextureLoader().load(sceneData.imageUrl, function() {
                    // Sembunyikan loading setelah gambar dimuat
                    document.getElementById('loading').style.display = 'none';

                    // Tambahkan hotspots
                    addHotspots(sceneData.hotspots);
                });

                const material = new THREE.MeshBasicMaterial({
                    map: texture
                });
                const mesh = new THREE.Mesh(geometry, material);
                scene.add(mesh);
            }

            // Tambahkan hotspots
            function addHotspots(hotspots) {
                if (!hotspots) return;

                hotspots.forEach(hotspot => {
                    const hotspotElement = document.createElement('div');
                    hotspotElement.className = 'hotspot';
                    hotspotElement.innerHTML = '➔'; // Simbol arrow
                    hotspotElement.setAttribute('title', hotspot.tooltip);
                    hotspotElement.addEventListener('click', () => {
                        // Cari index scene target
                        const targetIndex = scenes.findIndex(scene => scene.id === hotspot.targetScene);
                        if (targetIndex !== -1) {
                            currentSceneIndex = targetIndex;
                            loadScene(scenes[currentSceneIndex]);
                        }
                    });

                    document.getElementById('container').appendChild(hotspotElement);
                    hotspotElements.push(hotspotElement);

                    // Posisi 3D untuk hotspot
                    hotspotElement.position3D = hotspot.position;
                });
            }

            // Update posisi hotspot
            function updateHotspotPositions() {
                hotspotElements.forEach(hotspot => {
                    if (hotspot.position3D) {
                        // Convert 3D position to screen coordinates
                        const vector = new THREE.Vector3(
                            hotspot.position3D.x * 500,
                            hotspot.position3D.y * 500,
                            hotspot.position3D.z * 500
                        );

                        vector.project(camera);

                        const x = (vector.x * 0.5 + 0.5) * window.innerWidth;
                        const y = (-vector.y * 0.5 + 0.5) * window.innerHeight;

                        // Cek apakah hotspot berada di depan kamera
                        if (vector.z < 1) {
                            hotspot.style.display = 'flex';
                            hotspot.style.left = x + 'px';
                            hotspot.style.top = y + 'px';
                        } else {
                            hotspot.style.display = 'none';
                        }
                    }
                });
            }

            // Fungsi untuk scene sebelumnya
            function prevScene() {
                currentSceneIndex = (currentSceneIndex - 1 + scenes.length) % scenes.length;
                loadScene(scenes[currentSceneIndex]);
            }

            // Fungsi untuk scene berikutnya
            function nextScene() {
                currentSceneIndex = (currentSceneIndex + 1) % scenes.length;
                loadScene(scenes[currentSceneIndex]);
            }

            // Fungsi zoom in
            function zoomIn() {
                if (camera.fov > 30) {
                    camera.fov -= 5;
                    camera.updateProjectionMatrix();
                }
            }

            // Fungsi zoom out
            function zoomOut() {
                if (camera.fov < 100) {
                    camera.fov += 5;
                    camera.updateProjectionMatrix();
                }
            }

            // Toggle fullscreen
            function toggleFullscreen() {
                if (!document.fullscreenElement) {
                    document.documentElement.requestFullscreen().catch(err => {
                        console.error(`Error attempting to enable full-screen mode: ${err.message}`);
                    });
                } else {
                    if (document.exitFullscreen) {
                        document.exitFullscreen();
                    }
                }
            }

            // Handle window resize
            function onWindowResize() {
                camera.aspect = window.innerWidth / window.innerHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(window.innerWidth, window.innerHeight);
            }

            // Pointer down event
            function onPointerDown(event) {
                if (event.isPrimary === false) return;

                isUserInteracting = true;

                onPointerDownMouseX = event.clientX;
                onPointerDownMouseY = event.clientY;

                onPointerDownLon = lon;
                onPointerDownLat = lat;
            }

            // Pointer move event
            function onPointerMove(event) {
                if (event.isPrimary === false) return;

                if (isUserInteracting) {
                    lon = (onPointerDownMouseX - event.clientX) * 0.1 + onPointerDownLon;
                    lat = (event.clientY - onPointerDownMouseY) * 0.1 + onPointerDownLat;
                }
            }

            // Pointer up event
            function onPointerUp() {
                isUserInteracting = false;
            }

            // Mouse wheel event
            function onDocumentMouseWheel(event) {
                const fov = camera.fov + event.deltaY * 0.05;
                camera.fov = THREE.MathUtils.clamp(fov, 30, 100);
                camera.updateProjectionMatrix();
            }

            // Animation loop
            function animate() {
                requestAnimationFrame(animate);
                update();
            }

            // Update camera position
            function update() {
                lat = Math.max(-85, Math.min(85, lat));
                phi = THREE.MathUtils.degToRad(90 - lat);
                theta = THREE.MathUtils.degToRad(lon);

                camera.position.x = distance * Math.sin(phi) * Math.cos(theta);
                camera.position.y = distance * Math.cos(phi);
                camera.position.z = distance * Math.sin(phi) * Math.sin(theta);

                camera.lookAt(0, 0, 0);

                renderer.render(scene, camera);

                // Update posisi hotspot
                updateHotspotPositions();
            }
        });
    </script>
</body>

</html>
