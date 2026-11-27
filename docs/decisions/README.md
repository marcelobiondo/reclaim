# Decision log (ADR)

As decisões são registradas aqui para evitar perder contexto quando a ideia evoluir.

## ADR-001: Native-first, domain separated
**Data:** 2026-11-27  
**Status:** Proposta para validar

**Contexto:** objetivo é usar APIs de Screen Time no iOS e preservar opção de Android.

**Decisão:** priorizar app iOS nativo (SwiftUI), com regras de domínio desacopladas de frameworks Apple. No Android, se houver segunda plataforma, usar adaptador e UI nativos próprios.

**Consequências:** maior fidelidade e acesso às APIs iOS; reutilização futura primariamente de regras/especificações, não de interface/código. Validar capacidades antes de comprometer o projeto.

## ADR-002: Local-first e gamificação opcional
**Data:** 2026-11-27  
**Status:** Proposta

Armazenamento local sem conta/servidor. Métrica principal é tempo protegido com definição transparente; créditos são opcionais. Evitar recompensas que incentivem passar mais tempo no aplicativo de distração.
