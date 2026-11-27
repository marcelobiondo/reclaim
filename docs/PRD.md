# PRD — Reclaim (draft 0.1)

## Problema
Aberturas impulsivas de aplicativos e doomscrolling competem com tarefas e relações importantes. O usuário deseja estabelecer limites situacionais, com reforço positivo e feedback sem culpa.

## Público inicial
Uma pessoa adulta utilizando iPhone próprio. Não é um produto parental e não pressupõe controle de terceiros.

## Job to be done
Quando eu reservar um período para trabalhar, me exercitar ou estar presente com minha família, quero reduzir distrações dos apps que escolhi e entender meu progresso, para poder usar a tecnologia de forma intencional.

## Proposta
1. Criar rotinas com nome, horários, dias e seleção de apps/categorias.
2. Proteger esses horários com mecanismos do Screen Time quando autorizados.
3. Medir períodos protegidos conforme eventos verificáveis.
4. Mostrar progresso diário com linguagem precisa e encorajadora.
5. Explorar créditos opcionais para desbloquear tempo depois.

## Não objetivos (V1)
Lançamento comercial, rede social, gamificação competitiva, cobrança, conta, backend, sincronização multiaparelho, coleta remota de dados, IA generativa, promessa de diagnóstico ou tratamento.

## Personas e contextos (hipóteses)
- Trabalho: redes sociais restritas durante blocos de concentração.
- Vida pessoal: momentos de convivência sem distrações.
- Atividade física: sugerir uma atividade; não alegar que foi realizada sem declaração/integração explícita.

## Fluxo principal
Onboarding explicativo → autorização Screen Time → escolha dos apps → definição de rotina → ativação da proteção → escudo/fluxo de exceção → resumo diário.

## Requisitos P0
- R01: explicar de forma transparente o que o app pode e não pode monitorar.
- R02: solicitar autorização FamilyControls com tratamento de negativa/revogação.
- R03: selecionar apps/categorias via FamilyActivityPicker; persistir tokens de forma apropriada.
- R04: criar/editar/desativar rotina recorrente.
- R05: agendar proteção e aplicar/remover shields conforme viabilidade testada.
- R06: permitir acesso emergencial/pausa com feedback claro, sem aprisionamento.
- R07: exibir métricas com fonte/definição explícita; não confundir proteção agendada com foco realizado.
- R08: funcionar sem servidor e sem conta.

## Requisitos P1 (dependem do spike)
- R09: créditos obtidos por unidades de tempo realmente elegíveis, com contabilização robusta.
- R10: resgatar janela de acesso e reativar proteção ao término.
- R11: acompanhar histórico e oferecer sugestões configuráveis (sem inferir comportamento).
- R12: configurar economia: minutos/crédito, minutos/resgate, limites e exceções.

## Questões em aberto
- Definição exata de tempo elegível: intervalo com shield ativo? App sem uso? Foco voluntariamente confirmado?
- Abrir um aplicativo bloqueado gera evento observável suficiente para penalidade? Testar; não assumir.
- Como distinguir falha técnica, permissão revogada, interrupção manual e tempo concluído?
- Política de créditos: saldo máximo, expiração, resgates em horários permitidos, prevenção de incentivo a scroll.
- Quais telas são realmente necessárias para uso diário?
- Qual linguagem de proteção funciona sem julgamento ou ansiedade?

## Critérios de sucesso do MVP
- Configurar e cumprir pelo menos uma rotina em iPhone real.
- Bloqueio e encerramento previsíveis, inclusive quando app principal não está aberto.
- Dados recuperados corretamente após reinicialização.
- Usuário consegue pausar, cancelar ou revogar permissão sem perder controle.
- Visualização honesta: minutos agendados, minutos protegidos verificáveis e exceções, conforme dados disponíveis.

## Riscos
Limites de privacidade e APIs da Apple; entitlement necessário para algumas formas de distribuição; diferenças entre simulador e aparelho; extensões com restrições de execução; comportamentos de shield não equivalentes ao Screen Time nativo completo.
