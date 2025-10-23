## Exemplo de ingestão da API de Posições da SPTrans


1) Clonar o projeto:
```
   git clone https://github.com/guilhermepepa/Exemplo-Ingestao.git
```

3) Após clonar, acessar o diretório do projeto onde está o docker-compose.yaml ("../Exemplo-Ingestao/") e executar o comando:
```
   docker compose up -d
```

3) Acessar o NiFi em https://127.0.0.1:9443/nifi/login (User:exemploingestao / Pwd:exemploingestao)
   
    - Escolher a opção "Upload Template" que está dentro da opção Operate e selecionar o template que está no diretório "/nifi-templates";

    - Clicar com o botão direito no process group "ingestao-sptrans" e escolher a opção "Configure";

    - Acessar aba "Controller Services". Nas propriedades do AWSCredentialsProviderControllerSerivce, editar o "Access Key ID" e o "Secret Access Key" do MinIO que estão no docker-compose.yaml (Access Key ID:exemploingestao / Secret Access Key:exemploingestao);

    - Habilitar o AWSCredentialsProviderControllerService;

    - Clicar com o botão direito no process group "ingestao-sptrans" e escolher a opção "Variables";

    - Adicionar o Token da SPTrans na variável "sptrans.api.token";

    - Clicar com o botão direito no process group "ingestao-sptrans" e escolher a opção Start.



4) Acessar o MinIO em http://127.0.0.1:9001 (User:exemploingestao / Pwd:exemploingestao)
   
   - Acessar o bucket "bronze". Os arquivos estarão em "bronze/sptrans/posicao/", particionados por ano/mes/dia/hora.
