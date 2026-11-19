# Experiência com rede e documentação

[Voltar à apresentação](../README.md) · [Estado documentado](Estado-e-Limites-da-Infraestrutura.md)

Dois problemas mostram por que a infraestrutura precisa acompanhar as automações.

## Gateway duplicado — outubro de 2026

O roteador principal e o equipamento usado como AP respondiam pelo mesmo endereço. Isso podia associar o gateway ao equipamento errado e interromper o acesso IPv4, enquanto alguns caminhos IPv6 ainda funcionavam.

A intervenção separou o endereço administrativo do AP, preservou sua função de ponte e manteve apenas o roteador principal como fornecedor de DHCP. A documentação registra testes de ARP, DHCP, conectividade externa e permanência da configuração após reinício.

O resultado corrigiu o conflito de endereço. O limite de 100 Mb/s das portas do AP continuou existindo; resolver endereçamento não aumenta a capacidade do enlace. Também ficou registrada uma falha específica de IPv6 pelo Wi-Fi do servidor, sem causa estabelecida naquele trabalho.

## Arquivos lentos no Obsidian — novembro de 2026

O problema parecia estar no aplicativo, mas as medições por etapa mostraram o maior tempo na leitura de arquivos.

O notebook resolvia o endereço Ethernet do servidor para a interface Wi-Fi. As duas interfaces estavam na mesma sub-rede, e a política ARP permitia essa associação. A correção documentada ajustou respostas e anúncios ARP por interface, sem reiniciar a rede ou desativar a proteção do SMB.

Uma medição histórica de abertura caiu de aproximadamente 104 para 15 segundos após a correção. Outras condições de abertura voltaram a apresentar lentidão; esse resultado representa aquele teste e não uma garantia de desempenho contínuo.

## Origem autorizada e endereço do cliente

Em outra ocorrência, o endereço do notebook mudou por DHCP. O mapeamento persistente e a credencial do Windows continuavam cadastrados, mas as regras de acesso ainda permitiam apenas a origem anterior.

A recuperação manteve a autenticação existente, atualizou as permissões específicas e comparou os mesmos arquivos no Windows e no Linux. Isso separou um problema de autorização de rede de um problema de senha.

## O que esses casos acrescentam ao meu método

O valor está em medir o caminho completo: equipamento, protocolo, permissões, arquivo e aplicativo. Os registros preservam o que foi alterado, como voltar e quais testes realmente foram feitos.

A infraestrutura permitiu conectar projetos maiores, como o [Factorio — Durkh Coop](https://github.com/DURKHEIM09/factorio-durkh-coop). Ela também trouxe trabalho de manutenção que não aparece apenas no código das automações.
