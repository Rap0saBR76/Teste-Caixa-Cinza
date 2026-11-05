
# 🧪 Projeto de Testes Caixa Cinza – API de Autenticação Supabase

**Disciplina:** Testes de Software  
**Projeto:** Testes Caixa Cinza em API de Autenticação  
**Ferramentas:** Supabase, Postman Desktop e GitHub  
**Repositório:** Teste-Caixa-Cinza

---

# 1. Introdução

Este projeto apresenta a realização de testes de caixa cinza em uma API de autenticação utilizando a plataforma Supabase e a ferramenta Postman Desktop.

Os testes foram realizados com o objetivo de verificar o funcionamento da autenticação de usuários, analisando requisições HTTP, códigos de resposta, mensagens de erro e retorno de dados em formato JSON.

A metodologia de caixa cinza foi utilizada porque permite testar o comportamento externo da API considerando também conhecimentos parciais de sua estrutura interna, como endpoints, autenticação, headers e parâmetros enviados.

# 2. Objetivo da Atividade

O objetivo desta atividade é compreender e aplicar testes de caixa cinza em APIs de autenticação.

Durante o desenvolvimento foram realizadas as seguintes atividades:

- Criação e configuração de um projeto no Supabase.
- Configuração da autenticação por e-mail e senha.
- Criação de usuário para testes.
- Configuração de ambiente no Postman.
- Criação de requisições HTTP.
- Execução de cinco cenários de testes.
- Validação de respostas HTTP e mensagens de erro.
- Registro dos resultados obtidos.
- Documentação das evidências no GitHub.

# 3. Configuração do Supabase

## 3.1 Criação do projeto

Inicialmente, foi criada uma conta na plataforma Supabase e, em seguida, um novo projeto chamado **Testes Caixa Cinza**.

O projeto foi configurado para disponibilizar os recursos necessários à realização dos testes de autenticação.

O Supabase foi utilizado como backend responsável pelo gerenciamento dos usuários e pelo processamento das solicitações de login.

## 3.2 Tipo de autenticação utilizada

Foi utilizada a autenticação por e-mail e senha, disponibilizada pelo Supabase Auth.

Esse método permite que usuários realizem login informando suas credenciais cadastradas.

## 3.3 Criação do usuário

Foi criado um usuário de teste por meio do painel de autenticação do Supabase.

Esse usuário foi utilizado para realizar o cenário de login válido no Postman.

Também foram utilizados dados inválidos e inexistentes para verificar o comportamento da API diante de diferentes situações.

## 3.4 Objetivo da configuração

A configuração do Supabase teve como finalidade disponibilizar uma API funcional para receber requisições de autenticação e permitir a execução dos testes propostos na atividade.

## 3.5 Evidências

As evidências desta etapa estão organizadas na pasta `prints/`.

- Projeto criado no Supabase.
- Painel do projeto.
- Configuração de autenticação.
- Usuário cadastrado.
- Configurações e credenciais da API.

# 4. Configuração do Postman

## 4.1 Criação do Workspace

Foi criado um Workspace no Postman Desktop com o nome **Testes Caixa Cinza**, destinado à organização das requisições e dos testes realizados durante a atividade.

O Workspace permite centralizar as requisições utilizadas e facilitar a organização do processo de validação.

## 4.2 Configuração do Environment

Foi criado um Environment chamado **Supabase - Testes**.

Nesse ambiente foram configuradas as variáveis necessárias para executar as requisições sem precisar informar manualmente os dados em cada teste.

## 4.3 Variáveis configuradas

| Variável | Descrição |
|---|---|
| base_url | URL principal da API Supabase |
| api_key | Chave de acesso da API |
| email | E-mail do usuário de teste |
| password | Senha do usuário de teste |

As variáveis permitem reutilizar informações nas requisições, facilitando a execução e a manutenção dos testes.

Por segurança, as credenciais reais não são disponibilizadas neste repositório.

## 4.4 Utilização do Postman

O Postman foi utilizado para enviar requisições HTTP ao endpoint de autenticação do Supabase.

Por meio da ferramenta foi possível:

- Configurar métodos HTTP.
- Informar os headers.
- Enviar dados em formato JSON.
- Executar os cenários de teste.
- Analisar os códigos de resposta.
- Verificar mensagens de erro.
- Validar o retorno de um token de autenticação.

