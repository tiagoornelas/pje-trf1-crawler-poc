# pje-trf1-crawler-poc

Prova de conceito (POC) de crawler para obtenção de andamentos processuais feita para TRF1 / PJe em dezembro de 2021 para fins de estudo e prova de conceito.

## Métodos Disponíveis

### API HTTP

#### `GET /progress`
Consulta os dados e andamentos do processo informado.

- **Payload (`application/json`)**:
  ```json
  {
    "lawsuit": "1000827-11.2020.4.01.3821"
  }
  ```

- **Resposta de sucesso (`200 OK`)**:
  ```json
  {
    "court": "TRF-1",
    "lawsuit": "1000827-11.2020.4.01.3821",
    "jurisdiction": "string",
    "subject": "string",
    "suitors": "string",
    "progress": [
      {
        "date": "DD/MM/AAAA",
        "time": "HH:MM:SS",
        "progress": "string"
      }
    ]
  }
  ```

- **Resposta de erro (`504 Gateway Timeout`)**:
  Retornada em caso de lentidão, erro ou indisponibilidade no portal do tribunal.

### Módulo Interno

- **`service/progress.js`**:
  - `getLawsuitTRF1(lawsuit)`: função assíncrona que inicializa o Puppeteer, acessa a consulta pública do TRF1/PJe, preenche o número do processo, navega aos detalhes e retorna o objeto estruturado com os dados e andamentos.


