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
<img src="Imagens/1.png" alt="Exercicio 1" width="90%" />

> **Resposta:**
> ```sql
> SELECT nome as "Nome", ano as "Ano" 
> FROM filmes;
>
> ```

---

### 2. Buscar o nome e ano dos filmes, ordenados por ordem crescente pelo ano
<img src="Imagens/2.png" alt="Exercicio 2" width="90%" />

> **Resposta:**
> ```sql
> SELECT nome as "Nome", ano as "Ano", duracao as "Duração" 
> FROM filmes 
> ORDER BY ano, duracao;
>
> ```

---

### 3. Buscar pelo filme "De Volta para o Futuro", trazendo nome, ano e a duração
<img src="Imagens/3.png" alt="Exercicio 3" width="90%" />

> **Resposta:**
> ```sql
> SELECT nome as "Nome", ano as "Ano", duracao as "Duração" 
> FROM filmes 
> WHERE nome='De Volta para o Futuro';
> 
> ```

---

### 4. Buscar os filmes lançados em 1997
<img src="Imagens/4.png" alt="Exercicio 4" width="90%" />

> **Resposta:**
> ```sql
> SELECT nome as "Nome", ano as "Ano", duracao as "Duração" 
> FROM filmes 
> WHERE ano=1997;
>
> ```

---

### 5. Buscar os filmes lançados APÓS o ano 2000
<img src="Imagens/5.png" alt="Exercicio 5" width="90%" />

> **Resposta:**
> ```sql
> SELECT nome as "Nome", ano as "Ano", duracao as "Duração" 
> FROM filmes 
> WHERE ano > 2000;
>
> ```

---

### 6. Buscar os filmes com a duração maior que 100 e menor que 150, ordenando pela duração em ordem crescente
<img src="Imagens/6.png" alt="Exercicio 6" width="90%" />

> **Resposta:**
> ```sql
> SELECT nome as "Nome", ano as "Ano", duracao as "Duração" 
> FROM filmes
> WHERE duracao > 100 AND duracao < 150
> ORDER BY duracao;
>
> ```

---

### 7. Buscar a quantidade de filmes lançados no ano, agrupando por ano e ordenando pela quantidade/duração em ordem decrescente
<img src="Imagens/7.png" alt="Exercicio 7" width="90%" />

> **Resposta:**
> ```sql
> SELECT ano as "Ano", COUNT(ano) as "Quantidade" 
> FROM filmes
> GROUP BY ano
> ORDER BY "Quantidade" DESC;
> 
> ```

---

### 8. Buscar os atores do gênero masculino, retornando PrimeiroNome e UltimoNome
<img src="Imagens/8.png" alt="Exercicio 8" width="90%" />

> **Resposta:**
> ```sql
> SELECT 
>     primeironome as "Primeiro Nome", 
>     ultimonome "Ultimo Nome", 
>     genero as "Genero"
> FROM atores
> WHERE genero = 'M';
> 
> ```

---

### 9. Buscar os atores do gênero feminino, retornando PrimeiroNome, UltimoNome e ordenando pelo PrimeiroNome
<img src="Imagens/9.png" alt="Exercicio 9" width="90%" />

> **Resposta:**
> ```sql
> SELECT 
>     primeironome as "Primeiro Nome", 
>     ultimonome "Ultimo Nome", 
>     genero as "Genero"
> FROM atores
> WHERE genero = 'F'
> ORDER BY primeironome;
> 
> ```

---

### 10. Buscar o nome do filme e o gênero
<img src="Imagens/10.png" alt="Exercicio 10" width="90%" />

> **Resposta:**
> ```sql
> SELECT 
>     Filmes.Nome as "Nome", 
>     Generos.Genero as "Genero"
> FROM Filmes
> JOIN FilmesGenero ON Filmes.Id = FilmesGenero.IdFilme
> JOIN Generos ON FilmesGenero.IdGenero = Generos.Id;
> 
> ```

---

### 11. Buscar o nome do filme e o gênero do tipo "Mistério"
<img src="Imagens/11.png" alt="Exercicio 11" width="90%" />

> **Resposta:**
> ```sql
> SELECT Filmes.Nome AS "Nome", Generos.Genero AS "Genero"
> FROM Filmes
> JOIN FilmesGenero ON Filmes.Id = FilmesGenero.IdFilme
> JOIN Generos ON FilmesGenero.IdGenero = Generos.Id
> WHERE Generos.Genero = 'Mistério';
> 
> ```

---

### 12. Buscar o nome do filme e os atores, trazendo PrimeiroNome, UltimoNome e seu Papel
<img src="Imagens/12.png" alt="Exercicio 12" width="90%" />

> **Resposta:**
> ```sql
> SELECT 
>     Filmes.Nome AS "Nome", 
>     Atores.PrimeiroNome AS "Primeiro Nome",
>     Atores.UltimoNome AS "Ultimo Nome",
>     ElencoFilme.Papel AS "Papel"
> FROM Filmes
> JOIN ElencoFilme ON Filmes.Id = ElencoFilme.IdFilme
> JOIN Atores ON ElencoFilme.IdAtor = Atores.Id;
> 
> ```
