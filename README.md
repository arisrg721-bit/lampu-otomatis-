// pin sensor
const int trigPin = 7;
const int echoPin = 8;

// pin led
const int led1 = 4;
const int led2 = 5;
const int led3 = 6;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);

  int distance = duration * 0.034 / 2;

  Serial.print("Jarak: ");
  Serial.print(distance);
  Serial.println(" cm");

  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);

  if (distance >= 1 && distance <= 24) { // jika jarak 1 cm - 24 cm led1 menyala
    digitalWrite(led1, HIGH);
  } else if (distance >= 25 && distance <= 49) { // jika jarak 25 cm - 49 cm led2 menyala
    digitalWrite(led2, HIGH);
  } else if (distance >= 50 && distance <= 99) { // jika jarak 50 cm - 99 cm led3 menyala
    digitalWrite(led3, HIGH);
  }

  delay(200); 
}
