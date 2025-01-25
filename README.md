# Chat Multicast Criptografado
Este projeto é uma implementação de um sistema de comunicação seguro utilizando técnicas de criptografia para garantir a confidencialidade das mensagens trocadas entre os participantes do grupo multicast. composto por dois componentes principais: `MulticastChat` e `ServerChaves`.

## MulticastChat
Um aplicativo de chat que utiliza o protocolo multicast para comunicação em grupo. As mensagens trocadas no grupo são protegidas por criptografia simétrica (AES) no modo CBC, utilizando uma chave de 256 bits gerada a partir de um password com o protocolo KDF2.

### Estrutura de MulticastChat
src/udpmulticast/UDPMulticast.java: Implementa a lógica principal do cliente multicast, incluindo a geração de chaves, criptografia e descriptografia de mensagens, e a comunicação com o servidor de chaves.
src/udpmulticast/Connection.java: Gerencia a recepção de mensagens no grupo multicast, descriptografando e exibindo as mensagens recebidas.

## ServerChaves
Servidor que gerencia a troca de chaves simétricas entre os clientes antes de eles se juntarem ao grupo multicast. A comunicação entre o cliente e o servidor de chaves é protegida por criptografia assimétrica (RSA).

### Estrutura do Projeto
src/serverchaves/ServidorTCP.java: Implementa a lógica do servidor, incluindo a geração de chaves assimétricas, a recepção de chaves públicas dos clientes, e o envio de chaves simétricas criptografadas para os clientes.

## Funcionamento
- Geração de Chaves: O cliente gera um par de chaves RSA (pública e privada) e uma chave simétrica AES.
- Troca de Chaves: O cliente se conecta ao ServerChaves via TCP, envia sua chave pública e recebe a chave simétrica criptografada com a chave pública do servidor.
- Comunicação Multicast: O cliente se junta ao grupo multicast utilizando a chave simétrica para criptografar e descriptografar as mensagens trocadas no grupo.

Trabalho feito para Disciplina de Segurança Computacional - 2023.1.
