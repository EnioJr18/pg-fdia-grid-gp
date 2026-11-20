# Mapeamento de Ameaças e Controles de Integridade FDIA por Camada

**Responsável:** David Gabriel Lima Martins (2024001428)  
**Data:** 20/11/2026  
**Fundamentação de referência:** Szczepaniuk (2025); Liang et al. (2017)

## 1. Arquitetura de Controles de Integridade

A partir de uma abordagem de segurança em camadas, a equipe propõe controles contra ataques de injeção de dados falsos (FDIA), priorizando o atributo de **integridade** em três camadas críticas da Smart Grid.

| Camada Arquitetural | Ativos Críticos | Vetor de Ataque FDIA | Controles Preventivos e Detectivos |
| :--- | :--- | :--- | :--- |
| **1. Campo e Medição** | Medidores inteligentes, RTUs, PMUs e IEDs | Adulteração física ou local de sensores antes da transmissão | Lacres físicos, autenticação de hardware quando disponível (por exemplo, TPM), verificação de assinatura na origem e redundância cruzada de PMUs |
| **2. Comunicação SCADA** | Enlaces DNP3, IEC 61850 e concentradores | Interceptação *man-in-the-middle* e injeção de mensagens falsas em trânsito | Proteção criptográfica compatível com protocolos/equipamentos (por exemplo, TLS/IPsec), HMAC e segmentação de redes operacionais |
| **3. Centro de Controle (EMS)** | Estimador de Estado (SE), SCADA Master e IHM | Manipulação coordenada de medidas para contornar a detecção baseada em resíduos ($r = z - H\hat{x}$) | Validação cruzada com históricos de carga, sinalização de telemetria incoerente e confirmação humana para despachos críticos |

## 2. Decisão Técnica Registrada

- **Decisão proposta:** Concentrar controles criptográficos de maior custo (como PMUs autenticadas e túneis IPsec dedicados) nos nós classificados como **Criticidade Alta** na matriz de priorização, mantendo controles proporcionais e validação estatística nos demais.
- **Justificativa:** Priorizar recursos sob restrição orçamentária. O efeito dessa seleção sobre a observabilidade global do estimador de estado **deve ser verificado tecnicamente**, e não pode ser garantido apenas pela priorização. Liang et al. (2017) é uma referência sobre FDIA, não comprovação automática desta escolha específica.

> **Nota de rastreabilidade acadêmica:** confirmar os títulos, dados bibliográficos e trechos exatos das obras antes de atribuir a elas a taxonomia ou a eficácia dos controles propostos.
