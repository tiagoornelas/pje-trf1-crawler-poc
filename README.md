# TRF1 Lawsuit Crawler (POC 2021)

> **Marco Histórico (Dezembro/2021)**: Este repositório registra o primeiro marco público na transição de carreira de Tiago Ornelas da advocacia para a engenharia de software, demonstrando a aplicação de automação e web scraping para resolver desafios reais do cotidiano forense.

---

## Contexto Histórico

Construído em dezembro de 2021, este projeto nasceu da necessidade prática de automatizar o acompanhamento de processos judiciais. Antes mesmo da transição formal para a área de tecnologia, o objetivo foi criar uma Prova de Conceito (POC) capaz de consultar e extrair movimentações processuais diretamente do Processo Judicial Eletrônico (PJe) da 1ª Região (TRF1).

O repositório é preservado em seu estado original como evidência técnica dessa trajetória, ilustrando os primeiros passos no desenvolvimento backend e na automação de processos.

---

## Visão Geral do Projeto

A aplicação consiste em uma API backend que recebe o número de um processo judicial e realiza raspagem de dados (*web scraping*) na consulta pública do TRF1, estruturando as informações retornadas em JSON.

Entre as informações capturadas estão:
- Órgão julgador e jurisdição
- Assunto processual
- Partes envolvidas no processo
- Histórico completo de andamentos processuais, com data, hora e descrição

---

## Escolhas Técnicas

Na época do desenvolvimento, a solução foi arquitetada utilizando o ecossistema Node.js:

- **Node.js & Express**: Servidor HTTP estruturado com roteamento REST, expondo a rota `GET /progress` para acionar a busca.
- **Puppeteer**: Automação de navegador *headless* para navegar pela interface JSF/RichFaces do PJe, preencher formulários de consulta, aguardar renderização dinâmica e extrair os dados do DOM.
- **Separação em Camadas**: Organização inicial desacoplando a recepção das requisições (`controller`) da automação de scraping e lógica de extração (`service`).
- **Resiliência a Instabilidades**: Tratamento de respostas para cenários frequentes de lentidão ou indisponibilidade dos servidores do tribunal (retornando `504 Gateway Timeout`).

---

## Evidências da Época

Registros visuais do funcionamento da POC em dezembro de 2021:

### Consulta com Sucesso
<img alt="Sucesso na captura de andamentos" src="https://i.ibb.co/vmmttcS/juridico-backend-2.jpg" />

### Tratamento de Indisponibilidade do PJe
<img alt="PJe fora do ar e mensagem tratada" src="https://i.ibb.co/vjfbMHF/juridico-backend-1.jpg" />

---

## Status do Repositório

Este projeto é um **arquivo histórico**. As interfaces dos tribunais e os sistemas de proteção do PJe evoluíram significativamente desde 2021, de modo que os seletores e fluxos originais não são ativamente mantidos. O código permanece público exclusivamente como registro de portfólio e aprendizado.

