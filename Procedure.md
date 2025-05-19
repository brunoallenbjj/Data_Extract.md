# Procedimento de Extração de Dados SAP – SE16

## Objetivo
Procedimento para Auditores de Autorização CSI realizarem o download de tabelas SAP utilizando a transação SE16.

---

## Observações Importantes

- Utilize **somente a transação SE16** com as configurações indicadas. **Não utilize SE16N ou SE16N em modo batch**.

---

## Passo a Passo

### 1. Verificar Configurações da SE16

Navegue até:  
**Configurações → Parâmetros do Usuário → Navegador de Dados**

Confirme os seguintes parâmetros:

- `Lista de Saída`: Lista Padrão SE16  
- `Palavra-Chave`: NOME DO CAMPO  
- `Número máximo de registros`: `999999.999`  
- `Largura da lista de saída`: `250`

---

### 2. Executar os Downloads

1. Inicie a transação **SE16**  
2. Insira o nome da tabela  
3. Deixe o campo **Max registros** em branco  
4. Execute (`F8`)  
5. Anote o total de registros selecionados  
6. Salve o arquivo:  
   `Sistema → Lista → Salvar → Arquivo Local → NÃO CONVERTIDO`  
   Salvar como: `C:\[NOME_DA_TABELA].UPL`

7. Repita o processo para cada tabela listada abaixo

---

## Tabelas Relevantes

| Nome da Tabela | Descrição                                | 3_XX | 4_XX | 4_0B | 4_5B | 4_6B | 4_6C | WAS | HANA |
|----------------|-------------------------------------------|------|------|------|------|------|------|-----|------|
| AGR_AGRS       | Papéis compostos                         |      |  X   |  X   |  X   |  X   |      |  X  |  X   |
| AGR_PROF       | Papel – Perfil                           |      |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| AGR_TEXTS(*)   | Descrição do papel                       |      |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| AGR_USERS      | Usuário – Papel                          |      |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| T000           | Configurações do Cliente                 |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| TOBJT(*)       | Descrição dos objetos de autorização     |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| USR02          | IDs de usuários                          |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| USR03          | Descrição dos IDs de usuários            |  X   |                                      |  X  |  X   |
| USR11(*)       | Descrição dos perfis                     |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| USR13(*)       | Descrição das autorizações               |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| USREFUS        | Usuários de referência                   |                                      |  X  |  X   |
| UST04          | Usuário – Perfis                         |                                      |  X  |  X   |
| UST10C         | Perfis compostos                         |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| UST10S         | Perfis individuais                       |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| UST12          | Valores de autorização                   |  X   |  X   |  X   |  X   |  X   |  X   |  X  |  X   |
| V_USERNAME     | Descrição dos IDs de usuário             |                          |  X   |  X   |  X  |  X   |
| AGR_1250       | Dados de autorização do grupo de atividades |                          |                   |  X  |  X   |
| AGR_1251       | Dados de autorização do grupo de atividades |                          |                   |  X  |  X   |
| AGR_1252       | Elementos organizacionais para autorizações |                          |                   |  X  |  X   |
| AGR_TCODES     | Atribuição de papéis às transações       |                          |                   |  X  |  X   |
| AGR_1016B      | Nome do perfil do grupo de atividades    |                          |                   |  X  |  X   |
| AGR_DEFINE     | Tabela de definição de papel             |                          |                   |  X  |  X   |
| AGR_FLAGS      | Atributos do papel                       |                          |                   |  X  |  X   |
| USORG          | Campos e descrição de níveis organizacionais |                        |                   |  X  |  X   |

> (*) Estas tabelas podem ser restringidas a um único idioma.

---

## Legenda de Releases

| Código | Descrição                                         |
|--------|---------------------------------------------------|
| 3.XX   | SAP Releases 3.0X ou 3.1X                         |
| 4.XX   | SAP Releases 4.XX (sem usuários, ref. etc.)       |
| 4.0B   | SAP Release 4.0B                                  |
| 4.5B   | SAP Release 4.5B                                  |
| 4.6B   | SAP Release 4.6B                                  |
| 4.6C   | SAP Releases 4.6C ou 4.6D                         |
| WAS    | SAP Releases 4.7, ECC 6.0, BW, CRM etc.           |
| HANA   | SAP S/4 HANA                                      |

---

## Relatórios Adicionais Obrigatórios

Execute os seguintes relatórios e salve como arquivos `.txt`:

- **RSPARAM**
- **RSUSR003**

---

## Preparação para Extração

### Antes de extrair cada tabela:

- **Certifique-se de que todos os campos estão selecionados para extração**
- Nome do campo = nome técnico

> Somente os campos selecionados serão incluídos no resultado da extração.