# 5. Configuração das Requisições

## 5.1 Endpoint utilizado

Foi utilizada a seguinte rota de autenticação:

`{{base_url}}/auth/v1/token?grant_type=password`

## 5.2 Método HTTP

**POST**

O método POST foi utilizado para enviar as credenciais do usuário à API e solicitar a autenticação.

## 5.3 Headers utilizados

| Header | Valor |
|---|---|
| apikey | {{api_key}} |
| Content-Type | application/json |
| Authorization | Bearer {{api_key}} |

A chave da API foi utilizada para identificar e autorizar o acesso ao serviço Supabase.

O Content-Type informa que os dados enviados estão no formato JSON.

O header Authorization foi configurado conforme a requisição utilizada no Postman. A chave utilizada deve ser a chave pública apropriada do projeto, nunca a chave secreta `service_role`.

## 5.4 Body JSON

O corpo da requisição foi configurado no formato JSON, contendo os campos de e-mail e senha.

Exemplo:

```json
{
  "email": "{{email}}",
  "password": "{{password}}"
}
```

## 5.5 Finalidade da requisição

A requisição tem como finalidade verificar se as credenciais informadas correspondem a um usuário cadastrado no Supabase.

Quando as informações estão corretas, a API retorna uma resposta de sucesso contendo informações de autenticação, incluindo o access token.

Quando as informações são inválidas ou estão ausentes, a API retorna mensagens de erro correspondentes à situação identificada.

## 5.6 Evidências

- Endpoint configurado.
- Método POST selecionado.
- Headers configurados.
- Body JSON preenchido.
- Requisição criada no Postman.

# 6. Execução dos Testes Caixa Cinza

Foram executados cinco cenários de testes para verificar diferentes comportamentos da API de autenticação.

Os testes foram realizados diretamente no Postman Desktop, utilizando o endpoint de autenticação do Supabase.

## 6.1 TC01 – Login válido

**Objetivo:** Verificar se a API permite a autenticação de um usuário cadastrado com credenciais corretas.

**Entrada utilizada:**
- E-mail válido cadastrado.
- Senha correta.

**Resultado esperado:**
- Status HTTP 200 OK.
- Retorno de um access token.
- Autenticação realizada com sucesso.

**Resultado obtido:**

A API retornou o status HTTP 200 OK, disponibilizando um token de acesso e informações do usuário autenticado.

**Status:** APROVADO.

## 6.2 TC02 – Senha incorreta

**Objetivo:** Verificar se a API impede o acesso quando o usuário informa uma senha incorreta.

**Entrada utilizada:**
- E-mail do usuário de teste.
- Senha incorreta.

**Resultado esperado:**
- Status HTTP 400 Bad Request.
- Mensagem de erro de autenticação.
- Nenhum token de acesso válido deve ser disponibilizado.

**Resultado obtido:**

A API retornou:

```json
{
  "code": 400,
  "error_code": "invalid_credentials",
  "msg": "Invalid login credentials"
}
```

**Status:** APROVADO.

## 6.3 TC03 – Usuário inexistente

**Objetivo:** Verificar o comportamento da API quando é informado um e-mail que não está cadastrado no sistema.

**Entrada utilizada:**
- E-mail inexistente.
- Senha informada para o teste.

**Resultado esperado:**
- Status HTTP 400 Bad Request.
- Mensagem indicando credenciais inválidas.
- Acesso negado.

**Resultado obtido:**

A API retornou:

```json
{
  "code": 400,
  "error_code": "invalid_credentials",
  "msg": "Invalid login credentials"
}
```

**Status:** APROVADO.

## 6.4 TC04 – Campos vazios

**Objetivo:** Verificar se a API identifica a ausência de informações obrigatórias no processo de autenticação.

**Entrada utilizada:**
- E-mail vazio.
- Senha vazia.

**Resultado esperado:**
- Status HTTP 400 Bad Request.
- Mensagem de validação.
- Autenticação não realizada.

**Resultado obtido:**

A API retornou:

```json
{
  "code": 400,
  "error_code": "validation_failed",
  "msg": "missing email or phone"
}
```

**Status:** APROVADO.

