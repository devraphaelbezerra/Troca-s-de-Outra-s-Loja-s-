# 🔁 Troca entre Filiais no Varejo

**Controle de trocas em filiais diferentes via processo Fluig integrado com TOTVS RMS.**

Este repositório documenta a modelagem e o controle de trocas onde a compra foi realizada em uma filial e a devolução/troca ocorre em outra. Processo visa evitar furos de estoque, garantir a rastreabilidade fiscal e criar uma trilha auditável entre as filiais envolvidas.
![Sem título](https://github.com/user-attachments/assets/f10a9da1-a4e4-4a21-b779-cb94db303a68)

---

## 🧠 Cenário Real
* Cliente compra um produto na **filial DUQUE** (ex: 1-9).
* Cliente realiza a troca na **filial CIDADE NOVA** (ex: 3-5).
* O produto retorna fisicamente no estoque da CIDADE NOVA, mas precisa de compensação contábil.

---

## ⚠️ Problemas sem controle adequado
* Entrada indevida de estoque na filial de troca.
* Falta de baixa ou compensação fiscal.
* Falta de rastreabilidade de produto trocado.
* Divergência em relatórios e inventários.

---

## ✅ Solução com Processo BPM Fluig + Integração RMS

### 1. Abertura da Troca no Fluig WEB(Recepção).

* Operador inicia troca informando:
  * Cupom original ou chave da NF-e.
  * CPF/CNPJ do cliente.
  * Filial de origem da venda.
  * Itens a serem trocados.
  * Quantidades.

### 2. Identificação de Filial Origem ≠ Filial Troca

* Processo valida que a origem e destino são diferentes.
* Se o Cupom/NFC-e ainda não participou de uma troca para esta quantidade de itens.
* Gatilho para **processo de controle interfilial**.
  
![Sem título](https://github.com/user-attachments/assets/3c9846a8-e172-4f2c-a341-3445ecca3691)

### 3. Criação de Registro no Fluig

* Widget Pública registra a solicitação com:
  * Filial origem (venda).
  * Filial destino (troca).
  * Código dos produtos.
  * Motivo da troca.
  * Quantidade(s).

### 4. Geração de Movimentação Interfilial
![Sem título](https://github.com/user-attachments/assets/0fc75d03-0a4c-4a96-a245-d1a90a4dbac3)

* Geração automática ou manual de:
  * Registros na tabela do Fluig com campos no banco para controle de processamentos.
  * Uma rotina do RMS é executada em turnos diferentes varrendos as tabelas que precisam gerar o ajuste de transferências.
  * Nota de transferência entre filiais.
  * Ajuste de estoque ou movimentação contábil.
   
---
 * Exemplo voucher de troca:
 * ![Sem título-1](https://github.com/user-attachments/assets/132f9c3f-6b31-48f6-8773-b501135fd8b6)

---

## 🛠️ Tecnologias utilizadas
* TOTVS Fluig (Widget, Dataset, BPM, Mobile)
* TOTVS RMS (Notas, Estoque, Cadastros)
* SQL (consultas e rastreio de origem)
* Integrações via WebService ou Banco

---
![Sem título-1](https://github.com/user-attachments/assets/fbf3eef8-2680-4959-ae68-fe3595e4c21c)

## 📈 Benefícios
* Redução de perdas e desvios.
* Acerto fiscal e contábil de forma segura.
* Visibilidade de trocas entre lojas.
* Melhoria na experiência do cliente com agilidade e confiabilidade.

---

## 📌 Autor

Processo modelado por [@devraphaelbezerra](https://github.com/devraphaelbezerra), com base em vivência no varejo alimentar, fluência em integrações TOTVS e foco em processos críticos de loja.
