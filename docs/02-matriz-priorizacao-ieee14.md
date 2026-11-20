# Matriz de Priorização de Medidores Críticos (Estudo de Caso IEEE 14-Bus)

**Responsável:** Entony Richard da Silva Santos (2024002087)  
**Data:** 20/11/2026  
**Fundamentação de referência:** Liang et al. (2017)

## 1. Critérios de Pontuação (Modelo Multicritério)

Para operacionalizar uma restrição orçamentária **simulada**, cada barramento recebe notas de 1 a 5 conforme critérios propostos pela equipe:

- **Impacto Operacional ($I$ — Peso 40%):** risco de sobrecarga e impacto no despacho econômico.
- **Centralidade Topológica ($T$ — Peso 35%):** conectividade e influência sobre o problema de estimação de estado.
- **Custo-Benefício de Blindagem ($C$ — Peso 25%):** viabilidade de implantação de controles em RTUs/PMUs.

$$
\text{Índice de Criticidade (IC)} = (I \times 0{,}40) + (T \times 0{,}35) + (C \times 0{,}25)
$$

**Ressalva sobre o teto:** um limite estrito de **35% das 14 barras** comporta, no máximo, **4 barras inteiras** ($4/14 \approx 28{,}6\%$); **5 de 14** representam **35,7%**, acima de 35%. A seleção de cinco barras abaixo corresponde, portanto, a um **teto arredondado/aproximado**, e não ao cumprimento exato de um limite rígido de 35%.

## 2. Ranqueamento Proposto (Top 7)

As notas são **estimativas ilustrativas** informadas no planejamento; não constituem saída validada de uma simulação elétrica ou de otimização. As funções topológicas precisam ser verificadas no modelo IEEE 14-Bus utilizado.

| Ranking | Barra (IEEE 14-Bus) | Função na Rede (descrição preliminar) | Impacto ($I$) | Topologia ($T$) | Custo-Benefício ($C$) | IC | Decisão sob teto **aproximado** de 5 barras |
| :---: | :---: | :--- | :---: | :---: | :---: | :---: | :--- |
| **1º** | **Barra 4** | Interligação central | 5,0 | 5,0 | 4,0 | **4,75** | **BLINDAR (Prioridade 1)** |
| **2º** | **Barra 5** | Transferência de fluxo e interligação | 5,0 | 4,5 | 4,0 | **4,58** | **BLINDAR (Prioridade 1)** |
| **3º** | **Barra 2** | Geração e interconexão | 5,0 | 4,0 | 4,0 | **4,40** | **BLINDAR (Prioridade 1)** |
| **4º** | **Barra 9** | Distribuição com compensação reativa | 4,5 | 4,5 | 3,5 | **4,25** | **BLINDAR (Prioridade 2)** |
| **5º** | **Barra 1** | Referência (*Slack Bus*) e geração | 5,0 | 3,5 | 3,5 | **4,10** | **BLINDAR (Prioridade 2)** |
| **6º** | **Barra 6** | Subestação com geração reativa | 4,0 | 3,5 | 3,5 | **3,70** | Monitoramento estatístico |
| **7º** | **Barra 14** | Extremidade de carga | 2,5 | 2,0 | 4,5 | **2,83** | Monitoramento estatístico |

## 3. Resultado Gerencial Proposto

No cenário de orçamento **aproximado** de cinco barras, selecionam-se barras 4, 5, 2, 9 e 1, equivalentes a **35,7%** do total. A seleção busca aumentar a dificuldade de alterações coordenadas e apoiar a priorização da defesa. **Não é possível concluir que ataques FDIA ficaram inviáveis ou que a observabilidade global está garantida sem teste quantitativo** contra um modelo de ataques e de estimação de estado.

O limiar de 35%, os pesos e as notas são **premissas da equipe**, não resultados matemáticos atribuídos sem verificação a Liang et al. (2017).
