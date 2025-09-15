const int trigPin = 7;
const int echoPin = 8;

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

  if (distance >= 2 && distance <= 24) {
    digitalWrite(led1, HIGH);
  } else if (distance >= 25 && distance <= 49) {
    digitalWrite(led2, HIGH);
  } else if (distance >= 50 && distance <= 99) {
    digitalWrite(led3, HIGH);
  }

  delay(200); 
}
