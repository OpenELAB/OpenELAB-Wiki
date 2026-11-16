---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# 4 digit 7-segment LED Display

### 4 digit 7-segment LED Display

***

### Product Link

{% embed url="https://openelab.io/products/4digit7segmentleddisplay?_pos=1&_sid=a94b74fcb&_ss=r" %}

### Introduction

Supports display of English characters, Chinese characters and pictures. English characters have built-in ascii code, while Chinese characters and pictures need to be provided by users. Characters can be displayed normally or rotated 90 degrees counterclockwise. Pictures and Chinese characters are all modeled in vertical orientation, with the principle of high position on top, left before right, top before bottom. Support multi-layer, can operate on any layer individually. Layers can be added and removed at any time, the top layer is not allowed to be removed. The buf of multi-layer can be defined in data segment, bss segment and heap segment. Support drawing points, drawing lines, drawing function images, drawing lines and function images support complementary unconnected points. Drawing function adopts matlab-like function interface form. Support print function. Support all clear screen, part of the region clear screen function. Support full-screen rainbow image display function, convenient for testing.

<figure><img src="../../.gitbook/assets/image (785).png" alt=""><figcaption></figcaption></figure>

### Features

### Pinout

<figure><img src="../../.gitbook/assets/image (786).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (787).png" alt=""><figcaption></figcaption></figure>

### How to Use

{% code fullWidth="false" %}
```cpp
/*
2  Showing number 0-9 on a Common Anode 7-segment LED display
3  Displays the numbers 0-9 on the display, with one second inbetween.
4    A
5   ---
6F |   | B
7  | G |
8   ---
9E |   | C
10  |   |
11   ---
12    D
13  This example code is in the public domain.
14 */
15 
16// Pin 2-8 is connected  to the 7 segments of the display.
17
18int pinA = 2;
19int pinB = 3;
20int pinC  = 4;
21int pinD = 5;
22int pinE = 6;
23int pinF = 7;
24int pinG = 8;
25int  D1 = 9;
26int D2 = 10;
27int D3 = 11;
28int D4 = 12;
29
30// the setup routine  runs once when you press reset:
31void setup() {                
32  // initialize  the digital pins as outputs.
33  pinMode(pinA, OUTPUT);     
34  pinMode(pinB,  OUTPUT);     
35  pinMode(pinC, OUTPUT);     
36  pinMode(pinD, OUTPUT);     
37  pinMode(pinE, OUTPUT);     
38  pinMode(pinF, OUTPUT);     
39  pinMode(pinG,  OUTPUT);   
40  pinMode(D1, OUTPUT);  
41  pinMode(D2, OUTPUT);  
42  pinMode(D3,  OUTPUT);  
43  pinMode(D4, OUTPUT);  
44}
45
46// the loop routine runs over  and over again forever:
47void loop() {
48  digitalWrite(D1, HIGH);
49  digitalWrite(D2,  LOW);
50  digitalWrite(D3, LOW);
51  digitalWrite(D4, LOW); 
52  //0
53  digitalWrite(pinA,  LOW);   
54  digitalWrite(pinB, HIGH);   
55  digitalWrite(pinC, LOW);   
56  digitalWrite(pinD, LOW);   
57  digitalWrite(pinE, HIGH);   
58  digitalWrite(pinF,  LOW);   
59  digitalWrite(pinG, LOW);   
60  delay(1);               // wait for  a second
61  
62  digitalWrite(D1, LOW);
63  digitalWrite(D2, HIGH);
64  digitalWrite(D3,  LOW);
65  digitalWrite(D4, LOW); 
66  //1
67  digitalWrite(pinA, LOW);   
68  digitalWrite(pinB, LOW);   
69  digitalWrite(pinC, LOW);   
70  digitalWrite(pinD,  HIGH);   
71  digitalWrite(pinE, LOW);   
72  digitalWrite(pinF, LOW);   
73  digitalWrite(pinG, LOW);   
74  delay(1);               // wait for a second
75  
76  digitalWrite(D1, LOW);
77  digitalWrite(D2, LOW);
78  digitalWrite(D3,  HIGH);
79  digitalWrite(D4, LOW); 
80  //2
81  digitalWrite(pinA, HIGH);   
82  digitalWrite(pinB, HIGH);   
83  digitalWrite(pinC, LOW);   
84  digitalWrite(pinD,  HIGH);   
85  digitalWrite(pinE, LOW);   
86  digitalWrite(pinF, HIGH);   
87  digitalWrite(pinG, LOW);     
88  delay(1);               // wait for a second
89
90  digitalWrite(D1, LOW);
91  digitalWrite(D2, LOW);
92  digitalWrite(D3, LOW);
93  digitalWrite(D4, HIGH); 
94  //3
95  digitalWrite(pinA, LOW);   
96  digitalWrite(pinB,  HIGH);   
97  digitalWrite(pinC, LOW);   
98  digitalWrite(pinD, HIGH);   
99  digitalWrite(pinE, LOW);   
100  digitalWrite(pinF, LOW);   
101  digitalWrite(pinG,  HIGH);     
102  delay(1);               // wait for a second
103/*  
104  //4
105  digitalWrite(pinA, HIGH);   
106  digitalWrite(pinB, LOW);   
107  digitalWrite(pinC,  LOW);   
108  digitalWrite(pinD, HIGH);   
109  digitalWrite(pinE, HIGH);   
110  digitalWrite(pinF, LOW);   
111  digitalWrite(pinG, LOW);     
112  delay(1000);               // wait for a second
113  
114  //5
115  digitalWrite(pinA, LOW);   
116  digitalWrite(pinB, HIGH);   
117  digitalWrite(pinC, LOW);   
118  digitalWrite(pinD,  LOW);   
119  digitalWrite(pinE, HIGH);   
120  digitalWrite(pinF, LOW);   
121  digitalWrite(pinG, LOW);     
122  delay(1000);               // wait for a second
123  
124  //6
125  digitalWrite(pinA, LOW);   
126  digitalWrite(pinB, HIGH);   
127  digitalWrite(pinC, LOW);   
128  digitalWrite(pinD, LOW);   
129  digitalWrite(pinE,  LOW);   
130  digitalWrite(pinF, LOW);   
131  digitalWrite(pinG, LOW);     
132  delay(1000);               // wait for a second
133  
134  //7
135  digitalWrite(pinA,  LOW);   
136  digitalWrite(pinB, LOW);   
137  digitalWrite(pinC, LOW);   
138  digitalWrite(pinD,  HIGH);   
139  digitalWrite(pinE, HIGH);   
140  digitalWrite(pinF, HIGH);   
141  digitalWrite(pinG, HIGH);     
142  delay(1000);               // wait for a second
143  
144  //8
145  digitalWrite(pinA, LOW);   
146  digitalWrite(pinB, LOW);   
147  digitalWrite(pinC, LOW);   
148  digitalWrite(pinD, LOW);   
149  digitalWrite(pinE,  LOW);   
150  digitalWrite(pinF, LOW);   
151  digitalWrite(pinG, LOW);     
152  delay(1000);               // wait for a second
153
154  //9
155  digitalWrite(pinA,  LOW);   
156  digitalWrite(pinB, LOW);   
157  digitalWrite(pinC, LOW);   
158  digitalWrite(pinD,  HIGH);   
159  digitalWrite(pinE, HIGH);   
160  digitalWrite(pinF, LOW);   
161  digitalWrite(pinG, LOW);     
162  delay(1000);               // wait for a second
163  */
164 }
```
{% endcode %}
