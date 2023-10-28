## Arduino code
* pinMode(10, INPUT); //R1: S1,S2,S3,S4 (1,2,3,A)                                  
  pinMode(11, INPUT_PULLUP); //R2: S5,S6,S7,S8 (4,5,6,B)
  pinMode(12, INPUT_PULLUP); //R3: S9, S10, S11,S12 (7,8,9,C)
  pinMode(13, INPUT_PULLUP); //R4: (*,0,#,D)
  pinMode(A0, OUTPUT); //A1, C1: S1,S5,S9 (1,4,7,*)
  pinMode(A1, OUTPUT); //A2, C2: S2,S6,S10 (2,5,8,0)
  pinMode(A2, OUTPUT); //A3, C3: S3,S7,S11 (3,6,9,#)
  pinMode(A3, OUTPUT); //A4, C4, S4,S8,S12 (*,0, #,D)  // (A, B, C, D) is correct.
  //Pin left to right :R1 R2 R3 R4 C1 C2 C3 C4

	10 ~ 13: Row
	A0 ~ A3: Column

* **char KeyValue[]={'1','2','3','A','4','5','6','B','7','8','9','C','*','0','#','D'};**
	![[Pasted image 20231002173455.png]]


## **lcd.setCursor(0,0);**
### Description
  move the LCD cursor's position to new position(row, cloumn); that is, set the location at which subsequent text written to the LCD will ve displayed
	![[Pasted image 20231002173705.png]]


## *lcd.print();**
### Description
prints text to the LCD
	-> lcd.print(data)
	-> lcd.print(data,BASE)

### Parameters
lcd:    a variable of type LiquidCrystal
data:  the data to print (char, byte, int, long, or string)
BASE: (optional) the base in which to print numbers: 
			BIN for binary
			DEC for decimal
			OCT for octal
			HEX for hexadecimal

## Returns
return the number of bytes written, though reading that number is optional.

## **digitalRead();**
### Description
Reads the value from a specified digital pin, either `HIGH` or `LOW`.

### Syntax
`digitalRead(pin)`

### Parameters
`pin`: the Arduino pin number you want to read

### Returns
`HIGH` or `LOW`