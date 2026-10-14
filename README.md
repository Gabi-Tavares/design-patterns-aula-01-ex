# Atividade

Que tal refletirmos um pouco sobre o que acontece com esse código quando novos requisitos são adicionados?

---

## 🎯 Objetivo da Atividade

Altere o código da classe PlanetasPrinter que os planetas também possam ser impressos.
Tente fazer isso com o menor esforço possível.

Verifique a classe [br.pucpr.Planet](https://github.com/ViniGodoy/design-patterns/blob/aula-01-ex/src/main/java/br/pucpr/planet/Planet.java)

O formato de impressão da tabela (bordas, temas) deve ser exatamente igual ao da tabela de usuários.

Quanto aos dados:
1. Devem ser impressas as seguintes colunas "Nome", "Diâmetro", "Dist. sol (km)", "Dist. sol (ua)", e "Tipo". Observação uma unidade astronomica (UA) é equivalente à distância da Terra ao Sol.
2. O diametro do planeta deve ser impresso com 1 casa decimal e separadores de milhar.
3. A distância até o sol em km deve ser impressa em um número inteiro com separadores de milhar.  
4. Já a distância em UA deve ser impressa com duas casas decimais com separadores de milhar.
5. O tipo deve ser impresso como "Rochoso", "Gososo", "Gelado", "Anão"

## 📋 Reflexão final

Ao final da implementação reflita:

1. Sua solução ficou com muito código duplicado?
2. O que aconteceria se uma terceira classe tivesse que ser adicionada?

### ✍️ Respostas

**1. Sua solução ficou com muito código duplicado?**

Sim. Quase metade da classe `PlanetasPrinter` é uma cópia da `UsersPrinter`. As duas repetem a validação de lista vazia, o desenho das bordas com o caractere do tema, o laço sobre os itens, o recuo usado para alinhar à direita e o corte de nomes longos. O que realmente muda entre elas é pouco: os títulos das colunas, as larguras e as funções que formatam cada valor.

**2. O que aconteceria se uma terceira classe tivesse que ser adicionada?**

Seria preciso fazer uma terceira cópia da mesma lógica, e o código repetido cresceria a cada nova tabela. Qualquer mudança no formato, como um tema novo ou outro tipo de borda, teria que ser feita em todas as impressoras. Um bug corrigido em uma delas poderia continuar nas outras. A largura da borda também é um número fixo calculado à mão em cada classe (74 nos usuários e 81 nos planetas), o que é fácil de errar.

Uma solução melhor seria separar o que é igual do que muda. Uma impressora de tabela genérica cuidaria das bordas, do cabeçalho, do tema e do alinhamento. Cada tipo de dado só informaria suas colunas: título, largura, alinhamento e uma função que extrai e formata o valor. Assim, adicionar uma terceira classe exigiria apenas declarar as colunas dela. Essa ideia se aproxima dos padrões Strategy e Template Method.

---

## 🛠️ Requisitos para Execução

* **Linguagem:** Java 17 ou superior

### Como Executar

```bash
javac PlanetasPrinter.java
java PlanetasPrinter
```
