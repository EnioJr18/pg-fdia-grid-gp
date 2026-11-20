# Playbook Operacional de Resposta a Incidentes FDIA (Versão Preliminar)

**Responsáveis pelo documento:** Lucas Gabriel da Silva Souza (2024015209) e Entony Richard da Silva Santos (2024002087)  
**Data:** 20/11/2026  
**Fundamentação de referência:** Szczepaniuk (2025); Al Khasabah et al. (2025)

## 1. Fluxo de Resposta e Contenção em 4 Fases

| Fase | Gatilho / Indicador | Ações Operacionais Propostas | Papel Responsável | SLA Máximo (meta simulada) |
| :--- | :--- | :--- | :--- | :---: |
| **1. Triagem e Detecção** | Divergência entre estimação de estado e carga histórica; falha de autenticação/HMAC | Sinalizar alerta no EMS e avaliar, conforme protocolo autorizado, a suspensão de comandos automáticos de redespacho (AGC) | Operador de Sala de Controle (EMS) | 5 min |
| **2. Contenção** | Confirmação de telemetria anômala em RTU/PMU | Isolar logicamente o canal suspeito mediante autorização operacional, utilizar medições redundantes verificadas e restringir escrita remota | Engenheiro de Segurança OT / SCADA | 15 min |
| **3. Erradicação** | Origem comprometida identificada (enlace, credencial ou firmware) | Revogar ou rotacionar credenciais afetadas conforme procedimento, providenciar *failover* seguro e validar integridade de firmware | Equipe de Resposta a Incidentes (CSIRT) | 60 min |
| **4. Recuperação e Lições** | Canal validado e medições consistentes | Reintegrar gradualmente ativos após validação técnica, atualizar riscos e elaborar relatório pós-incidente | Gestor de Operação e Riscos | 24 horas |

## 2. Critérios de Segurança e Escalonamento

As ações são **propostas para estudo acadêmico**; em uma rede elétrica real, suspensão de AGC, isolamento de SCADA, rotação de chaves e retorno de RTUs exigem aprovação dos operadores responsáveis e procedimentos formais de segurança operacional. Não executar automaticamente mudanças que possam comprometer estabilidade, disponibilidade ou segurança física.

Os SLAs são **metas de exercício**, não valores medidos ou estabelecidos pelos artigos. Devem ser revisados após simulações e aprovação da equipe.

## 3. Evidências e Próximos Passos

- Registrar horário do alerta, medidas observadas, decisões autorizadas e responsáveis.
- Preservar logs e trilha de auditoria do incidente.
- Validar a versão preliminar com os responsáveis antes do fechamento da EAP 3.3.
