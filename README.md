# Infraestrutura do meu laboratório

Minha infraestrutura é a base dos projetos de IA e automação que uso. Quando comecei a integrar IA ao Factorio, já tinha servidor, acesso remoto e documentação em Markdown; isso facilitou conectar as peças e testar ideias maiores.

Este repositório reúne a estrutura e os aprendizados desse laboratório pessoal: servidor Linux, notebook Windows, rede local, SSH e acesso aos mesmos documentos pelo Obsidian.

## O que organizei

| Parte | Papel |
| --- | --- |
| Servidor Linux | Mantém arquivos, sistemas e pontos de execução das automações. |
| Notebook Windows | Ambiente de trabalho e testes, com acesso ao servidor. |
| Rede local | Conecta os equipamentos por Ethernet e Wi-Fi. |
| SSH | Permite operação remota usando autenticação por chave. |
| Compartilhamento SMB3 | Disponibiliza arquivos do servidor ao Windows, com acesso privado e restrito. |
| Documentação | Registra decisões, operação e recuperação junto aos arquivos dos projetos. |

A separação entre infraestrutura, sistemas instalados e projetos próprios ajudou a dar um lugar claro para cada coisa. Os programas continuam nos seus caminhos nativos; os portais documentais apontam para eles.

## Por onde começar

- [Arquitetura e limites entre as camadas](docs/Arquitetura-da-Infraestrutura.md).
- [Roteiro de acesso e validação](docs/Acessos-e-Validacao-do-Laboratorio.md).
- [Problemas de rede e aprendizados](docs/Experiencia-com-Rede-e-Documentacao.md).
- [Estado documentado e próximos passos](docs/Estado-e-Limites-da-Infraestrutura.md).

## Projetos que usam essa base

- [Hermes e Durkh 509](https://github.com/DURKHEIM09/hermes-durkh-509): assistente pessoal e integrações.
- [Factorio — Durkh Coop](https://github.com/DURKHEIM09/factorio-durkh-coop): automação, relatórios e interação com o jogo.
- [Hermes Control](https://github.com/DURKHEIM09/hermes-control): painel complementar em desenvolvimento.
- [Neuro-Link e Obsidian](https://github.com/DURKHEIM09/neuro-link-obsidian): organização da documentação e uso de contexto por IA.
- [Sistemas e integrações](https://github.com/DURKHEIM09/sistemas-e-integracoes): o papel das ferramentas usadas no laboratório.

A publicação foi preparada em 19/11/2026 a partir da documentação existente. Os exemplos usam nomes e endereços ilustrativos. Os registros de testes representam as datas das intervenções, sem uma nova inspeção dos serviços nesta publicação.