## 6.5 TC05 – Credenciais inválidas

**Objetivo:** Verificar se a API rejeita informações de autenticação em formato inválido.

**Entrada utilizada:**
- E-mail em formato inválido.
- Senha inválida.

**Resultado esperado:**
- Status HTTP 400 Bad Request.
- Mensagem de erro.
- Acesso negado.

**Resultado obtido:**

A API retornou:

```json
{
  "code": 400,
  "error_code": "invalid_credentials",
  "msg": "Invalid login credentials"
}
```

**Status:** APROVADO.

# 7. Registro dos Testes

Os testes realizados foram registrados por meio de uma planilha de controle, contendo informações sobre cada cenário executado.

O registro permite acompanhar as entradas utilizadas, os resultados esperados, os resultados obtidos e a situação de cada teste.

## 7.1 Tabela de cenários

| ID | Cenário | Entrada utilizada | Resultado esperado | Resultado obtido | Status |
|---|---|---|---|---|---|
| TC01 | Login válido | E-mail e senha corretos | HTTP 200 + token | HTTP 200 + access token | APROVADO |
| TC02 | Senha incorreta | Senha inválida | Erro de autenticação | HTTP 400 - invalid_credentials | APROVADO |
| TC03 | Usuário inexistente | E-mail não cadastrado | Acesso negado | HTTP 400 - invalid_credentials | APROVADO |
| TC04 | Campos vazios | E-mail e senha vazios | Erro de validação | HTTP 400 - validation_failed | APROVADO |
| TC05 | Credenciais inválidas | E-mail malformado e senha inválida | Mensagem de erro | HTTP 400 - invalid_credentials | APROVADO |

## 7.2 Importância da documentação

A documentação dos testes é importante porque permite acompanhar os resultados, identificar falhas e comprovar o comportamento da aplicação diante de diferentes situações.

Também facilita a reprodução dos testes e a identificação de possíveis problemas durante futuras manutenções.

## 7.3 Falhas identificadas

Durante os testes foram observados diferentes retornos de erro:

- `invalid_credentials`: apresentado quando as credenciais não permitem a autenticação.
- `validation_failed`: apresentado quando os campos obrigatórios não foram informados.

Esses retornos demonstram que a API realiza validações e impede tentativas de autenticação com dados incorretos ou incompletos.

# 8. Resultados Obtidos

Após a execução dos cinco cenários, foram observados os seguintes resultados:

- O login com credenciais válidas foi realizado com sucesso.
- A API retornou um access token no cenário de autenticação válida.
- A senha incorreta foi rejeitada.
- O usuário inexistente não conseguiu acessar o sistema.
- Os campos vazios foram identificados pela validação da API.
- As credenciais inválidas foram rejeitadas.

## 8.1 Resumo dos resultados

| Indicador | Resultado |
|---|---|
| Total de testes executados | 5 |
| Testes aprovados | 5 |
| Testes reprovados | 0 |
| Testes com resposta HTTP 200 | 1 |
| Testes com resposta HTTP 400 | 4 |

Os resultados demonstraram que a API apresentou o comportamento esperado nos cinco cenários avaliados.

---

# 9. Conclusão

A realização desta atividade permitiu compreender na prática como funcionam os testes de caixa cinza aplicados a uma API de autenticação.

Durante o desenvolvimento foi possível configurar um ambiente no Supabase, criar um usuário de teste, configurar requisições HTTP no Postman e validar diferentes situações relacionadas ao processo de login.

Os cinco cenários foram executados e apresentaram os comportamentos esperados.

A autenticação funcionou corretamente para o usuário cadastrado, retornando o status HTTP 200 OK e um access token.

Nos cenários negativos, a API identificou as informações incorretas ou ausentes e retornou os respectivos códigos e mensagens de erro.

Uma das dificuldades encontradas foi compreender os diferentes retornos HTTP e identificar as mensagens apresentadas pela API durante as tentativas de autenticação inválidas.

Como melhorias futuras, poderiam ser implementados testes automatizados, validações adicionais, testes de segurança e novos cenários de autenticação.

Conclui-se que os testes de caixa cinza são importantes para verificar a confiabilidade, a segurança e o comportamento de APIs, permitindo identificar problemas antes que afetem os usuários finais.
