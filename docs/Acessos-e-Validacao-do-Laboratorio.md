# Acessos e validação do laboratório

[Voltar à apresentação](../README.md) · [Arquitetura](Arquitetura-da-Infraestrutura.md)

Este roteiro adapta os procedimentos documentados para um ambiente próprio. Pressupõe servidor, conta autorizada, SSH por chave e compartilhamento já configurados. A instalação completa desses serviços não está coberta por esta versão.

## 1. Defina os papéis da rede

Identifique o gateway, quem fornece DHCP e a função de cada equipamento intermediário. Se um segundo roteador for usado como AP, confira o modo suportado pelo fabricante e evite dois equipamentos respondendo pelo mesmo endereço.

Registre os endereços atribuídos e como serão mantidos. Receber um endereço por DHCP não comprova reserva ou IP estático.

## 2. Use um alias SSH local

Exemplo ilustrativo de entrada no arquivo de configuração do cliente SSH:

```sshconfig
Host servidor-exemplo
    HostName 192.0.2.10
    User operador
    IdentityFile ~/.ssh/chave_do_laboratorio
    IdentitiesOnly yes
```

O endereço pertence a uma faixa de documentação: substitua-o pelo destino autorizado. O caminho da chave representa uma chave já provisionada; o arquivo privado permanece protegido na máquina de origem.

Confira a identidade do servidor por um canal confiável antes de aceitar sua chave de host. Depois de conectar, confirme o ambiente antes de operar:

```bash
ssh servidor-exemplo
hostname
pwd
id
```

Quando houver falha, diferencie resolução de nome, rota, disponibilidade da porta e autenticação. Trocar uma chave não corrige um problema de rede.

## 3. Conecte o compartilhamento privado

No caso documentado, o acesso usa SMB3 com assinatura e criptografia, restrição de origem e permissões no servidor. A credencial do compartilhamento é independente da conta Linux e fica no armazenamento protegido do Windows.

O alias definido no arquivo de configuração SSH é usado apenas pelo cliente SSH. Um nome usado pelo SMB ou pelo teste TCP precisa resolver por DNS ou por outro mecanismo do sistema. Para manter o exemplo independente dessa resolução, os comandos abaixo usam o mesmo IP ilustrativo; substitua-o pelo endereço autorizado.

Com o compartilhamento já preparado e a credencial cadastrada, um exemplo de mapeamento é:

```powershell
Test-NetConnection 192.0.2.10 -Port 445
net use X: "\\192.0.2.10\documentacao" /persistent:yes
Get-SmbMapping -LocalPath 'X:'
```

Se houver recusa após mudança de endereço do cliente, compare a origem atual com as permissões do compartilhamento e do firewall. O caso registrado foi resolvido ajustando somente essas regras específicas.

## 4. Confira a mesma origem dos arquivos

Crie um pequeno arquivo temporário de teste na pasta compartilhada e confira se o Linux lê o mesmo conteúdo. Compare os hashes usando o caminho correspondente em cada máquina:

```powershell
Get-FileHash -Algorithm SHA256 'X:\validacao-laboratorio.txt'
```

```bash
sha256sum /caminho/compartilhado/validacao-laboratorio.txt
```

Edite pelo outro lado, confira a alteração e remova somente o arquivo criado para o teste. A configuração documentada também testa o bloqueio de diretórios sensíveis e de links simbólicos.

## 5. Abra a documentação e observe o carregamento

Aponte o Obsidian para a pasta mapeada. Separe a disponibilidade de um arquivo pequeno do tempo necessário para ler todo o acervo. Registre a etapa lenta, o caminho da rede e a condição em que o teste foi feito.

A atualização de notas externas e a reescrita de links são operações diferentes: detectar uma renomeação não corrige automaticamente os links antigos.
