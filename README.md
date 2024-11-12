<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Câmeras de Trânsito - Recife</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }
        header {
            background-color: #007BFF;
            color: white;
            padding: 20px;
            text-align: center;
            width: 100%;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
        }
        main {
            padding: 80px 20px 20px 20px;
            width: 100%;
            max-width: 1200px;
        }
        .grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            width: 100%;
        }
        .card {
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        img {
            width: 100%;
            height: auto;
            display: block;
        }
        .info {
            padding: 15px;
            color: #555;
            font-weight: bold;
        }
        .button {
            display: block;
            background-color: #007BFF;
            color: white;
            text-align: center;
            padding: 10px;
            text-decoration: none;
            border-radius: 0 0 8px 8px;
        }
        footer {
            background-color: #007BFF;
            color: white;
            padding: 20px;
            text-align: center;
            width: 100%;
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
        }
        .camera-info {
            text-align: center;
            margin-top: 40px;
        }
        .camera-info img {
            width: 100px;
            height: auto;
            display: block;
            margin: 0 auto 10px;
        }
    </style>
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY"></script>
</head>
<body>
    <header>
        <h1>Câmeras de Trânsito - Recife</h1>
    </header>
    <main>
        <div class="countdown" id="countdown">Atualizando em: 3:00</div>
        <div class="grid" id="camera-grid"></div>
        <div id="map"></div>
        <div class="grid">
            <div class="card">
                <img src="camera1.jpg" alt="Câmera 1">
                <div class="info">Localização: Avenida Boa Viagem</div>
                <a href="#" class="button">Ver Detalhes</a>
            </div>
            <div class="card">
                <img src="camera2.jpg" alt="Câmera 2">
                <div class="info">Localização: Rua da Aurora</div>
                <a href="#" class="button">Ver Detalhes</a>
            </div>
            <div class="card">
                <img src="camera3.jpg" alt="Câmera 3">
                <div class="info">Localização: Avenida Agamenon Magalhães</div>
                <a href="#" class="button">Ver Detalhes</a>
            </div>
            <!-- Adicione mais câmeras conforme necessário -->
        </div>
    </main>
    <footer>
        <p>&copy; 2023 Câmeras de Trânsito - Recife</p>
    </footer>

    <div class="modal" id="imageModal">
        <span class="close" onclick="closeModal()">&times;</span>
        <img id="modalImage" src="" alt="">
    </div>
    <!-- Webcam Section -->
    <div class="grid">
        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618848563/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDg1NjMsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.rPEZXLBZW1TDbxQf9Q0cFnCHnZTDAwVqJzvsUfJQgfQ&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/63/1618848563/current/full/1618848563.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDg1NjMsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.rPEZXLBZW1TDbxQf9Q0cFnCHnZTDAwVqJzvsUfJQgfQ" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Avenida Governador Agamenon Magalhães - Soledade</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 39 minutos | 
                        Distância: 1.6 km
                    </div>
                " data-lg-id="59c0f392-8316-421b-ba1c-b2d332619372">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618848563/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDg1NjMsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.rPEZXLBZW1TDbxQf9Q0cFnCHnZTDAwVqJzvsUfJQgfQ&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Avenida Governador Agamenon Magalhães - Soledade" data-coord="-8.05204 -34.89536">
                    Recife: Avenida Governador Agamenon Magalhães - Soledade
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="almost-out-of-date"></div>
                            há 39 minutos
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 1.6 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618847951/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc5NTEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.jTPeZjlCKqPrTf4F6c37k5CNJHpSbI2y9kIh6ptcqu0&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/51/1618847951/current/full/1618847951.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc5NTEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.jTPeZjlCKqPrTf4F6c37k5CNJHpSbI2y9kIh6ptcqu0" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Paissandu - Avenida Governador Agamenon Magalhães</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 1 hora | 
                        Distância: 2 km
                    </div>
                " data-lg-id="c6868d3c-a9e6-4de9-80d0-6dda035eafea">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618847951/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc5NTEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.jTPeZjlCKqPrTf4F6c37k5CNJHpSbI2y9kIh6ptcqu0&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Paissandu - Avenida Governador Agamenon Magalhães" data-coord="-8.06196 -34.89769">
                    Recife: Paissandu - Avenida Governador Agamenon Magalhães
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="out-of-date"></div>
                            há 1 hora
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 2 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618847806/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc4MDYsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.VmXvBPKhIGgTl1mSQ49dgDj2tuRx875LHB1IlPSiyBY&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/06/1618847806/current/full/1618847806.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc4MDYsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.VmXvBPKhIGgTl1mSQ49dgDj2tuRx875LHB1IlPSiyBY" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Paissandu - Avenida Governador Agamenon Magalhães</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 2 horas | 
                        Distância: 2 km
                    </div>
                " data-lg-id="0b424c91-0367-410f-9f68-1ae9dafc61cd">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618847806/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc4MDYsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.VmXvBPKhIGgTl1mSQ49dgDj2tuRx875LHB1IlPSiyBY&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Paissandu - Avenida Governador Agamenon Magalhães" data-coord="-8.06289 -34.89739">
                    Recife: Paissandu - Avenida Governador Agamenon Magalhães
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="out-of-date"></div>
                            há 2 horas
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 2 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618847579/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc1NzksInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.09_1KtKPxhXQWFOjIVMMUxtoOHu7FDmK9z6XzidIXg0&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/79/1618847579/current/full/1618847579.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc1NzksInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.09_1KtKPxhXQWFOjIVMMUxtoOHu7FDmK9z6XzidIXg0" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Praça do Derby</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 59 minutos | 
                        Distância: 2.1 km
                    </div>
                " data-lg-id="de63003c-0bab-4185-842e-ad1ac198140a">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618847579/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDc1NzksInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.09_1KtKPxhXQWFOjIVMMUxtoOHu7FDmK9z6XzidIXg0&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Praça do Derby" data-coord="-8.05687 -34.89983">
                    Recife: Praça do Derby
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="almost-out-of-date"></div>
                            há 59 minutos
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 2.1 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618848275/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDgyNzUsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.ehMQQZ_whKCcqJY2feh6qcoMYsd-FfptRxZ7vP5qGlM&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/75/1618848275/current/full/1618848275.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDgyNzUsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.ehMQQZ_whKCcqJY2feh6qcoMYsd-FfptRxZ7vP5qGlM" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Clube Náutico Capibaribe</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 26 minutos | 
                        Distância: 2.2 km
                    </div>
                " data-lg-id="075309e0-6ed7-4583-88c8-b78e1d2a3f3f">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618848275/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg4NDgyNzUsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.ehMQQZ_whKCcqJY2feh6qcoMYsd-FfptRxZ7vP5qGlM&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Clube Náutico Capibaribe" data-coord="-8.04183 -34.89798">
                    Recife: Clube Náutico Capibaribe
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="semi-up-to-date"></div>
                            há 26 minutos
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 2.2 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618759734/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg3NTk3MzQsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.DSjPXameI6YWDl3En42vahweZhYU0CRWXtN_uUDLd_0&autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/34/1618759734/current/full/1618759734.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg3NTk3MzQsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.DSjPXameI6YWDl3En42vahweZhYU0CRWXtN_uUDLd_0" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Madalena</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>há 1 hora | Distância: 3 km</div>
                " data-lg-id="af2ffbb4-e3e7-49bc-a6f2-00037c5f8140">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618759734/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg3NTk3MzQsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.DSjPXameI6YWDl3En42vahweZhYU0CRWXtN_uUDLd_0&autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Madalena" data-coord="-8.05357 -34.90851">
                    Recife: Madalena
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="out-of-date"></div>há 1 hora
                        </span>
                        <span class="distance">Distância: 3 km</span>
                    </div>
                </div>
            </div>
        </div>
        
        

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618514501/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTQ1MDEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.cvcWRd2_wM9t84EStSvFtlnjC3UanrV5zq4DswaqNps&autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/01/1618514501/current/full/1618514501.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTQ1MDEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.cvcWRd2_wM9t84EStSvFtlnjC3UanrV5zq4DswaqNps" title="Recife" sub-html="
                        <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Igreja do Pina</div>
                        <div class='webcam-extra-info' style='font-size: 1.2em;'>há 1 hora | Distância: 3.2 km</div>
                    " data-lg-id="a928468c-5e41-44c4-9f3b-ab38a51bd079">
                    <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618514501/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTQ1MDEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.cvcWRd2_wM9t84EStSvFtlnjC3UanrV5zq4DswaqNps&autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Igreja do Pina" data-coord="-8.08876 -34.88513">
                    Recife: Igreja do Pina
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="out-of-date"></div>há 1 hora
                        </span>
                        <span class="distance">Distância: 3.2 km</span>
                    </div>
                </div>
            </div>
        </div>
        

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618253294/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTgyNTMyOTQsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.yZy4BKy1bPtTkvi7in2WY-hbmucbbk8IRGE-PDKL8SU&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/94/1618253294/current/full/1618253294.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTgyNTMyOTQsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.yZy4BKy1bPtTkvi7in2WY-hbmucbbk8IRGE-PDKL8SU" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Peace Community Center - COMPAZ- Alto Santa Terezinha</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 45 minutos | 
                        Distância: 4.7 km
                    </div>
                " data-lg-id="cb6681cc-cd71-4a5b-b34b-fc192f769760">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618253294/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTgyNTMyOTQsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.yZy4BKy1bPtTkvi7in2WY-hbmucbbk8IRGE-PDKL8SU&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Peace Community Center - COMPAZ- Alto Santa Terezinha" data-coord="-8.01045 -34.90322">
                    Recife: Peace Community Center - COMPAZ- Alto Santa Terezinha
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="almost-out-of-date"></div>
                            há 45 minutos
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 4.7 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618513395/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTMzOTUsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.9LTUruyff6WLh8fD6SeHoxc_6HPN80xZADF9BVV6xzc&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/95/1618513395/current/full/1618513395.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTMzOTUsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.9LTUruyff6WLh8fD6SeHoxc_6HPN80xZADF9BVV6xzc" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Av. Eng. Domingos Ferreira, 1818</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 1 hora | 
                        Distância: 4.8 km
                    </div>
                " data-lg-id="933d3a11-018e-42dd-b2c4-b9408b9faac8">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618513395/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTMzOTUsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.9LTUruyff6WLh8fD6SeHoxc_6HPN80xZADF9BVV6xzc&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Av. Eng. Domingos Ferreira, 1818" data-coord="-8.10511 -34.88949">
                    Recife: Av. Eng. Domingos Ferreira, 1818
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="out-of-date"></div>
                            há 1 hora
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 4.8 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618431781/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg0MzE3ODEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.nXh_U7atz0RkMLmIsWOEke9TZ1x01n3I8uxMfKB-t7Y&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/81/1618431781/current/full/1618431781.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg0MzE3ODEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.nXh_U7atz0RkMLmIsWOEke9TZ1x01n3I8uxMfKB-t7Y" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Av. Eng. Domingos Ferreira, 3814</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 7 minutos | 
                        Distância: 6.5 km
                    </div>
                " data-lg-id="ed49679a-6456-4d1e-aacd-63204d7bdbf4">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618431781/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg0MzE3ODEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.nXh_U7atz0RkMLmIsWOEke9TZ1x01n3I8uxMfKB-t7Y&amp;autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Av. Eng. Domingos Ferreira, 3814" data-coord="-8.12153 -34.89917">
                    Recife: Av. Eng. Domingos Ferreira, 3814
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="up-to-date"></div>
                            há 7 minutos
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 6.5 km
                        </span>
                    </div>
                </div>
            </div>
        </div>

        <div class="col-6 webcam-container">
            <div class="webcam-content" data-embed="https://webcams.windy.com/webcams/public/embed/player/1618433407/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg0MzM0MDcsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.D6Qeq743dR5_oRUkT6V-dwT40R4rI0GKA4ZDfCc4A14&amp;autoPlay=1">
                <a class="webcam-img" href="https://images-webcams.windy.com/public/07/1618433407/current/full/1618433407.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg0MzM0MDcsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.D6Qeq743dR5_oRUkT6V-dwT40R4rI0GKA4ZDfCc4A14" title="Recife" sub-html="
                    <div style='font-weight: bold; font-size: 1.5em; margin-bottom: 5px;'>Recife: Avenida Desembargador José Neves</div>
                    <div class='webcam-extra-info' style='font-size: 1.2em;'>
                        há 4 minutos | 
                        Distância: 6.9 km
                    </div>
                " data-lg-id="52514539-96ad-4a40-9179-8ad03f5378bf">
                <iframe src="https://webcams.windy.com/webcams/public/embed/player/1618514501/day?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ3ZWJjYW1faWQiOjE2MTg1MTQ1MDEsInVzZXJfdHlwZSI6MSwiYXZhaWxhYmxlX3NpemVzIjoidGVhc2VyYmcsaWNvbix0aHVtYm5haWwscHJldmlldyxub3JtYWwsZnVsbCxwYW5vcmFtYSIsImlhdCI6MTcyOTkwNDU4MSwiZXhwIjoxNzI5OTkwOTgxfQ.cvcWRd2_wM9t84EStSvFtlnjC3UanrV5zq4DswaqNps&autoPlay=1" width="389" height="219"></iframe>
                </a>
                <div class="title webcam-city" title="Recife: Avenida Desembargador José Neves" data-coord="-8.12117 -34.90982">
                    Recife: Avenida Desembargador José Neves
                    <div class="webcam-extra-info">
                        <span class="last-update">
                            <div class="up-to-date"></div>
                            há 4 minutos
                        </span>
                        <div class="activate-embed">
                            <span class="fasvg-12 fa-play"></span>
                        </div>
                        <span class="distance">
                            Distância: 6.9 km
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const cameraData = [
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.223/",
			alt: "Câmera em Aeroporto - Desembarque",
			info: "Aeroporto - Desembarque",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1318843,-34.9177437"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.224/",
			alt: "Câmera em Aeroporto - Embarque",
			info: "Aeroporto - Embarque",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1318843,-34.9177437"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.217/",
			alt: "Câmera em Alto Santa Terezinha - Próximo ao COMPAZ",
			info: "Rua Alto Santa Terezinha - Próximo ao COMPAZ",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0105487,-34.9030866"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.210/",
			alt: "Câmera em Av. Alfredo Lisboa - Marco Zero",
			info: "Av. Alfredo Lisboa - Marco Zero",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.062957,-34.871137"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.220/",
			alt: "Câmera em Av. Antônio de Goés - (SAD)",
			info: "Av. Antônio de Goés - (SAD)",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0889793,-34.8831811"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.141/",
			alt: "Câmera em Av. Caxangá, Semáforo 609",
			info: "Av. Caxangá, Semáforo 609",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.034399,-34.949951"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.207/",
			alt: "Câmera em Cons. Rosa e Silva x Av. Santos Dumont",
			info: "Av. Cons. Rosa e Silva x Av. Santos Dumont",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0395947,-34.8993822"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.231/",
			alt: "Câmera em Av. Conselheiro Aguiar, Rua Barão de Souza Leão",
			info: "Av. Conselheiro Aguiar, Rua Barão de Souza Leão",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1319088,-34.9014824"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.214/",
			alt: "Câmera em Av. da Recuperação x Rua Dois Irmãos",
			info: "Av. da Recuperação x Rua Dois Irmãos",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0172259,-34.9408671"
		  },		 
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.204/",
			alt: "Câmera em Av. São Paulo (Três Carneiros)",
			info: "Av. São Paulo (Três Carneiros)",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1244851,-34.9573657"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.103/",
			alt: "Câmera em Av. Marques de Olinda, Semáforo 020, Bairro do Recife",
			info: "Av. Marques de Olinda, Semáforo 020, Bairro do Recife",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.063417,-34.873583"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.126/",
			alt: "Câmera em Av. Des. José Neves - Sentido Subúrbio",
			info: "Av. Des. José Neves - Sentido Subúrbio",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1212609,-34.9097869"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.222/",
			alt: "Câmera em Av. Dois Rios, Semáforo 561",
			info: "Av. Dois Rios, Semáforo 561",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1104889,-34.9369696"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.202/",
			alt: "Câmera em Eng. Abdias de Carvalho x Gen. San Martin",
			info: "Av. Eng. Abdias de Carvalho x Gen. San Martin",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0992523,-34.8904273"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.228/",
			alt: "Câmera em Eng. Abdias de Carvalho x José Gonçalves",
			info: "Av. Eng. Abdias de Carvalho x José Gonçalves",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0610797,-34.9048904"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.132/",
			alt: "Câmera em Gov. Agamenon Magalhães, Sentido Boa Viagem",
			info: "Av. Gov. Agamenon Magalhães, Sentido Boa Viagem",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0399542,-34.878934"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.189/",
			alt: "Câmera em Gov. Agamenon Magalhães, Sentido Campo Grande",
			info: "Av. Gov. Agamenon Magalhães, Sentido Campo Grande",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0394729,-34.878737"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.229/",
			alt: "Câmera em Av. João de Barros x Rua 48",
			info: "Av. João de Barros x Rua 48",
				mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.044729,-34.890026"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.130/",
			alt: "Câmera em Av. Liberdade, Semáforo 440",
			info: "Av. Liberdade, Semáforo 440",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0810669,-34.9683467"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.227/",
			alt: "Câmera em Av. Maria Irene, Semáforo 581",
			info: "Av. Maria Irene, Semáforo 581",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0490336,-34.8964562"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.135/",
			alt: "Câmera em Norte, Semáforo 062",
			info: "Av.Norte, Semáforo 062",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.029633,-34.900494"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.136/",
			alt: "Câmera em Norte, Semáforo 081",
			info: "Av. Norte, Semáforo 081",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.033536,-34.896475"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.235/",
			alt: "Câmera em Pernambuco (UR1 Ibura)",
			info: "Av. Pernambuco (UR1 Ibura)",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1186386,-34.9463362"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.205/",
			alt: "Câmera em Recife x Rua Jean Emile Favre",
			info: "Av. Recife x Rua Jean Emile Favre",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1151579,-34.9245366"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.219/",
			alt: "Câmera em Recife, próximo ao Semáforo 059",
			info: "Av. Recife, próximo ao Semáforo 059",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.09400623,-34.9289640"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.121/",
			alt: "Câmera em Abdias de Carvalho - Estácio",
			info: "Av. Abdias de Carvalho - Estácio",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0623563,-34.9168512"
		  },
          {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.65/",
			alt: "Câmera em Agamenon Magalhães x Joaquim Inácio - Giro",
			info: "Av. Agamenon Magalhães x Joaquim Inácio - Giro",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0621773,-34.8977463"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.63/",
			alt: "Câmera em Av. Ag. Magalhães x Bandeira Filho - Semáforo 17",
			info: "Av. Ag. Magalhães x Bandeira Filho - Semáforo 17",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0517371,-34.8950253"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.192/",
			alt: "Câmera em Av. Beberibe - Próximo ao Arruda",
			info: "Av. Beberibe - Próximo ao Arruda",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0279204,-34.8928982"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.114/",
			alt: "Câmera em Av. Boa Viagem x Polo Pina - FIXA",
			info: "Av. Boa Viagem x Polo Pina - FIXA",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0918999,-34.8820963"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.109/",
			alt: "Câmera em Conde da Boa Vista x Rua Sete de Setembro - Semáforo",
			info: "Av. Conde da Boa Vista x Rua Sete de Setembro - Semáforo",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0611731,-34.8832374"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.125/",
			alt: "Câmera em Av. Des. José Neves - Sentido Centro",
			info: "Av. Des. José Neves - Sentido Centro",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1214768,-34.9093352"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.140/",
			alt: "Câmera em Av. Dr. José Rufino, Sentido Centro, Semáforo 044",
			info: "Av. Dr. José Rufino, Sentido Centro, Semáforo 044",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.091724,-34.936071"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.107/",
			alt: "Câmera em Eng. Abdias de Carvalho Nº 441 - Semáforo 271",
			info: "Av. Eng. Abdias de Carvalho Nº 441 - Semáforo 271",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0640708,-34.9356262"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.75/",
			alt: "Câmera em Eng. Abdias de Carvalho Nº 441 - Semáforo 272",
			info: "Av. Eng. Abdias de Carvalho Nº 441 - Semáforo 272",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0639982,-34.9357633"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.117/",
			alt: "Câmera em Av. Recife, Semáforo 617 - Sentido UFPE",
			info: "Av. Recife, Semáforo 617 - Sentido UFPE",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1005774,-34.9280712"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.148/",
			alt: "Câmera em Av. Dr. José Rufino - Sentido Av. Recife - Colégio Visão",
			info: "Av. Dr. José Rufino - Sentido Av. Recife - Colégio Visão",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.0846798,-34.928241"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.115/",
			alt: "Câmera em Marechal Mascarenhas de Moraes, Semáforo 530",
			info: "Av. Marechal Mascarenhas de Moraes, Semáforo 530",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1273685,-34.9155198"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.113/",
			alt: "Câmera em Mascarenhas de Moraes, Semáforo 531, sentido Aeroporto",
			info: "Av. Mascarenhas de Moraes, Semáforo 531, sentido Aeroporto",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1273685,-34.9155198"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.145/",
			alt: "Câmera em Norte Miguel Arraes de Alencar, Semáforo 043",
			info: "Av. Norte Miguel Arraes de Alencar, Semáforo 043",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.02776,-34.928"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.149/",
			alt: "Câmera em Norte Miguel Arraes de Alencar, Semáforo 043",
			info: "Av. Norte Miguel Arraes de Alencar, Semáforo 043",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.038574,-34.892"
		  },
		  {
			src: "http://transito.gtrans.com.br/cttupe/index.php/portal/getImg/192.168.11.116/",
			alt: "Câmera em Recife - Semáforo 336 - Sentido Aeroporto",
			info: "Av. Recife - Semáforo 336 - Sentido Aeroporto",
			mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.1003307,-34.9282209"
		  }
		]

        function updateCameras() {
            const grid = document.getElementById('camera-grid');
            grid.innerHTML = ''; // Limpar conteúdo existente

            cameraData.forEach(cam => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    <img src="${cam.src}?${new Date().getTime()}" alt="${cam.alt}" onclick="openModal('${cam.src}?${new Date().getTime()}', '${cam.alt}')">
                    <div class="info">${cam.info}</div>
                    <a href="${cam.mapUrl}" class="button" target="_blank">Ver no Google Maps</a>
                `;
                grid.appendChild(card);
            });
        }

        function openModal(imageSrc, altText) {
            const modal = document.getElementById('imageModal');
            const modalImage = document.getElementById('modalImage');
            modalImage.src = imageSrc;
            modalImage.alt = altText;
            modal.style.display = "flex"; // Exibir o modal
        }

        function closeModal() {
            const modal = document.getElementById('imageModal');
            modal.style.display = "none"; // Ocultar o modal
        }

        let countdownTime = 180; // 3 minutos em segundos
        const countdownDisplay = document.getElementById('countdown');

        function startCountdown() {
            updateCameras(); // Atualização inicial
            const interval = setInterval(() => {
                countdownTime--;
                if (countdownTime < 0) {
                    clearInterval(interval);
                    countdownTime = 180; // Resetar a contagem
                    updateCameras();
                }

                const minutes = Math.floor(countdownTime / 60);
                const seconds = countdownTime % 60;
                countdownDisplay.innerText = `Atualizando em: ${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
            }, 1000);
        }

        window.onload = startCountdown; // Iniciar contagem ao carregar a página
    </script>
</body>
</html>
