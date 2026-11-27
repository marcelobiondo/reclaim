# Reclaim

> Recupere o controle do seu tempo.

**Status:** discovery / technical feasibility • **Plataforma inicial:** iOS • **Uso inicial:** pessoal

Reclaim é um experimento de bem-estar digital: ajudar uma pessoa a proteger momentos importantes (trabalho, atividade física e família), reduzir aberturas impulsivas de aplicativos e tornar visível o tempo protegido. Um sistema opcional de créditos poderá recompensar períodos concluídos e permitir resgates conscientes de uso.

## Princípios
- **Autonomia, não punição.** Pausas, exceções e desligamento devem ser claros.
- **Tempo protegido não é tempo produtivo comprovado.** Não afirmar que a pessoa trabalhou, treinou ou esteve com a família sem confirmação.
- **Privacidade primeiro.** Dados locais; sem conta, servidor, anúncios ou rastreamento na V1.
- **Simplicidade.** Resolver a necessidade de um único usuário antes de considerar escala.
- **Gamificação não compulsiva.** Créditos opcionais; não incentivar consumo só para gastar recompensas.
- **Viabilidade técnica antes do acabamento visual.** Validar as restrições reais do Screen Time no iPhone.

## Documentos
- [Visão e PRD](docs/PRD.md)
- [Arquitetura e viabilidade](docs/architecture.md)
- [Backlog e roadmap](docs/backlog.md)
- [Experimentação e case](docs/case.md)
- [Decisões técnicas e de produto](docs/decisions/README.md)
- [Contribuição e fluxo](CONTRIBUTING.md)

## Roadmap
0. **Spike técnico:** autorização individual; seleção de apps; shield, agendamento e extensão; liberação/rebloqueio.
1. **MVP:** rotina, proteção e dashboard diário confiável.
2. **Gamificação:** créditos, resgates, histórico e recomendações simples.
3. **Validação:** testar na rotina real e produzir case com evidências.

### Arquitetura pretendida
Swift + SwiftUI no iOS; regras de domínio separadas dos adaptadores para APIs da Apple. No futuro, Android com interface e integrações nativas próprias, compartilhando especificação e conceitos — não presumir código de UI multiplataforma.

> **Não existe app executável ainda.** Este repositório começa pela documentação e por uma prova de conceito no dispositivo físico. Nome e regras de recompensa são provisórios.
