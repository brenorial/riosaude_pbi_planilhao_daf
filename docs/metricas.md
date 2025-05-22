## 🧾 Métricas Principais

### NF Canceladas

Conta o total de Notas Fiscais cujo status foi marcado como **Cancelada**, em que na tabela Status_NF contenha a string "Cancelada".

```DAX
NF Canceladas =
CALCULATE(
    COUNT(processos[numero_nf]),
    processos[status_nf] = "Cancelada"
)
```

---

### NF Atrasadas

Conta as Notas Fiscais que apresentam algum atraso registrado, ou seja, quando o campo de atraso não está vazio, permitindo identificar NF que não foram processadas no prazo esperado.

```DAX
NF Atrasadas =
CALCULATE(
    COUNT(processos[numero_nf]),
    NOT(ISBLANK(processos[atrasado]))
)
```

---

### NF Autorizadas

Calcula o total de Notas Fiscais com status **Autorizada**, em que na tabela Status_NF contenha a string "Autorizada".

```DAX
NF Autorizadas =
CALCULATE(
    COUNT(processos[numero_nf]),
    processos[status_nf] = "Autorizada"
)
```

---

### Saldo

Representa a diferença entre o valor total das Notas Fiscais e o valor líquido total, indicando o saldo financeiro pendente ou disponível.

```DAX
Saldo = [Valor NF Total] - [Valor Líquido Total]
```

---

### Total de NF

Contabiliza todas as Notas Fiscais registradas, independentemente do status, oferecendo uma visão geral do volume de documentos processados.

```DAX
Total de NF =
CALCULATE(COUNT(processos[numero_nf]))
```
