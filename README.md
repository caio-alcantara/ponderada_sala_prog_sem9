# Ponderada de Sala - Programação - Semana 09
Ponderada de programação da semana 09, módulo 04, onde o objetivo era listar e documentar vulnerabilidades de segurança que o nosso dispositivo IOT contém, como podem ser exploradas, e como podemos resolvê-las

&emsp;A segurança em IoT (Internet das Coisas) é essencial para proteger dispositivos conectados e os dados que eles geram, transmitem e armazenam. Os principais desafios incluem a vulnerabilidade dos dispositivos, falta de padrões de segurança, ataques como DDoS e malware, e a complexidade de gerenciar redes heterogêneas.

# Atividade de Cibersegurança no Projeto

## Tabela de Vulnerabilidades

| **Vulnerabilidade**                           | **Grau de Impacto** | **Possível Ataque**                                                                                                       | **Responsável** |
|-----------------------------------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------|-----------------|
| SQL Injection                                 | Alto                | Utilização de comandos SQL para manipulação de dados no banco, podendo alterar ou excluir dados.                          | Kaio            |
| Brecha do Broker                              | Alto                | Envio de informações falsas ao tópico do broker, comprometendo a integridade do banco de dados.                          | Kaio            |
| Broker MQTT Público                           | Baixo               | Escuta de mensagens por terceiros não autorizados.                                                                       | Caio            |
| Tópicos MQTT sem autenticação                 | Alto                | Envio de dados falsos ou maliciosos ao tópico do dispositivo.                                                             | Caio            |
| Informações sendo exibidas na porta serial    | Baixo               | Leitura de informações sensíveis conectando-se fisicamente ao dispositivo.                                               | Caio            |
| Possibilidade de injeção de comandos/códigos  | Alto                | Alteração do funcionamento primário através de comandos maliciosos.                                                      | Mariana         |
| Autenticação inexistente na dashboard         | Alto                | Acesso não autorizado e uso de phishing para captura de credenciais.                                                     | Mariana         |
| APIs expostas                                 | Médio               | Acesso não autorizado ou deturpação de dados através de APIs sem autenticação adequada.                                   | Mariana         |
| Possibilidade de desligar o dispositivo físico| Alto                | Desligamento manual do dispositivo, interrompendo o monitoramento da floresta.                                           | Mariella        |
| Erro na coleta dos dados por causa maligna    | Baixo               | Manipulação de sensores para fornecer dados incorretos.                                                                  | Fidelis         |
| Wi-Fi hard coded no código                    | Alto                | Rede invadida devido ao armazenamento de credenciais no código público.                                                  | Fidelis         |
| Falta de criptografia nos dados               | Alto                | Captura de dados sensíveis transmitidos entre dispositivos ou armazenados localmente.                                     | Preto           |

## Plano de Ação para Correção das Vulnerabilidades

1. **SQL Injection**  
   - Implementar validação e sanitização de dados recebidos utilizando frameworks específicos.
   - Utilizar queries parametrizadas ou ORM como Sequelize ou SQLAlchemy.

2. **Brecha do Broker**  
   - Configurar um broker MQTT privado com autenticação baseada em credenciais.
   - Habilitar criptografia TLS/SSL para as mensagens.

3. **Broker MQTT Público e Tópicos sem Autenticação**  
   - Migrar para um broker privado.
   - Implementar autenticação e controle de acesso por tópico.

4. **Informações sendo exibidas na Porta Serial**  
   - Desabilitar logs em produção.
   - Filtrar informações sensíveis nos logs.

5. **Possibilidade de Injeção de Comandos**  
   - Usar sanitização para entradas de usuários e validação de códigos executáveis.

6. **Autenticação inexistente na Dashboard**  
   - Implementar autenticação robusta com MFA e restrições baseadas em papéis.

7. **APIs Expostas**  
   - Configurar autenticação JWT e validação rigorosa de dados.

8. **Possibilidade de Desligar o Dispositivo Físico**  
   - Adicionar sensores de interrupção para alertar o dashboard em caso de desconexão.

9. **Erro na Coleta dos Dados**  
   - Implementar algoritmos para validação cruzada de leituras dos sensores.

10. **Wi-Fi Hard Coded no Código**  
    - Adotar gerenciadores de segredo como AWS Secrets Manager.

11. **Falta de Criptografia nos Dados**  
    - Implementar criptografia de ponta a ponta (E2EE) usando AES-256.

## Contribuições dos Participantes

- **Kaio**: Identificação e descrição de vulnerabilidades relacionadas ao SQL Injection e brechas no broker MQTT.
- **Caio**: Análise de tópicos MQTT e segurança na porta serial.
- **Mariana**: Avaliação de problemas em APIs, autenticação e injeção de comandos.
- **Mariella**: Identificação de riscos relacionados à manipulação física do dispositivo.
- **Fidelis**: Relatos sobre coleta de dados maliciosos e credenciais Wi-Fi expostas.
- **Preto**: Análise do impacto da ausência de criptografia nos dados transmitidos.
