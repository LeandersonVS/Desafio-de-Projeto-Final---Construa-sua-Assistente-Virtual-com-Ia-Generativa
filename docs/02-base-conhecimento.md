# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para que serve o Amigo IA? |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores, Ou seja, dar continuidade ao atendimento de forma mais eficiente. |
| `perfil_investidor.json` | JSON | Personalizar recomendações sobre as dúvidas e necessidades de aprendizado do cliente. |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil do cliente. |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente do cliente e usar essas informações de forma didática. |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados?

Não teve modificações nos dados.

---

## Estratégia de Integração

### Como os dados são carregados?
import json

# Carrega a base no início da sessão
with open("knowledge_base.json", "r", encoding="utf-8") as f:
    knowledge = json.load(f)

# Injeta dados relevantes no prompt
def build_prompt(question):
    context = knowledge["educational_content"]
    return f"Use apenas o contexto abaixo:\n{context}\n\nPergunta: {question}"


### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Existem duas possibilidades, injetar os dados diretamente no prompt (CTRL + C, CTRL + V) ou carregar via código.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
