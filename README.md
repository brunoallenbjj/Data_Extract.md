# 🧾 Procedimento de Extração de Dados SAP – SE16

Este repositório documenta o procedimento utilizado por auditores de autorização (CSI) para extração de dados de tabelas SAP através da transação **SE16**.

---

## ⚠️ Observações Importantes

- Utilize **apenas a transação SE16** (não use SE16N ou SE16N em modo batch).
- As configurações de usuário devem ser ajustadas antes de iniciar a extração.

---

## ⚙️ Configuração Inicial da SE16

Acesse:  
**Configurações → Parâmetros do Usuário → Navegador de Dados**

Defina os seguintes parâmetros:

| Parâmetro                      | Valor                 |
|-------------------------------|------------------------|
| Lista de saída (`Output List`) | SE16 Lista Padrão     |
| Palavra-chave (`Key Word`)    | FIELD NAME            |
| Nº máximo de registros        | 999999.999            |
| Largura da lista de saída     | 250                   |

---

## 🧩 Passo a Passo para Extração

1. Inicie a transação **SE16**
2. Insira o nome da tabela
3. Deixe o campo de número máximo de registros em branco
4. Execute (F8)
5. Anote o total de registros selecionados
6. Salve o arquivo via:
