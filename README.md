# Avaliação Prática 06 — Configuração de VLANs tipo Acesso
1. Objetivo
Configurar duas VLANs nos switches da Camada de Acesso do ambiente hierárquico simulado no Cisco Packet Tracer.

A atividade estabelece a seguinte divisão:
- VLAN 10 — ALUNOS: portas ímpares de acesso conectadas aos computadores.
- VLAN 20 — VISITANTES: portas pares de acesso conectadas aos notebooks.
2. Topologia utilizada
A topologia possui quatro switches na camada de acesso:
- ACESSO0
- ACESSO1
- ACESSO2
- ACESSO3
Cada switch conecta computadores e notebooks. Os computadores pertencem à VLAN 10 (ALUNOS), enquanto os notebooks pertencem à VLAN 20 (VISITANTES).
<img width="508" height="352" alt="image" src="https://github.com/user-attachments/assets/2f5c7d9d-2794-4cc2-8928-770f5610e6f3" />

3. Identificação das VLANs

| ID da VLAN | Nome | Dispositivos associados |
|---|---|---|
| 10 | ALUNOS | Computadores (PCs) |
| 20 | VISITANTES | Notebooks |

4. Mapeamento das portas
A atividade determina que as portas ímpares conectadas aos computadores sejam associadas à VLAN 10 e as portas pares conectadas aos notebooks sejam associadas à VLAN 20.

| Switch | Dispositivo | Interface física | VLAN |
|---|---|---|---|
| ACESSO0 | PC0 | Fa0/1  | 10 — ALUNOS |
| ACESSO0 | Laptop0 | Fa0/2  | 20 — VISITANTES |
| ACESSO1 | PC1 | Fa0/1 | 10 — ALUNOS |
| ACESSO1 | Laptop1 | Fa0/2 | 20 — VISITANTES |
| ACESSO2 | PC2 | Fa0/1 | 10 — ALUNOS |
| ACESSO2 | Laptop2 | Fa0/2  | 20 — VISITANTES |
| ACESSO3 | PC3 | Fa0/1  | 10 — ALUNOS |
| ACESSO3 | Laptop3 | Fa0/2  | 20 — VISITANTES |

5. Configuração das portas de acesso
A configuração deve ser aplicada às portas dos switches que estiverem conectadas aos dispositivos finais. Conforme a regra da atividade, portas ímpares são destinadas aos computadores (VLAN 10) e portas pares aos notebooks (VLAN 20).

5.1. Porta conectada a um computador — VLAN 10
Exemplo para a interface FastEthernet0/1:
| Etapa | Comando Cisco IOS | Finalidade |
|---|---|---|
| 1 | `interface fastEthernet 0/1` | Selecionar a porta Fa0/1 do switch. |
| 2 | `switchport mode access` | Definir a interface como porta de acesso. |
| 3 | `switchport access vlan 10` | Associar a porta à VLAN 10 (ALUNOS). |
| 4 | `no shutdown` | Habilitar administrativamente a interface. |
| 5 | `exit` | Sair da configuração da interface. |

5.2. Porta conectada a um notebook — VLAN 20
Exemplo para a interface FastEthernet0/2:
| Etapa | Comando Cisco IOS | Finalidade |
|---|---|---|
| 1 | `interface fastEthernet 0/2` | Selecionar a porta Fa0/2 do switch. |
| 2 | `switchport mode access` | Definir a interface como porta de acesso. |
| 3 | `switchport access vlan 20` | Associar a porta à VLAN 20 (VISITANTES). |
| 4 | `no shutdown` | Habilitar administrativamente a interface. |
| 5 | `exit` | Sair da configuração da interface. |

Repita o procedimento em cada switch de acesso, substituindo as interfaces de exemplo pelas portas efetivamente conectadas aos computadores e notebooks. Não aplique essa configuração às portas de interligação entre switches, pois elas serão tratadas na Avaliação 07.

6. Salvar a configuração
Após criar as VLANs e configurar as portas de acesso em cada switch, execute os comandos abaixo:


| Etapa | Comando Cisco IOS | Finalidade |
|---|---|---|
| 1 | `end` | Sair do modo de configuração e retornar ao modo EXEC privilegiado. |
| 2 | `copy running-config startup-config` | Salvar a configuração atual para que seja mantida após reiniciar o switch. |
7. Verificação da configuração
Execute os comandos em cada switch de acesso.

Conferir as VLANs e as portas associada

| `show vlan brief` |

O resultado deve apresentar a VLAN 10 (ALUNOS) e a VLAN 20 (VISITANTES), com as portas de acesso correspondentes.

Conferir uma interface específica

| `show interfaces fastEthernet 0/1 switchport` |

Troque 0/1 pela porta que deseja verificar, como 0/2 ou 0/3.

Conferir a configuração em execução

| `show running-config` |

8. Testes de conectividade
Nos computadores e notebooks, a interface de rede utilizada é Fa0. Para testar a comunicação, abra o Prompt de Comando do dispositivo e utilize ping seguido do endereço IP de destino.


Endereços informados:

192.168.0.1

192.168.0.2

192.168.0.3

192.168.0.4

192.168.0.5

192.168.0.6

192.168.0.7

192.168.0.8

192.168.0.9

Para validar a separação por VLAN, priorize testes entre dispositivos pertencentes à mesma VLAN. A comunicação entre VLAN 10 e VLAN 20 depende de roteamento entre VLANs; a configuração de portas de acesso, sozinha, não realiza esse roteamento.
