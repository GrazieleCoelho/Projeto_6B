# Projeto 6-B: **Sistema de Temporização de um Disparo de LEDs**
**EMBARCATECH - UNIDADE 04**

## Desenvolvedora
**Aluna Graziele Coelho de Alencar**

## Links: 
- Execução na BitDogLab:
https://drive.google.com/file/d/11KoGedWk1whBiqKaU15A6xvEROKsw3WM/view?usp=sharing

- Execução no Wokwi integrado no VS Code:
https://drive.google.com/file/d/1bYXTXM4NBNQ6uXbMYF7FmLMvKaMA1VpA/view?usp=sharing

## Descrição
Este projeto implementa um sistema de controle de LEDs utilizando o Raspberry Pi Pico e o Pico SDK. 
O sistema é controlado por um botão (GPIO 5), que inicia uma sequência de temporização para desligar três LEDs (Verde, Azul e Vermelho), com intervalos de 3 segundos entre cada etapa.

## Funcionamento
1. **Estado inicial:** Todos os LEDs estão desligados.
2. **Pressionar o botão:** Quando o botão é pressionado, todos os LEDs são acesos simultaneamente.
3. **Sequência de desligamento:**
   - Após 3 segundos, o **LED Verde** é desligado.
   - Após mais 3 segundos, o **LED Azul** é desligado.
   - Após mais 3 segundos, o **LED Vermelho** é desligado.
4. **Reinício:** Após o desligamento do último LED, o sistema está pronto para ser acionado novamente.

## Hardware Utilizado
- **Microcontrolador:** Raspberry Pi Pico
- **LEDs:**
  - LED Verde conectado ao GPIO 11
  - LED Azul conectado ao GPIO 12
  - LED Vermelho conectado ao GPIO 13
- **Botão (Pushbutton):**
  - Conectado ao GPIO 5
  - Configurado com resistor pull-up interno
- **Resistores de 330 Ω:** Utilizados em série com cada LED.

## Configuração dos Pinos

- LED Verde -> GPIO 11
- LED Azul -> GPIO 12
- LED Vermelho -> GPIO 13
- Botão -> GPIO 5

## Pré-requisitos
1. **Ferramentas necessárias:**
   - Raspberry Pi Pico.
   - Ambiente de desenvolvimento, como o VS Code, configurado com o Pico SDK, CMake** e GNU Make instalados.
2. **Hardware conectado:** Monte o circuito conforme a descrição.

## Instruções de Uso
### 1. Configurar o Ambiente de Desenvolvimento
- Certifique-se de que o Pico SDK está configurado corretamente em seu sistema.

### 2. Compilar e Carregar o Código
1. Clone o repositório (ou copie o código para um arquivo `main.c`).
2. Crie um diretório de build e compile o código.
3. Conecte o Raspberry Pi Pico ao computador no modo de Bootsel e copie o arquivo `.uf2` gerado para o dispositivo.

### 3. Executar o Sistema
- Após carregar o programa, pressione o botão conectado ao GPIO 5 para iniciar a sequência de LEDs.
- Acompanhe as mensagens no console serial para monitorar o status do sistema.

## Detalhes Técnicos
### Debounce
- O botão implementa **debounce por software** para ignorar acionamentos acidentais em intervalos inferiores a 50 ms.

### Sequência de Temporização
- Utiliza a função `add_alarm_in_ms` do Pico SDK para agendar callbacks:
  - **Callback 1:** Desliga o LED Verde e agenda o desligamento do LED Azul.
  - **Callback 2:** Desliga o LED Azul e agenda o desligamento do LED Vermelho.
  - **Callback 3:** Desliga o LED Vermelho e finaliza a sequência.

### Mensagens no Console Serial
- Durante a execução, mensagens informativas são enviadas ao console para facilitar o monitoramento do sistema.

## Exemplo de Saída no Console

- *Sistema de temporização de LEDs iniciado.*
- *Aguardando acionamento do botão...*
- *Botão pressionado! Iniciando sequência de LEDs...*
- *LED Verde desligado. Dois LEDs permanecem ligados (Azul e Vermelho).*
- *LED Azul desligado. Somente LED Vermelho permanece ligado.*
- *LED Vermelho desligado. Sequência finalizada.*
- *Aguardando acionamento do botão...*


## Observação
- Certifique-se de que todos os componentes estão conectados corretamente antes de executar o programa.
