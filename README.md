# DHCP E DHCP-RELAY

## INTRODUÇÃO 
    
   1. **DHCP**

        Atividade da disciplina de projeto de redes de computadores do Curso Superior de Tecnologia em Rede de Computadores do IFPB.

        O Protocolo de Configuração Dinâmica de Hosts (DHCP) é um protocolo de rede usado para atribuir endereços IP e fornecer informações de configuração a dispositivos como servidores, computadores desktop ou dispositivos móveis, para que possam se comunicar em uma rede usando o Protocolo de Internet (IP).
    
        O ISC DHCP é um conjunto de software que implementa todos os aspectos da suíte de protocolos DHCP (Dynamic Host Configuration Protocol).

   2. **DHCP-RELAY**

        **DESCRIÇÃO**

        O Agente de DHCP-RELAY da Internet Systems Consortium, dhcrelay, fornece um meio de retransmitir solicitações DHCP e BOOTP de uma sub-rede para a qual nenhum servidor DHCP está diretamente conectado para um ou mais servidores DHCP em outras sub-redes. Ele oferece suporte aos protocolos DHCPv4/BOOTP e DHCPv6.

        **OPERAÇÃO**
    
        O Agente de DHCP-RELAY escuta por consultas DHCPv4 ou DHCPv6 de clientes ou de outros agentes de relevo em uma ou mais interfaces, repassando-as para servidores ou agentes DHCP-RELAY "montante" conforme especificado na linha de comando. Quando uma resposta é recebida do montante, ela é transmitida de volta "a jusante" para a origem da solicitação original, seja por multicast ou unicast.

## REQUISITOS DO PROJETO

   3. **SISTEMA HOSPEDEIRO**

        VMWARE WORKSTATION 17.X
        IMAGENS UBUNTU 2023, KALI 2023 E WINDOWS10

        MÁQUINA HOST WINDOWS 11, PROCESSADOR 11th Gen Intel(R) Core(TM) i7-11800H @ 2.30GHz   2.30 GHz, MEMÓRIA RAM 16,0 GB (utilizável: 15,9 GB), Sistema operacional de 64 bits, processador baseado em x64. 

   4. **MÁQUINAS VIRTUAIS** 

        MÁQUINAS VIRTUAIS COM 2GB RAM E 2 PROCESSADORES PARA SERVIDOR DHCP, HOST E AGENTE DHCP FORAM CRIADOS CLONES DAS MÁQUINAS COM AS MESMAS CONFIGURAÇÕES.

## CENÁRIO PROPOSTO

   5. **TOPOLOGIA**

        Um servidor DHCP conectado a um roteador que conecta duas sub-redes. A primeira sub-rede deverá conter um cliente Linux e o servidor DHCP. A segunda sub-rede conterá apenas um cliente Windows 10.

   6. **ESCOPO DHCP**

        O escopo para a primeira sub-rede terá parâmetros na rede 192.168.0.0/24 e o escopo da segunda sub-rede terá parâmetros na rede 172.16.0.0/16.

        Os parâmetros de cada escopo devem conter faixa de endereços para empréstimos e endereço da interface de rede do roteador padrão da sub-rede.

## CONFIGURAÇÃO DA MV KALI (ATUANDO COMO ROTEADOR)

   7. Network adapters

        VMnet11 (ip estático): 192.168.0.1

        VMnet12 (ip estático): 172.16.0.1

        VMnet8 (nat) - opcional: escopo automático do VWware Workstation

   8. REGRAS DE IPTABLES

        sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -d 172.16.0.0/16 -j ACCEPT

        sudo iptables -A FORWARD -i eth1 -o eth0 -s 172.16.0.0/16 -d 192.168.0.0/24 -j ACCEPT

        sudo iptables -A INPUT -i eth0 -s 192.168.0.0/24 -j ACCEPT

        sudo iptables -A INPUT -i eth1 -s 172.16.0.0/16 -j ACCEPT

        sudo iptables -t nat -A POSTROUTING -o eth2 -s 192.168.0.0/24 -j MASQUERADE

        sudo iptables -t nat -A POSTROUTING -o eth2 -s 172.16.0.0/16 -j MASQUERADE

        Verificar interfaces do roteador caso necessário.

## CONFIGURAÇÃO DO DHPC

   10. INSTALANDO ISC-DHCP-SERVER

    ``` shell
        sudo apt-get update
        sudo apt-get install isc-dhcp-server
        

## CONFIGURAÇÃO DO AGENTE DHCP-RELAY

   9. DHCP E DHCP-RELAY

3. 