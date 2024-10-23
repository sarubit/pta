# PTA Server - Protocolo de Transferência de Arquivos

Este projeto implementa um servidor para o Protocolo de Transferência de Arquivos (PTA), um protocolo simples e didático para transferir arquivos entre clientes e servidores. Ele foi desenvolvido como parte de uma atividade prática voltada para o estudo de redes e comunicação entre sistemas.

## Estrutura do Projeto.

- `server.py`: Código do servidor PTA.
- `pta-server/`
  - `users.txt`: Contém a lista de usuários autorizados a se conectar ao servidor.
  - `files/`: Diretório contendo os arquivos que podem ser solicitados pelos clientes.
  

## Instruções para Executar o Servidor

### Requisitos

- Python 3.x
- Bibliotecas do Python: `socket`, `threading`, `os`

### Passos para Execução

1. **Clone o repositório**:
   ```bash
   git clone <URL do repositório>
   cd pta-server
   ```

2. **Certifique-se de que os arquivos estão no local correto**:
   - Coloque os arquivos que você deseja disponibilizar para os clientes dentro da pasta `files/`.
   - Certifique-se de que o arquivo `users.txt` contém os usuários autorizados (um por linha).
   - 
3. **Execute o Servidor**:
   
   Execute o servidor utilizando o seguinte comando:
   ```bash
   python server.py
   ```

   O servidor irá escutar na porta `11550` por padrão. Certifique-se de que esta porta está livre antes de executar o código.

4. **Conectando ao Servidor**:
5. 
   Use um cliente compatível com o protocolo PTA (ex: `pta-client.py`). O cliente deve seguir o protocolo PTA para se autenticar, listar e requisitar arquivos do servidor.

## Formato das Mensagens

O servidor responde aos seguintes comandos:

- **CUMP**: Utilizado para autenticação. O cliente deve enviar um nome de usuário, e o servidor responde com `OK` (se o usuário for válido) ou `NOK` (se for inválido).
- **LIST**: Requisição de listagem de arquivos. O servidor responde com a lista dos arquivos disponíveis no diretório `files/`.
- **PEGA [arquivo]**: Solicita a transferência de um arquivo específico. O servidor envia o arquivo ou responde com `NOK` se o arquivo não for encontrado.
- **TERM**: Solicita a terminação da sessão. O servidor encerra a conexão com o cliente após enviar a resposta `OK`;

## Considerações

- Se a autenticação falhar, o servidor encerra a conexão automaticamente.
- Todas as mensagens entre cliente e servidor são trocadas em formato ASCII.
- Utilize o cliente PTA fornecido para testar as funcionalidades do servidor (`pta-client.py`), que simula as requisições e respostas esperadas.


