# Alunos:
Gustavo Henrique, Ícaro Botelho, Maruan Biasi, Rafael Pereira, Ricardo Falção

# Descrição geral do produto/protótipo
O SMEE é um protótipo IoT que coleta dados de tensão, corrente e potência, transmitindo-os via ESP32 e rede Wi-Fi para um servidor central. Os dados são processados em Node-RED, armazenados em InfluxDB e exibidos em dashboards Grafana, com possibilidade de relatórios e alertas configuráveis.

# Contexto para Produto/Protótipo

O CamarVolt será constituído por dois elementos principais: o aparelho adaptador de tomada inteligente e o servidor de processamento e visualização de dados.

## Ambiente de uso

O aparelho será instalado diretamente em tomadas padrão brasileiro (2P+T), funcionando como um adaptador entre a tomada da parede e o dispositivo conectado.
O protótipo foi projetado para uso em residências, onde o monitoramento de consumo de energia elétrica é relevante.

## Usuários

Residenciais: moradores que desejam acompanhar e reduzir gastos de energia.

## Fluxo de interação

O aparelho adaptador coleta informações de corrente elétrica através do sensor ZMCT103C, processa localmente com o módulo Wemos ESP8266 e transmite os dados via rede Wi-Fi.
Os dados são enviados de forma segura para o servidor central, que pode estar hospedado localmente em um computador ou em uma plataforma em nuvem (AWS, Azure, Oracle, etc.).
O servidor recebe os dados, armazena-os em um banco de dados e processa os valores de consumo.
O dashboard web permite que os usuários visualizem consumo em tempo real, relatórios históricos e valores calculados de custo de energia.
Presets regionais (como tarifa de energia elétrica em Joinville) podem ser utilizados, além de valores customizados fornecidos pelo usuário.

## Restrições físicas e de design

O adaptador não deve ultrapassar 10 cm em profundidade nem 5 cm em largura/altura em relação à tomada.
O aparelho deve ser visualmente semelhante a adaptadores tradicionais, não podendo conter aparência ofensiva.
Materiais e design devem reduzir risco de fogo e evitar choques elétricos.

## Plataformas de desenvolvimento

Para prototipagem, serão utilizados equipamentos de soldagem, protoboard, cabos jumper e ferramentas de programação (ex.: VSCode + NodeJS).
O firmware será gravado no ESP8266 através de cabo USB e ambiente de desenvolvimento compatível (Arduino IDE ou PlatformIO).

## Segurança e confiabilidade

A comunicação entre aparelho e servidor deve ser criptografada.
O servidor deve tratar múltiplos dispositivos simultaneamente, sem perda ou desintegração de dados.
Tanto o aparelho quanto o servidor devem operar continuamente, utilizando apenas energia fornecida pela tomada (no caso do aparelho).


# Requisitos do Produto - Item 4 do Template

## Requisitos Funcionais (RF)

- RF01: Medir tensão, corrente, potência e fator de potência a cada 10 segundos.

- RF02: Calcular e armazenar o consumo total em kWh.

- RF03: Exibir gráficos e relatórios no dashboard.

- RF04: Gerar alertas em caso de sobrecarga ou consumo anormal.

- RF05: Permitir exportação dos dados em CSV/JSON.

- RF06: Conectar-se a redes Wi-Fi disponíveis.

- RF07: Enviar dados de consumo para o servidor central em tempo real.

- RF08: Calcular valores de gasto em energia elétrica a partir de custos inseridos pelo usuário.

- RF09: Oferecer presets de custo de energia elétrica (ex.: tarifa padrão de uma cidade).

- RF10: Medir correntes de até 30 amperes no máximo.

## Requisitos Não Funcionais (RNF)

- RNF01: O sistema deve ter disponibilidade mínima de 99%.

- RNF02: O tempo de resposta dos dados deve ser inferior a 5 segundos.

- RNF03: Todos os dados transmitidos devem ser criptografados (TLS).

- RNF04: O sistema deve armazenar dados históricos por pelo menos 12 meses.

- RNF05: O dispositivo não deve exceder 10 cm de protrusão da tomada (em ângulo reto).

- RNF06: O dispositivo não deve exceder 5 cm de protrusão nas direções paralelas à tomada.

- RNF07: O design deve inibir ou reduzir risco de incêndio e choques elétricos.

- RNF08: O dispositivo não pode ter aparência ofensiva nem nomes inadequados.

## Requisitos de Hardware

- Sensore de corrente: AC 30A SCT-013-030 Não Invasivo

- Módulo medidor de energia PZEM-004T.

- Microcontrolador ESP32 ou Wemos ESP8266 (CH340G).

- Fonte de alimentação estabilizada 5V 1A.

- Diodo de proteção.

- Protoboard para prototipação.

- Fios diversos e cabos jumper (macho-macho, macho-fêmea, fêmea-fêmea).

- Equipamentos de soldagem (ferro de solda, estanho, suporte com garras, EPI de segurança).

## Requisitos de Software

- Firmware em C++ (Arduino IDE / ESP-IDF).

- Node JS (processamento de dados e interface).

## Requisitos de Plataforma (IoT)

- Mesa para prototipação.

- Tomada elétrica padrão brasileiro (2P+T).

- Computador com acesso a IDE de programação (Arduino IDE / VSCode).

- Cabo USB para gravação do firmware.

- Ambiente de desenvolvimento com Node.js e VSCode.

## Requisitos de Plataforma (Servidor)

- Computador local dedicado ou instância em nuvem (AWS, Azure, Oracle, etc.).

![requisitos](https://github.com/user-attachments/assets/e8cccc82-b551-4a7a-985f-19a88cd01d66)

![usecase](https://github.com/user-attachments/assets/b1df7a44-57b3-40e4-b041-5c83a6741fe9)

<img width="721" height="451" alt="Diagrama sem nome drawio" src="https://github.com/user-attachments/assets/2d797ffc-6b43-4281-a80d-e05068ba3b38" />

