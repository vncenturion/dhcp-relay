# DHCP E DHCP-RELAY

    Atividade da disciplina de projeto de redes de computadores do Curso Superior de Tecnologia em Rede de Computadores do IFPB.

    O Protocolo de Configuração Dinâmica de Hosts (DHCP) é um protocolo de rede usado para atribuir endereços IP e fornecer informações de configuração a dispositivos como servidores, computadores desktop ou dispositivos móveis, para que possam se comunicar em uma rede usando o Protocolo de Internet (IP).
    
    O ISC DHCP é um conjunto de software que implementa todos os aspectos da suíte de protocolos DHCP (Dynamic Host Configuration Protocol).

    DESCRIÇÃO

    O Agente de DHCP-RELAY da Internet Systems Consortium, dhcrelay, fornece um meio de retransmitir solicitações DHCP e BOOTP de uma sub-rede para a qual nenhum servidor DHCP está diretamente conectado para um ou mais servidores DHCP em outras sub-redes. Ele oferece suporte aos protocolos DHCPv4/BOOTP e DHCPv6.

    OPERAÇÃO
    
    O Agente de DHCP-RELAY escuta por consultas DHCPv4 ou DHCPv6 de clientes ou de outros agentes de relevo em uma ou mais interfaces, repassando-as para servidores ou agentes DHCP-RELAY "montante" conforme especificado na linha de comando. Quando uma resposta é recebida do montante, ela é transmitida de volta "a jusante" para a origem da solicitação original, seja por multicast ou unicast.

## REQUISITOS DO PROJETO

   1. Sistema hospedeiro

   2. Máquinas virtuais 

## CENÁRIO PROPOSTO

    Um servidor DHCP conectado a um roteador que conecta duas sub-redes. A primeira sub-rede deverá conter um cliente Linux e o servidor DHCP. A segunda sub-rede conterá apenas um cliente Windows 10.

    O escopo para a primeira sub-rede terá parâmetros na rede 192.168.0.0/24 e o escopo da segunda sub-rede terá parâmetros na rede 172.16.0.0/16.

    Os parâmetros de cada escopo devem conter faixa de endereços para empréstimos e endereço da interface de rede do roteador padrão da sub-rede.

## CONFIGURAÇÃO DO DHPC


## CONFIGURAÇÃO DO AGENTE DHCP-RELAY
2. DHCP E DHCP-RELAY

3. 