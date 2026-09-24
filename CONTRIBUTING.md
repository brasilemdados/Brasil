# Como contribuir

O projeto é aberto e colaborativo. Qualquer pessoa pode contribuir, independentemente de formação, profissão, região, experiência técnica, religião ou visão de mundo.

Antes de contribuir, leia também o `README.md` do projeto.

## Navegação

<details>
<summary><strong>Ver seções</strong></summary>

- [Princípios das contribuições](#princípios-das-contribuições)
- [1. Comece pela pergunta](#1-comece-pela-pergunta)
- [2. Utilize fontes públicas](#2-utilize-fontes-públicas)
- [3. Explique por que cada fonte é necessária](#3-explique-por-que-cada-fonte-é-necessária)
- [4. A metodologia deve ser explícita](#4-a-metodologia-deve-ser-explícita)
- [5. Não transforme correlação em conclusão](#5-não-transforme-correlação-em-conclusão)
- [6. Rastreabilidade](#6-rastreabilidade)
- [7. Documente as fontes](#7-documente-as-fontes)
- [8. Limitações devem ser apresentadas](#8-limitações-devem-ser-apresentadas)
- [9. Compartilhamos fatos, não juízos de valor](#9-compartilhamos-fatos-não-juízos-de-valor)
- [10. Organização dos repositórios](#10-organização-dos-repositórios)
- [11. Código em português](#11-código-em-português)
- [12. Clareza antes de sofisticação](#12-clareza-antes-de-sofisticação)
- [13. Pull Requests](#13-pull-requests)
- [14. Commits](#14-commits)
- [15. Revisão das contribuições](#15-revisão-das-contribuições)

</details>

## Princípios das contribuições

A contribuição deve ajudar outras pessoas a encontrar respostas nos dados, não dizer a elas qual conclusão devem tirar.

Toda contribuição deve respeitar os princípios do Brasil em Dados:

* utilizar fontes públicas e verificáveis, preferencialmente governamentais;
* partir de uma pergunta clara e objetiva;
* manter postura apartidária;
* documentar a metodologia utilizada;
* informar limitações conhecidas;
* priorizar clareza e rastreabilidade;
* utilizar língua portuguesa padrão sempre que possível.

---

# 1. Comece pela pergunta

Cada análise, cruzamento ou conjunto de dados derivado deve partir de uma **pergunta clara e objetiva**. A fonte deve ser escolhida porque contém uma informação necessária para responder à pergunta.

**Não devemos coletar dados apenas porque estão disponíveis.**

<details>
<summary><strong>Ver exemplo</strong></summary>

Por exemplo:

> **Quantas empresas registradas no Cadastro Nacional de Empresas Inidôneas e Suspensas (CEIS) assinaram contratos com entes públicos após a data de início de uma sanção no período X?**

A partir dessa pergunta, podemos determinar quais informações são necessárias para respondê-la.

| Informação necessária                            | Possível fonte pública |
| ------------------------------------------------ | ---------------------- |
| Empresas e sanções registradas                   | CEIS                   |
| Contratos celebrados com entes públicos          | PNCP                   |
| Informações cadastrais da empresa                | REDESIM                |
| Identificador utilizado para relacionar as bases | CNPJ                   |

</details>

---

# 2. Utilize fontes públicas

Os dados utilizados pelo Brasil em Dados devem ser provenientes de **fontes públicas e verificáveis**, preferencialmente governamentais. Sempre que possível, os dados devem ser obtidos diretamente do órgão responsável por sua produção ou publicação.

O fato de uma informação estar disponível na internet não significa, por si só, que ela seja uma fonte adequada para o projeto.

<details>
<summary><strong>Dados que não devem ser utilizados</strong></summary>

Não devem ser utilizados dados:

* obtidos de forma ilegal;
* provenientes de vazamentos;
* obtidos por acesso indevido;
* cuja origem não possa ser identificada;
* que não possam ser verificados por outras pessoas.

</details>

---

# 3. Explique por que cada fonte é necessária

Explique o papel de cada uma das bases na resposta à pergunta. Não basta informar quais arquivos ou bases foram utilizados.

<details>
<summary><strong>Ver exemplo</strong></summary>

Considerando a pergunta:

> **Quantas empresas registradas no Cadastro Nacional de Empresas Inidôneas e Suspensas (CEIS) assinaram contratos com entes públicos após a data de início de uma sanção no período X?**

A relação entre as fontes pode ser explicada da seguinte forma:

```text
CEIS -> Identifica empresas e os períodos das sanções

PNCP -> Identifica contratos celebrados com entes públicos

REDESIM -> Complementa informações cadastrais das empresas

CNPJ -> Permite relacionar os registros entre as bases
```

</details>

---

# 4. A metodologia deve ser explícita

A pergunta sozinha não é suficiente. Também precisamos explicar **como ela foi respondida**.

A implementação pode ser complexa, mas a explicação não precisa ser.

<details>
<summary><strong>O que pode precisar ser documentado?</strong></summary>

No exemplo das empresas sancionadas, seria necessário definir, entre outras coisas:

* quais registros do CEIS foram considerados;
* qual período foi analisado;
* qual data representa o início da sanção;
* se a sanção possuía data de término;
* quais tipos de sanção foram considerados;
* quais contratos foram considerados;
* qual data do contrato foi utilizada;
* como as empresas foram identificadas;
* como registros duplicados foram tratados;
* como empresas sem CNPJ válido foram tratadas;
* como contratos alterados ou cancelados foram tratados.

</details>

---

# 5. Não transforme correlação em conclusão

Um cruzamento de bases pode identificar um fato que merece análise. Ele não deve produzir automaticamente uma conclusão que os próprios dados não sustentam.

Encontrar um contrato com data posterior ao início de uma sanção, por exemplo, **não significa, por si só, que houve uma contratação irregular**.

O Brasil em Dados apresenta o que foi encontrado nos dados. Conclusões que dependam de análise jurídica, política, moral ou de outras informações não devem ser presumidas pelo projeto.

<details>
<summary><strong>Ver exemplo</strong></summary>

Pode ser necessário considerar:

* tipo da sanção;
* alcance da sanção;
* órgão responsável;
* período de vigência;
* legislação aplicável;
* momento em que o contrato foi celebrado;
* alterações posteriores no registro;
* particularidades administrativas ou jurídicas.

Uma resposta adequada seria:

> Foram encontradas Z empresas que celebraram contratos com Y entes públicos após a data de início das sanções, considerando o período X.

Repare na diferença: apresentamos o que foi encontrado nos dados, sem afirmar se os contratos são **regulares** ou **irregulares**.

</details>

---

# 6. Rastreabilidade

Uma pessoa que encontre um resultado no Brasil em Dados deve conseguir entender de onde ele veio e como foi produzido.

<details>
<summary><strong>Perguntas que toda análise deve permitir responder</strong></summary>

1. Qual pergunta está sendo respondida?
2. Quais fontes foram utilizadas?
3. De onde os dados vieram?
4. Quando os dados foram coletados?
5. Quais transformações foram realizadas?
6. Como as bases foram relacionadas?
7. Como o resultado foi calculado?
8. Quais são as limitações conhecidas?
9. É possível reproduzir o resultado?

</details>

---

# 7. Documente as fontes

Cada fonte utilizada deve ser identificada de forma clara.

Sempre que aplicável, informe:

* nome da base;
* instituição responsável;
* endereço de origem;
* data da coleta.

<details>
<summary><strong>Ver exemplo</strong></summary>

```text
Fonte: Cadastro Nacional de Empresas Inidôneas e Suspensas
Sigla: CEIS
Responsável: Controladoria-Geral da União
Data da coleta: DD/MM/AAAA
```

</details>

---

# 8. Limitações devem ser apresentadas

Nenhuma base de dados é perfeita. Quando conhecidas, as limitações devem ser apresentadas junto à análise.

**Não esconda limitações. Elas fazem parte do resultado.**

<details>
<summary><strong>Exemplos de limitações</strong></summary>

* períodos sem dados;
* atraso na atualização da fonte;
* registros sem CNPJ;
* mudanças metodológicas;
* diferenças entre bases;
* informações duplicadas;
* dados corrigidos posteriormente pela fonte;
* impossibilidade de identificar determinados registros;
* cobertura incompleta da fonte para determinados períodos.

</details>

---

# 9. Compartilhamos fatos, não juízos de valor

Uma contribuição **não deve** utilizar os dados para defender uma posição política, partidária, moral ou ideológica.

**A interpretação pertence a quem utiliza os dados.**

---

# 10. Organização dos repositórios

O Brasil em Dados possui um repositório central, chamado `Brasil`, e um repositório específico para cada Unidade da Federação.

Um processo automatizado é responsável por integrar ao repositório `Brasil` os dados produzidos nos repositórios estaduais e no Distrito Federal.

De forma geral:

* dados específicos de uma Unidade da Federação devem ser adicionados ao repositório correspondente;
* o repositório `Brasil` funciona como ponto central para consulta e integração dos dados do projeto.

---

# 11. Código em português

O projeto deve ser compreensível pelo maior número possível de brasileiros. Por isso, sempre que possível, utilize **língua portuguesa padrão** em:

* nomes de arquivos;
* diretórios;
* variáveis;
* funções;
* classes;
* comentários;
* documentação;
* mensagens produzidas pelo sistema.

O objetivo não é traduzir tudo artificialmente.

O objetivo é tornar o projeto compreensível.

<details>
<summary><strong>Termos técnicos que podem permanecer em inglês</strong></summary>

Termos técnicos consolidados podem permanecer em inglês quando sua tradução dificultar a compreensão ou gerar ambiguidade.

Exemplos:

```text
API
CSV
JSON
SQL
DataFrame
HTTP
commit
Pull Request
```

</details>

---

# 12. Clareza antes de sofisticação

Prefira código simples e explícito. Uma solução fácil de ler, testar e reproduzir é preferível a uma solução mais curta, porém difícil de compreender.

Código que outra pessoa consegue entender e manter é mais valioso para o projeto do que uma solução desnecessariamente sofisticada.

---

# 13. Pull Requests

Todo `Pull Request` que adicionar uma análise deve conter informações suficientes para que outra pessoa consiga entender e reproduzir a contribuição.

<details>
<summary><strong>O que deve constar no Pull Request?</strong></summary>

### Qual pergunta estamos respondendo?

Explique em uma frase.

### Quais fontes foram utilizadas?

Informe as bases públicas utilizadas.

### Por que essas fontes foram utilizadas?

Explique qual informação cada fonte fornece.

### Como os dados foram relacionados?

Informe as chaves utilizadas, como CNPJ, código de município ou outro identificador.

### Qual metodologia foi utilizada?

Explique filtros, regras, cálculos e transformações.

### Quais limitações existem?

Documente problemas conhecidos.

### Como reproduzir?

Informe os comandos necessários para gerar novamente o resultado.

</details>

---

# 14. Commits

Mensagens de `commit` podem e devem ser escritas em português.

Prefira mensagens que expliquem claramente a alteração realizada.

---

# 15. Revisão das contribuições

Uma contribuição pode receber pedidos de alteração antes de ser aceita.

A revisão deve se concentrar nos **dados e na metodologia**, e não na posição política, religião, profissão ou visão de mundo de quem contribuiu.

<details>
<summary><strong>Critérios de revisão</strong></summary>

As revisões devem verificar principalmente:

* a pergunta está clara?
* as fontes são públicas e verificáveis?
* fontes governamentais foram priorizadas quando disponíveis?
* as fontes realmente permitem responder à pergunta?
* a metodologia está documentada?
* o resultado pode ser reproduzido?
* os cálculos estão corretos?
* as limitações estão descritas?
* existe algum juízo de valor sendo apresentado como fato?
* o código está compreensível?
* outra pessoa consegue entender como o resultado foi produzido?

</details>

---

## Obrigado por contribuir 🇧🇷
