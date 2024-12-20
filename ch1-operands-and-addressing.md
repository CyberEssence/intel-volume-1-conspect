Операнды команд
Когда команды представлены символически, используется подмножество языка ассемблера IA-32. В этом подмножестве
команда имеет следующий формат:

```asm
label: mnemonic argument1, argument2, argument3
```

где:
- Метка - это идентификатор, за которым следует двоеточие.
- Мнемоника - это зарезервированное имя для класса командных кодов операций, которые выполняют одну и ту же функцию.
- Операнды argument1, argument2 и argument3 являются необязательными. В зависимости от кода операции может быть от нуля до трех операндов. Если они присутствуют, они принимают форму литералов или идентификаторов элементов данных. Идентификаторы операндов являются либо зарезервированными именами регистров, либо предполагается, что они присваиваются элементам данных, объявленным в другой части программы (которые могут быть не показаны в примере).

Когда в арифметической или логической команде присутствуют два операнда, правый операнд является исходным, а левый - конечным.

Например:
```asm
LOADREG: MOV EAX, SUBTOTAL
```
  
В этом примере LOADREG - это метка, MOV - мнемонический идентификатор кода операции, EAX - целевой операнд,
а SUBTOTAL - исходный операнд. В некоторых языках ассемблера исходный код и конечный результат указываются в обратном порядке.

Сегментированная адресация

Процессор использует байтовую адресацию. Это означает, что память организована и доступ к ней осуществляется в виде последовательности байтов.
Независимо от того, осуществляется ли доступ к одному или нескольким байтам, для определения местоположения байта или байтовой памяти используется байтовый адрес. 
Область памяти, к которой можно обращаться, называется адресным пространством.
Процессор также поддерживает сегментированную адресацию. Это форма адресации, при которой программа может иметь множество
независимых адресных пространств, называемых сегментами. Например, программа может сохранять свой код (инструкции) и стек
в отдельных сегментах. Кодовые адреса всегда будут относиться к кодовому пространству, а стековые адреса всегда
будут относиться к стековому пространству. Для указания байтового адреса в сегменте используется следующая запись:

```asm
Segment-register:Byte-address
```

Например, следующий адрес сегмента идентифицирует байт по адресу FF79H в сегменте, на который указывает регистр DS:

```asm
DS:FF79H
```

Следующий адрес сегмента идентифицирует адрес команды в сегменте кода. Регистр CS указывает на сегмент кода, а регистр EIP содержит адрес инструкции.

```asm
CS:EIP
```
