Disciplina: **ENE0011 – Laboratório de Redes**  
Curso: **Engenharia de Redes de Comunicação**  
Instituição: **Universidade de Brasília (UnB)**  
Departamento: **Engenharia Elétrica** 

Professor Responsável: **Prof. Dr. Laerte Peotta de Melo**

# Relatório do Experimento "X"

## Identificação
- Nome: João Victor Machado Santos
- Matrícula: 23201318
- Turma: 01

## Objetivo


## Ambiente experimental

- Cisco IOL
- 2 máquinas linux com a imagem do tinycore

## Procedimentos

Primeiro foram adicionados os Nodes. Em seguida foram utilizados os comandos cisco para configurar os gateways. Comandos utilizados [hostname, interface eth 0/X, ip address 192.168.X.1 255.255.255.0, no shutdown, no ip routing]. Em seguida, foram atríbuidos endereços IP a cada host linux.

X ∈ {10,20}
## Resultados e evidências

<p align="center">
  <img src="https://github.com/user-attachments/assets/84e967ab-f395-4477-9ed4-9cc794d04dd8" alt="Topologia desenvolvida">
  <br>
  <em>Figura 1 – Topologia utilizada no experimento com dois hosts e dois gateways Cisco IOL.</em>
</p>

Com o Tiny Core foi atribuido um IP à cada host.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fdf5d66c-fbf9-4102-9c5f-8efc491c70f8" alt="Configuração dos hosts">
  <br>
  <em>Figura 2 – Configuração dos hosts.</em>
</p>

Utilizando o Host B. Repare na <b>Figura 2</b> que ela pinga seu Gateway porém não pinga o outro Host. Isso se deve ao fato de que mesmo que os dois PCs estejam conectados fisicamente ao mesmo switch ou roteador, eles não conseguem se comunicar diretamente porque pertencem a redes lógicas diferentes.


## Análise técnica

<b>Teste de conectividade SEM roteamento
  -  O enlace físico funciona? O IP está configurado corretamente? <br>
O teste confirmou que o enlace físico e as configurações IP estavam corretos (ping para o gateway funcionou).
- Por que o pacote não chega ao Host B? <br>
A falha entre hosts ocorreu pela ausência de roteamento: o roteador não encaminhava pacotes entre suas interfaces e os hosts não sabiam como alcançar a outra rede.

<b>Teste de conectividade COM roteamento:</br>
- 

## Conclusão

O roteador é essencial para interconectar redes, atuando no plano de dados (encaminhamento) e plano de controle (tabela de rotas). A falha inicial foi corretamente identificada como problema de roteamento, não físico.

