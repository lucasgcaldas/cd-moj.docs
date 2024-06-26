# Guia para subir contest

![type:video](/cd-moj.docs/assets/videos/criandoContest.mp4)

## Contest

O arquivo contest-description.txt deve estar corretamente preenchido e precisa obrigatoriamente estar compactado no formato **.tar** seguindo o exemplo abaixo:

### contest-description.txt

Dentro de um arquivo de contest deve conter um arquivo chamado **contest-description.txt** e uma pasta chamada **enunciados** e dentro dela deve conter todos os arquivos dos problemas que estarão presentes no contest.

O arquivo responsável pela criação dos contests deve seguir um modelo específico

```
ID_PADRAO_UNIX
"Nome Completo do Contest"
Data e hora de inicio em segundos
Data e hora de termino em segundos
Quantidade problemas
SITE ID "Nome Completo" item_contest link-enunciado
Numero-de-usuarios
login:senha:Nome Completo
login.admin:senha:Usuario do Tipo Administrador
login.mon:senha:Usuario do Tipo Monitor
Diretivas
```

- **ID_PADRAO_UNIX** - Um identificador único para o contest, não deve haver espaços.
- **Data e hora de início e fim** - Podem ser geradas pelo comando:
  `date --date="15:00:00 today" +%s`
- **Quantidade de problemas** - Deve ser um número inteiro.
- **SITE** - Identificador para o site de origem do problema, podendo ser spoj-br ou spoj-www.
- **ID** - É o ID do problema no SITE
- **Nome completo** - É o nome completo do problema, deve estar entre aspas.
- **item_contest** - É o item do problema dentro do contest, numérico ou alfanumérico. É recomendável, que sejam colocados em ordem.
- **link-enunciado** - São os endereços responsáveis por redirecionar para cada um dos problemas em seus respectivos sites, há três tipos:
  - **site** - Redireciona para o site, que deve ser um link inciando por http://.
  - **sitepdf** - Redireciona para o pdf do site.
  - **nome** - O nome do arquivo que pode está dentro do diretório de enunciados(Se a extensão do arquivo for omitida é utilizado todos os arquivos).
  - **none** - Para não ter um enunciado.
- **Número de usuários** - Deve ser um número inteiro designando o total de usuários no contest.
- **Diretivas** - Diretivas são algumas flags dentro do sistema do cd-moj que fornecem permissão a certas funcionalidades, são elas:
  - **LANGUAGES** - Define quais linguagens são aceitas pelo contest.
  - **PASSWD** - Define se a troca de senhas no contest é permitida. Se PASSWD=1 essa troca é permitida.
  - **PENALTYCOST** - PENALTYCOST=n implica uma penalidade de n minutos por submissão errada (n inteiro).
  - **PARTIALSTATISTIC** - Quando 1 permite acesso público às estatísticas durante a execução do contest (padrão = 0).
  - **STATISTICS** - Quando 0 não permite acesso público às estatísticas após o encerramento do contest (padrão = 1).
  - **ALLOWLATEUSER** - Quando y permite cadastro posterior de usuário por interação com o bot do telegram **@mojinho** (padrão = n).
  - **SHOWCODE** - Quando 1 mostra o código da submissão. (padrão = 0).
  - **CLARIFICATION** - Quando 1 permite acesso as abas de clarification. (padrão = 0).
  - **DISABLESUBMIT** - Esta variável permite desabilitar submissões no contest, mesmo que ele esteja em execução. Serve para permitir que os usuários leiam os enunciados, por exemplo, para um trabalho.
  - **MOJCONTESTSERVERS** - Esta variável permite direcionar as correções das submissões exclusivamente para uma ou mais máquinas específicas. Caso essa variável não seja fornecida, será considerado que o contest pode ser corrigido por qualquer máquina.
  - **CONTEST_TYPE** - Define o tipo de contest, direcionando-o para a fila de prioridade adequada. Caso essa variável não seja fornecida ou esteja vazia, será considerada a prioridade intermediária de *lista-privada*. Os tipos possíveis são, em ordem da maior para a menor prioridade:
    - super
    - prova
    - lista-privada
    - lista-publica

Segue um exemplo de um arquivo preenchido

```
doc_cdmoj
"Documentação CD-MOJ"
1627804800
2227420800
4
spoj-br PLACAR "Quem vai ser reprovado?" A reprovado.txt
cdmoj cartasfora "Jogando Cartas Fora" B jogando-cartas-fora.pdf
spoj-www TEST "Life, the Universe, and Everything" C https://www.spoj.com/problems/TEST/
spoj-br CONTAGEM "Não é Mais um Joguinho Canadense" D contagem.txt
4
winchester.admin:senhasecretaADMIN:Dean winchester Administrador
luffy.mon:senhasecretaMon:Monkey D. luffy Monitor
ribas:fiesta:Bruno Ribas
ricardo:busao:Ricardo Oliveira
CLARIFICATION=1
SHOWCODE=1
MOJCONTESTSERVERS="gpu2 gpu3"
CONTEST_TYPE=prova
```

---

## Passo a passo para criar um contest

1. É necessário entrar no link de [administrador](https://moj.naquadah.com.br/cgi-bin/admin.sh) e realizar o login;
2. Clicar na aba Old School;
3. Adicionar o arquivo contest-description.tar na opção "Envie novo contest" e clicar em submit;
4. Conferir se o contest foi criado com sucesso observando o Log disponibilizado logo abaixo da aba Old School;

---

### Formulário

Você tambem pode criar um contest por meio de um formulário, segue os mesmos padrões dos dados explicados em [contest-description](#contest-descriptiontxt).

![form](/cd-moj.docs/assets/images/form_create_contest.jpg)

---