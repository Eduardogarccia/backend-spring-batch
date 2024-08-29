# SpringBatch (inserindo arquivo CNAB no banco H2)

Esse BackEnd usa o SpringBatch para fazer upload de dados de um arquivo do tipo CNAB no banco de dados H2. Nesse projeto é garantida a unicidade dos uploads, não sendo possível enviar dois arquivos de mesmo nome.

## Requisitos

- **Java 17**
- **IDE STS (Spring Tool Suite)**

## Primeiros Passos

### 1. Clonar o Repositório

Clone o repositório ou baixe o arquivo ZIP do projeto e descompacte-o no seu workspace da IDE STS:

```bash
git clone https://github.com/Eduardogarccia/backend-spring-batch.git
```

## 2. Iniciar a Aplicação

Abra a IDE STS, importe o projeto e inicie a aplicação com a opção **Run As Spring Boot App**.

## 3. Testar

Agora que o backend está rodando, você pode testar as funcionalidades pelo seu Terminal ou Postman (aconselho usar o terminal).
No projeto há 3 arquivos que podem ser testados, nomeados como: "QNAB-5.text", "QNAB-6.text" e "QNAB-7.text"

PELO TERMINAL:
No seu terminal, abra o caminho em que o prejeto se encontra:
 ```bash
    cd C:\Caminho\Para\O\Projeto\backend
    ```
Entre na pasta de files:
 ```bash
    cd files
    ```
Para inserir um dos arquivos insira o seguinte comando (inserindo o CNAB-5.txt por exemplo):
 ```bash
    C:\Caminho\Para\O\Projeto\backend\files curl -X POST -F "file=@CNAB-5.txt" http://localhost:8080/cnab/upload
    ```
Agora deve ter aparecido a mensagem: "Processamento iniciado!"

Abra o console do H2 e veja a tabela transacoes:
No seu navegador abra http://localhost:8080/h2-console
Verifique se a JDBC URL está correta: jdbc:h2:file:./data/db

Agora você ja pode ver os dados na tabela transações.

PELO POSTMAN:
Abra o Postman e defina um método http POST com a seguinte url: http://localhost:8080/cnab/upload

No body selecione a opção form-data.
No campo key digite "file".
À direita do campo Key, há um menu dropdown que, por padrão, está definido como "Text". Clique nele e selecione File.
Agora, um botão Select Files aparecerá no campo Value. Clique nesse botão e selecione o arquivo CNAB-5.txt (por exemplo) seguindo o caminho de onde está o projeto, na pasta "files".
Após configurar a requisição, clique no botão Send.
No painel de resposta do Postman, você deverá ver a resposta que a sua API retorna, que no seu caso deve ser "Processamento iniciado!".

Abra o console do H2 e veja a tabela transacoes:
No seu navegador abra http://localhost:8080/h2-console
Verifique se a JDBC URL está correta: jdbc:h2:file:./data/db

Agora você ja pode ver os dados na tabela transações.



