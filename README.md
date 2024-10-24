# Guia de Testes Manuais - Cadastro de Parceiros

Este documento descreve os cenários de testes manuais para o cadastro de parceiros, utilizando técnicas como validação de campos obrigatórios, validação de limites e formatos de caracteres, e envio de formulários. Os cenários estão descritos em BDD com Gherkin, proporcionando clareza e padronização.

---

## Cenários de Testes
```bash
Feature: Campos obrigatórios no formulário de cadastro de parceiros
  Dado que esteja na página de cadastro de parceiros
  Quando não preencher os campos do formulário
  E clicar no botão "Próxima página"
  Então o sistema deve exibir mensagem dos campos obrigatórios

Feature: Validação de CNPJ inválido
  Dado que esteja na página de cadastro de parceiros
  Quando inserir um CNPJ inválido "123.456.78/0009-10"
  E clicar no botão "Próxima página"
  Então o sistema deve exibir uma mensagem de erro "CNPJ inválido"

Feature: Validação de limites de caracteres
  Dado que esteja na página de cadastro de parceiros
  Quando inserir de 1 a 100 caracteres nos campos Razão Social, Nome Fantasia e Site
  Então o sistema deve aceitar sem exibir erros
  E quando tentar inserir mais de 100 caracteres
  Então o sistema deve impedir a inserção de novos caracteres

Feature: Validação de URL inválida
  Dado que esteja na página de cadastro de parceiros
  Quando inserir uma URL inválida "exemplo-url.com.br"
  E clicar no botão "Próxima página"
  Então o sistema deve exibir uma mensagem de erro "Insira uma URL válida"

Feature: Validação de telefone comercial e WhatsApp
  Dado que esteja na página de cadastro de parceiros
  Quando inserir de 10 ou 11 caracteres numéricos nos campos Telefone Comercial e WhatsApp
  Então o sistema deve aceitar sem exibir erros
  E quando tentar inserir mais de 12 caracteres ou caracteres especiais
  Então o sistema deve impedir a inserção de novos caracteres ou exibir erro

Feature: Validação de CPF inválido
  Dado que esteja na página de cadastro de parceiros
  Quando inserir um CPF inválido com caracteres especiais ou fora do limite "123.456.789-10"
  E clicar no botão "Próxima página"
  Então o sistema deve exibir uma mensagem de erro "CPF inválido"

Feature: Validação de RG válido com letras e números
  Dado que esteja na página de cadastro de parceiros
  Quando inserir um RG válido com letras e números "26.711.209-X"
  E clicar no botão "Próxima página"
  Então o sistema deve aceitar sem exibir erros

Feature: Validação de e-mail inválido
  Dado que esteja na página de cadastro de parceiros
  Quando inserir um e-mail inválido "exemplo-email.com.br"
  E clicar no botão "Próxima página"
  Então o sistema deve exibir uma mensagem de erro "E-mail inválido"

Feature: Envio de formulário com dados válidos
  Dado que esteja na página de cadastro de parceiros
  E preencher os campos do formulário com dados válidos
  E clicar no botão "Próxima página"
  Quando acessar o formulário de dados do representante
  E clicar no botão de radio dos termos
  E preencher os formulários com dados válidos
  E clicar em enviar
  Então o sistema deve enviar o formulário com sucesso exibindo um alerta de que os dados serão analisados

```

### Execução dos Testes

Passos para execução dos testes

1. Acesse a página de cadastro de parceiros no sistema.
2. Preencha ou não preencha os campos conforme descrito em cada cenário.
3. Realize as ações de clicar no botão "Próxima página" ou outras ações descritas.
4. Verifique se o comportamento do sistema corresponde ao resultado esperado de cada cenário.

---

### Sugestão de melhoria: 
```bash
Como o campo Site é um campo obrigatorio seria bom ter uma validação 
via HTML, Javascript ou backend para o campo para exibir mensagem de erro quando inserido url invalida.
Para ficar mais intuitivo inserir um placeholder como exemplo
```
