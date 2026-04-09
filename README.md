# Relatório da NOME DA ATIVIDADE

**Disciplina:** PROGRAMAÇÃO CONCORRENTE E DISTRIBUÍDA 
**Aluno(s):** Leticia de Oliveira Barros
**Turma:** S.I 
**Professor:** Rafael Marconi
**Data:**08/04/2026

---

# 1. Descrição do Problema

Descreva o problema computacional resolvido pelo programa.

## Orientações para preenchimento

Explique:

* Qual problema foi implementado
* Qual algoritmo foi utilizado
* Qual o tamanho da entrada utilizada nos testes
* Qual o objetivo da paralelização

**Questões que devem ser respondidas:**

* Qual é o objetivo do programa?
* Qual o volume de dados processado?
* Qual algoritmo foi utilizado?
* Qual a complexidade aproximada do algoritmo?

---

# 2. Ambiente Experimental

Descreva o ambiente em que os experimentos foram realizados.

## Orientações

Informar as características do hardware e software utilizados na execução dos testes.

| Item                        | Descrição |
| --------------------------- | --------- |
| Processador                 |    Core i7-12700        |
| Número de núcleos           |      12     |
| Memória RAM                 |      16 GB     |
| Sistema Operacional         |     Windows 11      |
| Linguagem utilizada         |     Python 3.13.2      |
| Biblioteca de paralelização |      MPI     |
| Compilador / Versão         |     Python 3.13.2       |

---

# 3. Metodologia de Testes

O tempo de execução foi medido utilizando a função time da linguagem Python.
Para cada configuração (1, 2, 4, 8 e 12 processos), foram realizadas 5 execuções, sendo utilizado o tempo médio como resultado final.

Os testes foram realizados em uma máquina com carga controlada, evitando a execução de outros processos que pudessem interferir nos resultados.

O tamanho da entrada foi mantido constante em todos os testes, garantindo a comparabilidade dos resultados.

Explique como os experimentos foram conduzidos.

## Orientações

Descrever:

* Como o tempo de execução foi medido
* Quantas execuções foram realizadas
* Se foi utilizada média dos tempos
* Qual tamanho da entrada foi usado

### Configurações testadas

Os experimentos devem ser realizados nas seguintes configurações:

* 1 thread/processo (versão serial)
* 2 threads/processos
* 4 threads/processos
* 8 threads/processos
* 12 threads/processos

### Procedimento experimental

Descrever:

* Número de execuções para cada configuração
* Forma de cálculo da média
* Condições de execução (ex: máquina dedicada, carga do sistema, etc.)

---

# 4. Resultados Experimentais

Preencha a tabela com os **tempos médios de execução** obtidos.

## Orientações

* O tempo deve ser informado em **segundos**
* Utilizar a **média das execuções**

| Nº Threads/Processos | Tempo de Execução (s) |
| -------------------- | --------------------- |
| 1                    |          31.61             |
| 2                    |          24.32             |
| 4                    |          16.60             |
| 8                    |          11.60             |
| 12                   |          10.07             |

---

# 5. Cálculo de Speedup e Eficiência

## Fórmulas Utilizadas

### Speedup

```
Speedup(p) = T(1) / T(p)
```

Onde:

* **T(1)** = tempo da execução serial
* **T(p)** = tempo com p threads/processos

### Eficiência

```
Eficiência(p) = Speedup(p) / p
```

Onde:

* **p** = número de threads ou processos

---

# 6. Tabela de Resultados

Preencha a tabela abaixo utilizando os tempos medidos.

| Threads/Processos | Tempo (s) | Speedup | Eficiência |
| ----------------- | --------- | ------- | ---------- |
| 1                 |   31.61        | 1.0     | 1.0        |
| 2                 |   24.32        | 1.30        |   0.65         |
| 4                 |   16.60        | 1.90        |   0.48         |
| 8                 |   11.60        | 2.72        |   0.34         |
| 12                |   10.07        | 3.14        |   0.26         |

---

# 7. Gráfico de Tempo de Execução

Construa um gráfico mostrando o **tempo de execução em função do número de threads/processos**.

## Orientações

* Eixo X: número de threads/processos
* Eixo Y: tempo de execução (segundos)

Inserir o gráfico abaixo:

![Gráfico Tempo Execução](graficos/tempo_execucao.png)

---

# 8. Gráfico de Speedup

Construa um gráfico mostrando o **speedup obtido**.

## Orientações

* Eixo X: número de threads/processos
* Eixo Y: speedup
* Incluir também a **linha de speedup ideal (linear)** para comparação

Inserir o gráfico abaixo:

![Gráfico Speedup](graficos/speedup.png)

---

# 9. Gráfico de Eficiência

Construa um gráfico mostrando a **eficiência da paralelização**.

## Orientações

* Eixo X: número de threads/processos
* Eixo Y: eficiência
* Valores entre 0 e 1

Inserir o gráfico abaixo:

![Gráfico Eficiência](graficos/eficiencia.png)

---

# 10. Análise dos Resultados

O speedup obtido não foi linear, ficando abaixo do ideal. Enquanto o speedup ideal para 12 processos seria 12, o valor obtido foi aproximadamente 3.14, indicando limitações na paralelização.

A aplicação apresentou ganho de desempenho, porém com baixa escalabilidade, especialmente a partir de 4 processos.

A eficiência começou a cair de forma mais acentuada a partir de 4 threads/processos, reduzindo para cerca de 0.26 com 12 processos.

Apesar do número de processos não ultrapassar o número de núcleos físicos (12), houve impacto negativo causado por overhead de paralelização.

Esse overhead pode estar relacionado a:

custo de criação e gerenciamento de processos
comunicação entre processos (MPI)
sincronização
acesso à memória compartilhada/cache

Além disso, o algoritmo pode possuir partes não paralelizáveis, limitando o ganho total (Lei de Amdahl).

Portanto, mesmo com o aumento do número de processos, o desempenho não cresce proporcionalmente.


---

# 11. Conclusão

O uso de paralelismo trouxe ganho significativo de desempenho, reduzindo o tempo de execução de 31.61s para 10.07s.

O melhor desempenho foi obtido com 12 processos, embora o ganho marginal em relação a 8 processos tenha sido pequeno.

A aplicação não escalou de forma ideal, apresentando queda de eficiência conforme o número de processos aumentou.

Como melhorias, poderiam ser implementadas:

redução da comunicação entre processos
melhor balanceamento de carga
otimização de trechos sequenciais do código

Conclui-se que a paralelização foi eficaz, porém limitada por fatores de overhead e características do algoritmo.

---
