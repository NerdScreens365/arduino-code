int led = 6;
const int botaoPin = 2;
bool botaoPressionado = false;

void setup() {
  pinMode(botaoPin, INPUT_PULLUP);
  Serial.begin(9600);
  pinMode(led, OUTPUT); // Configura o pino do LED como saída
}

void loop() {
  digitalWrite(led, HIGH);
  delay(500);
  digitalWrite(led, LOW);
  delay(500);

  // Verifica o estado do botão dentro do loop
  if (digitalRead(botaoPin) == LOW) {
    botaoPressionado = true;
  }

  if (!botaoPressionado) {
    digitalWrite(led, LOW);
  }

  // Verifica se o botão foi liberado para permitir a próxima ação
  if (digitalRead(botaoPin) == HIGH) {
    botaoPressionado = false;
  }
}
