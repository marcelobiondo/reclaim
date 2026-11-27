# Arquitetura / feasibility-first

## Decisão inicial
iOS nativo com Swift e SwiftUI. Regras isoladas do SDK Apple, permitindo futura versão Android nativa (Kotlin + Jetpack Compose). Não prometer base de código única.

## Componentes planejados
- **App SwiftUI:** onboarding, autorização, rotinas, dashboard, configurações.
- **Domain:** Routine, ProtectionSession, CreditLedgerEntry, CreditPolicy, ProtectionEvent.
- **Use cases:** ActivateRoutine, PauseProtection, CalculateEligibleMinutes, RedeemCredit.
- **Apple adapters:** FamilyControls / FamilyActivityPicker, ManagedSettings (shields), DeviceActivity (schedule/monitor).
- **Extensões (a validar):** DeviceActivityMonitor extension, ShieldConfiguration extension, ShieldAction extension.
- **Storage:** SwiftData para dados próprios; App Group para estado mínimo compartilhado entre app e extensões; verificar quais tipos/tokens podem ser serializados com segurança.
- **Clock abstraction:** fonte de horário injetável para testes de virada de dia, fuso e horário de verão.

## Modelo conceitual (não é schema definitivo)
```
Routine: id, title, kind, weekdaySet, startTime, endTime, selectionReference, enabled
ProtectionSession: id, routineId, start, end?, state, observedEvidence, interruptionReason?
CreditPolicy: earnMinutesPerCredit, redeemMinutesPerCredit, caps?, enableRedemption
CreditLedgerEntry: id, timestamp, delta, reason, referenceId, idempotencyKey
ProtectionEvent: timestamp, type, routineId, source, detail
```

Saldo = soma dos lançamentos do ledger; nunca atualizar diretamente um contador como fonte de verdade. Os eventos devem ser idempotentes para evitar crédito duplicado após callbacks/restarts.

## Spike técnico antes da UI
1. Conferir signing e capability Family Controls / autorização individual em aparelho real.
2. Testar autorização concedida, negada e revogada.
3. Selecionar Instagram (token via picker, sem depender de bundle IDs).
4. Aplicar e remover shield manualmente.
5. Testar agenda recorrente e chamadas das extensões com app fechado.
6. Testar comportamento atravessando meia-noite, reboot, mudança de hora e conflito entre rotinas.
7. Verificar possibilidade de uma pausa temporária e rebloqueio consistente.
8. Registrar sinais observáveis e lacunas: **não presumir** detecção de cada abertura ou tempo poupado.
9. Verificar os requisitos de entitlement e distribuição (desenvolvimento pessoal vs TestFlight/App Store).

## Critérios de arquitetura
- Sem rede obrigatória, sem analytics externos ou login.
- Cálculo de créditos separado do monitoramento.
- Nenhum bypass inseguro ou uso de APIs privadas.
- Proteger privacidade dos tokens e não tentar reconstruir identidade dos apps selecionados por métodos não autorizados.
- Testes unitários para sobreposição de rotinas, zonas horárias, limites, resgate e idempotência.

## Referências oficiais
- https://developer.apple.com/documentation/familycontrols
- https://developer.apple.com/documentation/managedsettings
- https://developer.apple.com/documentation/deviceactivity
- https://developer.apple.com/documentation/managedsettingsui

## Limitação
Este arquivo documenta a proposta. Disponibilidade de callbacks, métricas e regras de distribuição ainda **não foi validada** no dispositivo.
