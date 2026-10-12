# DIO - Trilha .NET - Banco de Dados
> Desafio de Projeto | [DIO (Digital Innovation One)](https://www.dio.me)

---

## 📌 Visão Geral do Desafio

Para este desafio, você precisará aplicar os conhecimentos adquiridos no módulo de **Banco de Dados** da trilha **.NET** da DIO.

### 🎬 Contexto
Você é responsável pelo banco de dados de um site de filmes, onde estão armazenadas informações completas sobre as obras e seus respectivos atores. Seu papel é construir consultas SQL para extrair relatórios e dados estruturados para análise.

---

## 🗄️ Modelagem do Banco de Dados

O banco de dados é composto por 5 tabelas interligadas:

<p align="center">
  <img src="Imagens/diagrama.png" alt="Diagrama Banco de Dados" width="700px" />
</p>

### 📋 Descrição das Tabelas

| Tabela | Descrição |
| :--- | :--- |
| **`Filmes`** | Armazena informações dos filmes (nome, ano e duração). |
| **`Atores`** | Armazena dados dos atores (primeiro nome, último nome e gênero). |
| **`Generos`** | Armazena os gêneros cinematográficos disponíveis. |
| **`ElencoFilme`** | Relacionamento *muitos-para-muitos* entre **Filmes** e **Atores**, especificando o papel/personagem. |
| **`FilmesGenero`** | Relacionamento *muitos-para-muitos* entre **Filmes** e **Gêneros**. |

---

## ⚙️ Preparando o Banco de Dados (PostgreSQL / pgAdmin)

> [!IMPORTANT]
> **Atenção — Migração de SQL Server para PostgreSQL:**  
> O script original do desafio foi projetado para **SQL Server**, mas neste projeto ele foi **convertido e adaptado para PostgreSQL** no arquivo [`Script Filmes.sql`](Script%20Filmes.sql).

> [!WARNING]
> **Execução no pgAdmin:**  
> No **pgAdmin / PostgreSQL**, comandos para criar banco de dados (`CREATE DATABASE`) não podem ser executados dentro de transações comuns no painel de scripts. Portanto, siga o passo a passo abaixo:
>
> 1. **Crie o Banco Manualmente:**
>    - Abra o **pgAdmin**.
>    - Conecte ao seu servidor PostgreSQL.
>    - Clique com o botão direito em **Databases** ➡️ **Create** ➡️ **Database...**.
>    - Defina o nome como `Filmes` (ou de sua preferência) e clique em **Save**.
>
> 2. **Abra o Query Tool no Banco Criado:**
>    - Selecione o banco de dados `Filmes` recém-criado na árvore lateral.
>    - Abra o console de consultas clicando em **Tools** ➡️ **Query Tool** (ou botão direito no banco ➡️ **Query Tool**).
>
> 3. **Execute o Script de Criação e Carga:**
>    - Carregue ou copie todo o conteúdo do arquivo [`Script Filmes.sql`](Script%20Filmes.sql).
>    - Execute o script (**F5** ou botão de *Play*).  
>    *As tabelas e todos os dados de teste serão criados com sucesso.*

---

## 🎯 Proposta e Consultas Solicitadas

Você deverá criar **12 consultas SQL** para retornar os dados conforme as especificações e imagens de resultado esperado abaixo:

---

### 1. Buscar o nome e ano dos filmes
![Exercicio 1](Imagens/1.png)

---

### 2. Buscar o nome e ano dos filmes, ordenados por ordem crescente pelo ano
![Exercicio 2](Imagens/2.png)

---

### 3. Buscar pelo filme "De Volta para o Futuro", trazendo nome, ano e a duração
![Exercicio 3](Imagens/3.png)

---

### 4. Buscar os filmes lançados em 1997
![Exercicio 4](Imagens/4.png)

---

### 5. Buscar os filmes lançados APÓS o ano 2000
![Exercicio 5](Imagens/5.png)

---

### 6. Buscar os filmes com a duração maior que 100 e menor que 150, ordenando pela duração em ordem crescente
![Exercicio 6](Imagens/6.png)

---

### 7. Buscar a quantidade de filmes lançados no ano, agrupando por ano e ordenando pela quantidade/duração em ordem decrescente
![Exercicio 7](Imagens/7.png)

---

### 8. Buscar os atores do gênero masculino, retornando PrimeiroNome e UltimoNome
![Exercicio 8](Imagens/8.png)

---

### 9. Buscar os atores do gênero feminino, retornando PrimeiroNome, UltimoNome e ordenando pelo PrimeiroNome
![Exercicio 9](Imagens/9.png)

---

### 10. Buscar o nome do filme e o gênero
![Exercicio 10](Imagens/10.png)

---

### 11. Buscar o nome do filme e o gênero do tipo "Mistério"
![Exercicio 11](Imagens/11.png)

---

### 12. Buscar o nome do filme e os atores, trazendo PrimeiroNome, UltimoNome e seu Papel
![Exercicio 12](Imagens/12.png)
