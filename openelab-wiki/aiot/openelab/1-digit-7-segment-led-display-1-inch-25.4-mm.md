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

# 1 Digit 7-Segment LED Display 1 inch 25.4 mm

### 1 Digit 7-Segment LED Display 1 inch 25.4 mm

***

### Product Link

{% embed url="https://openelab.io/products/1digit7segmentleddisplay?_pos=1&_sid=d15d6c749&_ss=r" %}

### Introduction

led digital tube (LED Segment Displays) is composed of multiple light-emitting diodes packaged together to form a "8" type device, the lead has been connected internally to complete, only need to lead out of their individual strokes, the public electrode. led digital tube commonly used for the number of segments is generally 7 segments with a decimal point, there is a similar 3-digit "+1" type. One is similar to the 3-bit "+1" type. The number of bits has half, 1, 2, 3, 4, 5, 6, 8, 10 and so on ，The led digital tube is divided into two categories, common negative and common positive, according to the different connection methods of the LED, it is very important to understand these characteristics of the LED for the programming, because different types of digital tubes, in addition to the differences in their hardware circuits, programming methods are also different

### Pinout

<figure><img src="../../.gitbook/assets/image (803).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (802).png" alt=""><figcaption></figcaption></figure>

### How to Use

Separately, a, b, c, d, e, and f, g, and dp to the Arduino's 4, 5, 6, 7, 8, 9, 10, and 11. call the function for the number you need to display

<pre class="language-cpp"><code class="lang-cpp">int a=7; 
int b=6; 
int c=5; 
int d=11; 
int e=10; 
int f=8; 
int g=9; 
int dp=4;
//显示数字 0 
void digital_0(void) 
{ 
    unsigned char j; 
    for(j=5;j&#x3C;=11;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(dp,HIGH); 
    digitalWrite(g,HIGH); 
}  
//显示数字 1 
void digital_1(void) 
{ 
    unsigned char j; 
    digitalWrite(c,LOW);//给数字 5 引脚低电平，点亮 c 段
    digitalWrite(b,LOW);//点亮 b 段
    for(j=7;j&#x3C;=11;j++)//熄灭其余段
    digitalWrite(j,HIGH); 
    digitalWrite(dp,HIGH);//熄灭小数点 DP 段
} 
//显示数字 2 
void digital_2(void) 
{ 
    unsigned char j; 
    digitalWrite(b,LOW); 
    digitalWrite(a,LOW); 
    for(j=9;j&#x3C;=11;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(dp,HIGH); 
    digitalWrite(c,HIGH); 
    digitalWrite(f,HIGH); 
} 
//显示数字 3 
void digital_3(void) 
{ 
<strong>    unsigned char j; 
</strong>    digitalWrite(g,LOW); 
    digitalWrite(d,LOW); 
    for(j=5;j&#x3C;=7;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(dp,HIGH); 
    digitalWrite(f,HIGH); 
    digitalWrite(e,HIGH); 
} 
//显示数字 4 
void digital_4(void) 
{ 
    digitalWrite(c,LOW); 
    digitalWrite(b,LOW); 
    digitalWrite(f,LOW); 
    digitalWrite(g,LOW); 
    digitalWrite(dp,HIGH); 
    digitalWrite(a,HIGH); 
    digitalWrite(e,HIGH); 
    digitalWrite(d,HIGH); 
} 
//显示数字 5 
void digital_5(void) 
{ 
    unsigned char j; 
    for(j=7;j&#x3C;=9;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(c,LOW); 
    digitalWrite(d,LOW); 
    digitalWrite(dp,HIGH); 
    digitalWrite(b,HIGH); 
    digitalWrite(e,HIGH); 
} 
//显示数字 6 
void digital_6(void) 
{ 
    unsigned char j; 
    for(j=7;j&#x3C;=11;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(c,LOW); 
    digitalWrite(dp,HIGH); 
    digitalWrite(b,HIGH); 
} 
//显示数字 7 
void digital_7(void) 
{ 
    unsigned char j; 
    for(j=5;j&#x3C;=7;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(dp,HIGH); 
    for(j=8;j&#x3C;=11;j++) 
    digitalWrite(j,HIGH); 
} 
//显示数字 8 
void digital_8(void) 
{ 
    unsigned char j; 
    for(j=5;j&#x3C;=11;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(dp,HIGH); 
} 
//显示数字 9 
void digital_9(void) 
{ 
    unsigned char j; 
    for(j=5;j&#x3C;=11;j++) 
    digitalWrite(j,LOW); 
    digitalWrite(dp,HIGH);
    digitalWrite(e,HIGH); 
} 
void setup() 
{ 
    int i;//定义变量
    for(i=4;i&#x3C;=11;i++) 
    pinMode(i,OUTPUT);//设置 4～11 引脚为输出模式
} 
void loop() 
{ 
    while(1) 
    {
        digital_0();//数字 0 
        delay(2000);//延时 2s  
        digital_1();//数字 1 
        delay(2000);//延时 2s 
        digital_2(); 
        delay(2000); 
        digital_3(); 
        delay(2000); 
        digital_4(); 
        delay(2000); 
        digital_5(); 
        delay(2000); 
        digital_6(); 
        delay(2000); 
        digital_7(); 
        delay(2000); 
        digital_8(); 
        delay(2000); 
        digital_9(); 
        delay(2000); 
    } 
}

</code></pre>
