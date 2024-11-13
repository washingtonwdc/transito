# Câmeras de Trânsito - Recife

Este projeto exibe um painel de câmeras de trânsito para Recife, Brasil. Inclui um layout em grade de feeds de câmeras de trânsito, um mapa do Google e um modal para visualização detalhada das imagens. A página também possui um temporizador de contagem regressiva que atualiza os feeds das câmeras a cada 3 minutos.

## Componentes Principais:
- Estrutura HTML5 com design responsivo.
- CSS para estilizar o layout, incluindo uma grade para feeds de câmeras, modal para visualização de imagens e temporizador de contagem regressiva.
- JavaScript para atualizações dinâmicas de conteúdo, incluindo:
    - Busca e exibição de feeds de câmeras.
    - Abertura e fechamento do modal de imagem.
    - Temporizador de contagem regressiva para atualização dos feeds das câmeras.

## Recursos Externos:
- API do Google Maps para incorporar um mapa.
- Windy.com para incorporar feeds de webcams.

## Funções JavaScript:
- `updateCameras()`: Atualiza os feeds das câmeras exibidos na grade.
- `openModal(imageSrc, altText)`: Abre o modal com a imagem selecionada.
- `closeModal()`: Fecha o modal de imagem.
- `startCountdown()`: Inicia o temporizador de contagem regressiva e atualiza os feeds das câmeras periodicamente.

## Uso:
- A página inicia automaticamente a contagem regressiva e atualiza os feeds das câmeras ao carregar.
- Os usuários podem clicar nas imagens das câmeras para visualizá-las em um modal.
- Os usuários podem visualizar as localizações das câmeras no Google Maps clicando no botão fornecido.

## Nota:
- Substitua `'YOUR_GOOGLE_MAPS_API_KEY'` por uma chave de API válida do Google Maps.

## Considerações

- Este projeto foi desenvolvido por Washington Dias para ajudar na visualização das câmeras de trânsito da CTTU.
- As imagens das câmeras nem sempre atualizam em tempo real.
- Se você tiver sugestões ou melhorias para este projeto, sinta-se à vontade para contribuir.

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
        }
        header {
            background-color: #007BFF;
            color: white;
            padding: 20px;
            text-align: center;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }
        main {
            padding: 80px 20px 20px 20px;
        }
        h1 {
            margin: 0;
        }
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        .card {
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            text-align: center;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .card:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
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
            background-color: #007BFF;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <header>
        <h1>Câmeras de Trânsito - Recife</h1>
    </header>
    <main>
        <div class="grid">
            <!-- Conteúdo das câmeras de trânsito -->
            <div class="card">
                <img src="images/camera1.jpg" alt="Câmera 1">
                <div class="info">Câmera 1 - Localização</div>
                <button class="button">Ver ao vivo</button>
            </div>
            <div class="card">
                <img src="images/camera2.jpg" alt="Câmera 2">
                <div class="info">Câmera 2 - Localização</div>
                <button class="button">Ver ao vivo</button>
            </div>
            <!-- Adicione mais cards conforme necessário -->
        </div>
    </main>
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
                info: "Recife x Rua Jean Emile Favre",
                mapUrl: "https://www.google.com/maps/search/?api=1&query=-8.063417,-34.873583"
            }
        ];

        const grid = document.querySelector('.grid');
        cameraData.forEach(camera => {
            const card = document.createElement('div');
            card.className = 'card';
            card.innerHTML = `
                <img src="${camera.src}" alt="${camera.alt}">
                <div class="info">${camera.info}</div>
                <a href="${camera.mapUrl}" target="_blank" class="button">Ver no mapa</a>
            `;
            grid.appendChild(card);
        });
    </script>
</body>
</html>