# Laboratório: Tratamento de Incidentes de Segurança

**Cisco Networking Academy · Programa Mulher Digital (Junior Achievement Américas) · Novembro de 2026**

Laboratório prático de resposta a incidentes. Nele, apliquei o ciclo de tratamento de incidentes da **NIST SP 800-61r2** a dois cenários simulados. Em cada etapa, formulei as perguntas que a equipe de resposta precisa fazer, levando em conta o porte da organização, o modelo de CSIRC e as metodologias usadas pelos analistas.

📽️ **Apresentação:** [lab-tratamento-incidentes.pdf](lab-tratamento-incidentes.pdf)

---

## Sumário

1. [Objetivo](#objetivo)
2. [Referencial: o ciclo da NIST SP 800-61r2](#referencial-o-ciclo-da-nist-sp-800-61r2)
3. [Cenário 1: Worm e agente de DDoS](#cenário-1-worm-e-agente-de-ddos)
4. [Cenário 2: Acesso não autorizado à folha de pagamento](#cenário-2-acesso-não-autorizado-à-folha-de-pagamento)
5. [Comparação entre os cenários](#comparação-entre-os-cenários)
6. [O que aprendi](#o-que-aprendi)
7. [Referências](#referências)

---

## Objetivo

Aplicar os procedimentos de tratamento de incidentes de segurança para formular perguntas sobre cenários de incidentes, em cada etapa do processo de resposta.

## Referencial: o ciclo da NIST SP 800-61r2

| Etapa | Foco |
|---|---|
| 1. Preparação | Políticas, equipe, ferramentas e prevenção antes do incidente |
| 2. Detecção e análise | Identificar o incidente, confirmar, medir o escopo e priorizar |
| 3. Contenção, erradicação e recuperação | Limitar o dano, remover a causa e restaurar o ambiente |
| 4. Atividade pós-incidente | Lições aprendidas, retenção de evidências e melhoria contínua |

---

## Cenário 1: Worm e agente de DDoS

### Resumo

| | |
|---|---|
| **Organização** | Pequena empresa de investimento familiar, um único local, menos de 100 funcionários |
| **Incidente** | Um novo worm se espalha por mídia removível e se copia para compartilhamentos abertos do Windows. Cada host infectado recebe um agente de DDoS |
| **Agravante** | As assinaturas de antivírus só ficaram disponíveis horas depois. A infecção já estava generalizada |
| **Equipe** | Pequena equipe de especialistas contratada, que usa o **Modelo Diamante** |

### Perguntas por etapa

#### 1. Preparação
- A empresa trataria esse caso como incidente? Se sim, qual política de resposta se aplica?
- Existe um plano de resposta e alguém responsável por acionar a equipe externa contratada?
- O que já existia para prevenir esse tipo de ataque? Por exemplo: bloqueio de mídia removível, compartilhamentos do Windows restritos, antivírus centralizado e atualizado.
- Há inventário atualizado dos hosts e da rede para saber o que pode ser afetado?
- Os funcionários sabem a quem avisar quando um computador se comporta de forma estranha?
- Existe contrato ou acordo com o provedor de internet para ajudar caso o tráfego de DDoS saia da rede da empresa?

#### 2. Detecção e análise
- Quais sinais indicaram o incidente? Antivírus, lentidão, tráfego de rede incomum, relato de funcionário?
- Quais ferramentas de monitoramento podem confirmar a infecção, como logs, IDS e análise de tráfego?
- Quantos hosts e quais compartilhamentos estão infectados? Como identificar o paciente zero e a mídia de origem?
- O agente de DDoS já está ativo? Contra quais alvos, e a empresa pode ser vista como origem de um ataque contra terceiros?
- Quais dados de clientes e sistemas financeiros estão expostos ou correm risco?
- Qual a prioridade do incidente, considerando o impacto no negócio e a velocidade de propagação?
- Quem precisa ser avisado agora: diretoria, equipe externa, provedor de internet, clientes?

#### 3. Contenção, erradicação e recuperação
- Qual estratégia de contenção usar: desconectar os hosts infectados, segmentar a rede, bloquear o tráfego de saída do DDoS?
- Como impedir a propagação enquanto não há assinatura de antivírus? Por exemplo: bloquear portas USB e fechar compartilhamentos.
- Como identificar com segurança todos os hosts infectados, inclusive notebooks que estavam fora da rede?
- Quais evidências preservar antes de limpar as máquinas: amostra do worm, logs, imagens de disco?
- Como remover o worm e o agente: limpeza com antivírus atualizado ou reinstalação do sistema?
- Como confirmar que a erradicação funcionou antes de reconectar os hosts?
- Qual a ordem de recuperação, começando pelos sistemas mais críticos para o negócio?

#### 4. Atividade pós-incidente
- Quem vai participar da reunião de lições aprendidas e quando?
- O que pode ser feito para evitar incidentes parecidos: política de mídia removível, revisão de compartilhamentos, atualização mais rápida de assinaturas?
- O que pode melhorar na detecção? Quanto tempo o worm se espalhou antes de ser percebido?
- O plano de resposta funcionou? A comunicação com a equipe externa foi rápida?
- Por quanto tempo as evidências serão guardadas?
- Quanto o incidente custou em horas paradas, equipe externa e dano à reputação?

### Modelo Diamante aplicado

| Vértice | Análise |
|---|---|
| **Adversário** | Desconhecido. Worm novo, possivelmente de propagação em massa, sem alvo específico |
| **Capacidade** | Worm que se propaga por mídia removível e compartilhamentos do Windows, mais um agente de DDoS instalado nos hosts |
| **Infraestrutura** | Mídias removíveis (pendrives), compartilhamentos de rede abertos e os próprios hosts infectados, usados como botnet |
| **Vítima** | A empresa de investimento, seus hosts e sua rede. Vítimas secundárias: os alvos externos do DDoS |

> **Observação:** a empresa é vítima e, ao mesmo tempo, pode virar origem de ataque contra terceiros. Isso aumenta o risco jurídico e de reputação.

---

## Cenário 2: Acesso não autorizado à folha de pagamento

### Resumo

| | |
|---|---|
| **Organização** | Hospital com unidades satélites, dezenas de locais e mais de 5.000 funcionários |
| **Modelo de CSIRC** | Equipes de resposta distribuídas, com uma equipe coordenadora. Monitoramento 24/7 parcialmente terceirizado para um **MSSP** |
| **Incidente** | Numa quarta à noite, uma administradora da folha de pagamento vê uma pessoa desconhecida sair correndo da sala dela. A estação ficou desbloqueada por poucos minutos, o sistema de folha continuava logado e o mouse parecia ter sido mexido |
| **Equipe** | Usa a **Cyber Kill Chain** e conhece o banco de dados **VERIS** |

### Perguntas por etapa

#### 1. Preparação
- A organização trataria esse caso como incidente? Qual política se aplica: segurança física, segurança da informação ou as duas?
- Existe política de bloqueio de tela obrigatório e de tempo limite de sessão nos sistemas sensíveis?
- Como a segurança física e a equipe de resposta se comunicam? Quem aciona quem?
- Quais são os papéis da equipe local, da equipe coordenadora e do MSSP neste caso? O contrato com o MSSP define isso?
- O sistema de folha de pagamento registra logs de auditoria detalhados das ações de cada usuário?
- Existem procedimentos e ferramentas de coleta forense prontos para uso?

#### 2. Detecção e análise
- O que aconteceu exatamente, e em que horário? Quanto tempo a estação ficou sem supervisão?
- Quais ações foram feitas no sistema de folha nesse intervalo? Algum dado foi consultado, alterado, exportado ou impresso?
- Os dados bancários de algum funcionário foram alterados para desviar salários?
- O que mostram os logs do sistema, da estação e da rede? Algum dispositivo USB foi conectado?
- O que as câmeras e os registros de acesso ao prédio mostram? A pessoa era funcionária ou visitante?
- O MSSP detectou algo fora do padrão nesse horário?
- Isso foi um caso isolado ou parte de algo maior? Outras estações foram acessadas?
- Quem precisa ser informado: equipe coordenadora, RH, jurídico, diretoria, polícia?

#### 3. Contenção, erradicação e recuperação
- A estação deve ser isolada da rede para preservar evidências? Como fazer isso sem perder dados da memória?
- Quais evidências coletar e em que ordem, seguindo a ordem de volatilidade: memória, processos, logs, disco?
- Como manter a cadeia de custódia, já que o caso pode acabar em processo judicial?
- A senha da administradora e outras credenciais expostas devem ser trocadas agora?
- Se houver alteração na folha, como reverter antes do próximo pagamento?
- Foi instalado algum software malicioso, como keylogger ou acesso remoto? Como confirmar que a estação está limpa?

#### 4. Atividade pós-incidente
- O que pode evitar que isso se repita: bloqueio automático de tela, controle de acesso físico às salas, treinamento?
- A comunicação entre segurança física, equipes distribuídas e MSSP funcionou bem?
- Quanto tempo levou entre o fato e o início da resposta?
- O incidente deve ser registrado no VERIS para gerar métricas e comparar com outros casos?
- Por quanto tempo guardar as evidências, considerando possíveis processos trabalhistas ou criminais?
- Os funcionários afetados precisam ser avisados? Existe obrigação legal de comunicar a autoridade de proteção de dados?

### Cyber Kill Chain aplicada

| Etapa | Análise do cenário | Status |
|---|---|---|
| 1. Reconhecimento | O invasor pode ter observado a rotina da administradora e o acesso à sala | 🟡 Hipótese |
| 2. Armamento | Possível preparação de pendrive com ferramenta de coleta ou de acesso remoto | 🟡 Hipótese |
| 3. Entrega | Acesso físico à sala e à estação desbloqueada | 🔵 Relatado |
| 4. Exploração | Uso da sessão já logada no sistema de folha, sem precisar de senha | 🔵 Relatado |
| 5. Instalação | Keylogger, software de acesso remoto ou nenhuma instalação | 🟠 Investigar |
| 6. Comando e controle | Conexões de rede saindo da estação após o incidente | 🟠 Investigar |
| 7. Ações no objetivo | Possível consulta, cópia ou alteração de dados da folha de pagamento | 🟠 Investigar |

> **Observação:** a etapa de entrega foi física, não digital. O controle mais barato e eficiente aqui seria o bloqueio automático de tela.

---

## Comparação entre os cenários

| Aspecto | Cenário 1 | Cenário 2 |
|---|---|---|
| Porte | Pequena empresa, um local | Hospital com mais de 5.000 funcionários |
| Tipo de ameaça | Malware automatizado, sem alvo específico | Pessoa com acesso físico, possivelmente direcionado |
| Prioridade inicial | Conter a propagação | Preservar evidências |
| Modelo de CSIRC | Equipe externa pequena | Equipes distribuídas, equipe coordenadora e MSSP |
| Metodologia | Modelo Diamante | Cyber Kill Chain e VERIS |
| Controle-chave | Bloqueio de mídia removível | Bloqueio automático de tela |
| Principal lição | Prevenção técnica e detecção rápida | Controles simples de comportamento e segurança física |

## O que aprendi

1. **Fazer as perguntas certas vem antes de agir.** Cada etapa do ciclo tem decisões diferentes, e pular uma delas pode destruir evidências ou espalhar o problema.
2. **O contexto muda a prioridade.** No worm, o urgente é conter. No acesso à folha, o urgente é preservar provas.
3. **Segurança física também é segurança da informação.** Uma tela desbloqueada por poucos minutos foi suficiente para expor dados sensíveis.
4. **Comunicação é parte do plano.** Com equipes distribuídas e um MSSP, saber quem faz o quê evita atraso e retrabalho.
5. **Modelos ajudam a organizar o raciocínio.** O Modelo Diamante e a Cyber Kill Chain transformam um cenário confuso em perguntas objetivas.

## Referências

- NIST SP 800-61 Rev. 2: *Computer Security Incident Handling Guide*
- Cisco Networking Academy: CyberOps Associate, laboratório "Tratamento de Incidentes"
- Caltagirone, Pendergast e Betz: *The Diamond Model of Intrusion Analysis*
- Lockheed Martin: *Cyber Kill Chain*
- VERIS: *Vocabulary for Event Recording and Incident Sharing*

---

**Autora:** Bruna Grandes Rodrigues · Arquiteta e urbanista em transição para Cibersegurança (GRC)
📧 brunagrandesr@gmail.com
