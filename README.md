# 🌡️Termometro Ambiente com Arduino🤖

Um projeto simples e funcional para medir a temperatura ambiente usando o Arduino Uno e um sensor TMP36 (ou equivalente).
A leitura é exibida em tempo real em um display LCD 16x2.

## Como Funciona⚙️

O sensor TMP detecta a temperatura do ambiente e converte essa variação térmica em tensão analógica proporcional.
O Arduino lê essa tensão na porta analógica A0 e realiza a conversão para graus Celsius (°C).
Por fim, o valor é mostrado no display LCD, que atualiza a leitura a cada segundo.


## Materiais🧰


<img width="50%" alt="Imagem do WhatsApp de 2025-10-03 à(s) 09 32 58_2a1dab3c" src="https://github.com/user-attachments/assets/38bc4a1e-a806-4210-a9d3-f20986d93829" />


* Tela LCD 16x2

* Resistor de 220Ω

* Sensor de temperatura (TMP)

* Potênciometro

* Arduino Uno

## Montagem🛠️


<img width="50%" alt="Imagem do WhatsApp de 2025-10-03 à(s) 09 32 58_2a1dab3c" src="https://github.com/user-attachments/assets/11b58b02-15c0-4b9b-8999-c27e6e64cdd9" />


Monte o Arduino em uma protoboard e conecte suas linhas de energia, levando 5V e GND para os trilhos laterais. Posicione o display LCD 16x2 e o potenciômetro próximos, para facilitar as ligações do contraste. Coloque o sensor de temperatura na parte superior da protoboard, com os fios bem organizados.

Conecte o potenciômetro ao LCD para controlar o contraste e ligue a alimentação e o terra do display nos trilhos correspondentes. O sensor deve ser ligado à mesma linha de alimentação do Arduino, compartilhando o GND com os demais componentes.

Depois de tudo conectado, revise as ligações, garantindo que não haja fios soltos ou curtos. Em seguida, conecte o cabo USB ao Arduino para energizar o circuito e ajuste o potenciômetro até que o texto apareça corretamente no display.


## Esquema de Conexão⚡

**Sensor TMP**

| Componente         | Pino do Arduino |
| ------------------ | --------------- |
| VCC -> Sensor TMP  | 5V              |
| VOUT -> Sensor TMP | A0              |
| GND -> Sensor TMP  | GND             |


_________________________________________________________________________________________________________________________________________________________________________________

**LCD, nos outros componentes**

| Componente                  | Pino do Arduino       |
| --------------------------- | --------------------- |
| RS -> LCD                   | D12                   |
| E -> LCD                    | D11                   |
| D4 -> LCD                   | D5                    |
| D5 -> LCD                   | D4                    |
| D6 -> LCD                   | D3                    |
| D7 -> LCD                   | D2                    |
| V0 -> LCD (Contraste)       | Meio do potenciômetro |
| Potenciômetro -> Terminal 1 | GND                   |
| Potenciômetro -> Terminal 2 | 5V                    |

**Alimentação do LCD**

| Componente      | Pino do Arduino                    |
| --------------- | ---------------------------------- |
| VSS -> LCD      | GND                                |
| VDD -> LCD      | 5V                                 |
| A (LED+) -> LCD | 5V *(opcional – retroiluminação)*  |
| K (LED-) -> LCD | GND *(opcional – retroiluminação)* |

## Código💻

```
#include <LiquidCrystal.h>

// Inicializando o LCD (RS, E, D4, D5, D6, D7)
LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

const int sensorPin = A0;

void setup() {
  lcd.begin(16, 2); // Configura o LCD como 16 colunas e 2 linhas
  lcd.print("Inicializando...");
  delay(2000);
  lcd.clear();
}

void loop() {
  int sensorValue = analogRead(sensorPin);
  float voltage = sensorValue * (5.0 / 1023.0);  // Converte para tensão
  float temperature = voltage * 100;            // Converte para °C
  
  lcd.setCursor(0, 0);
  lcd.print("Temp: ");
  lcd.print(temperature);
  lcd.print(" C");
  
  delay(1000);
}
```
## Projeto no TinkerCAD❗

https://www.tinkercad.com/things/8bG02cF6Bpi-termometro-ambiente-
