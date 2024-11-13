<!--

Este arquivo HTML exibe um painel de câmeras de trânsito para Recife, Brasil. Inclui um layout em grade de feeds de câmeras de trânsito, um mapa do Google e um modal para visualização detalhada das imagens. A página também possui um temporizador de contagem regressiva que atualiza os feeds das câmeras a cada 3 minutos.

Componentes Principais:
- Estrutura HTML5 com design responsivo.
- CSS para estilizar o layout, incluindo uma grade para feeds de câmeras, modal para visualização de imagens e temporizador de contagem regressiva.
- JavaScript para atualizações dinâmicas de conteúdo, incluindo:
    - Busca e exibição de feeds de câmeras.
    - Abertura e fechamento do modal de imagem.
    - Temporizador de contagem regressiva para atualização dos feeds das câmeras.

Recursos Externos:
- API do Google Maps para incorporar um mapa.
- Windy.com para incorporar feeds de webcams.

Funções JavaScript:
- updateCameras(): Atualiza os feeds das câmeras exibidos na grade.
- openModal(imageSrc, altText): Abre o modal com a imagem selecionada.
- closeModal(): Fecha o modal de imagem.
- startCountdown(): Inicia o temporizador de contagem regressiva e atualiza os feeds das câmeras periodicamente.

Uso:
- A página inicia automaticamente a contagem regressiva e atualiza os feeds das câmeras ao carregar.
- Os usuários podem clicar nas imagens das câmeras para visualizá-las em um modal.
- Os usuários podem visualizar as localizações das câmeras no Google Maps clicando no botão fornecido.

Nota:
- Substitua 'YOUR_GOOGLE_MAPS_API_KEY' por uma chave de API válida do Google Maps.

Considerações:
- Este projeto foi desenvolvido por Washington Dias para ajudar na visualização das câmeras de trânsito da CTTU (Companhia de Trânsito e Transporte Urbano).
- As imagens das câmeras nem sempre atualizam em tempo real.
- Se você tiver sugestões ou melhorias para este projeto, sinta-se à vontade para contribuir.
-->

## Funcionalidades

- Busca e exibição de feeds de câmeras.
    - Abertura e fechamento do modal de imagem.
    - Temporizador de contagem regressiva para atualização dos feeds das câmeras.

## Recursos Externos

- API do Google Maps para incorporar um mapa.
- Windy.com para incorporar feeds de webcams.

## Funções JavaScript

- `updateCameras()`: Atualiza os feeds das câmeras exibidos na grade.
- `openModal(imageSrc, altText)`: Abre o modal com a imagem selecionada.
- `closeModal()`: Fecha o modal de imagem.
- `startCountdown()`: Inicia o temporizador de contagem regressiva e atualiza os feeds das câmeras periodicamente.

## Uso

- A página inicia automaticamente a contagem regressiva e atualiza os feeds das câmeras ao carregar.
- Os usuários podem clicar nas imagens das câmeras para visualizá-las em um modal.
- Os usuários podem visualizar as localizações das câmeras no Google Maps clicando no botão fornecido.

## Nota

- Substitua 'YOUR_GOOGLE_MAPS_API_KEY' por uma chave de API válida do Google Maps.

## Considerações

- Este projeto foi desenvolvido por Washington Dias para ajudar na visualização das câmeras de trânsito da CTTU.
- As imagens das câmeras nem sempre atualizam em tempo real.
- Se você tiver sugestões ou melhorias para este projeto, sinta-se à vontade para contribuir.