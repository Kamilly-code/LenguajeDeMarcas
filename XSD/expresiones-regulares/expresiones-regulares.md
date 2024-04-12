# Expresiones regulares

| Símbolo | Explicación |
|---------|-------------|
| .       | Coincide con cualquier carácter excepto un salto de línea. |
| *       | Coincide con cero o más repeticiones del elemento anterior. |
| +       | Coincide con una o más repeticiones del elemento anterior. |
| ?       | Coincide con cero o una repetición del elemento anterior. |
| ^       | Coincide con el inicio de una cadena. |
| $       | Coincide con el final de una cadena. |
| [...]   | Coincide con cualquier carácter dentro de los corchetes. |
| [^...]  | Coincide con cualquier carácter que no esté dentro de los corchetes. |
| \d      | Coincide con un dígito. |
| \w      | Coincide con un carácter alfanumérico o un guion bajo. |
| [a-z]   | Cualquier carácter de la a a la z. |
| x{n}    | x debe aparecer exactamente n veces. |
| x{n,m}  | x debe aparecer entre n y m veces. |
| x{n,}   | x debe aparecer al menos n veces. |



# Ejemplo para cada símbolo:

- `.` : "c.t" coincidiría con "cat", "cot", "cut", etc.
- `*` : "ca*t" coincidiría con "ct", "cat", "caat", "caaat", etc. 
- `+` : "c+t" coincidiría con "cat", "caat", "caaat", etc. pero no con "ct".
- `?` : "c?t" coincidiría con "ct" y "cat", pero no con "caat" o "caaat".
- `^` : "^cat" coincidiría con "cat" al inicio de una cadena.shift+` = ^
- `$` : "cat$" coincidiría con "cat" al final de una cadena.
- [...]: "[aeiou]" coincidiría con cualquier vocal.
- [^...]: "[^aeiou]" coincidiría con cualquier consonante.
- \d: "\d\d" coincidiría con cualquier par de dígitos.
- \w: "\w+" coincidiría con cualquier palabra alfanumérica o guion bajo.
- x{n}: "x{5}" coincidiría con "xxxxx"
- 

# Ejercicios
| Número | Descripción |
|--------|-------------|
| 1)     | "Capítulo 0", "Capítulo 1", "Capítulo 2"... "Capítulo 9". (Solo se permite un dígito). |
| 2)     | "Capítulo 0", "Capítulo 1", "Capítulo 2"... "Capítulo 99". (Uno o dos dígitos). |
| 3)     | "Capítulo 1", "Capítulo 2", "Capítulo 3"... "Capítulo 99". (No se permite "Capítulo 0"). |
| 4)     | "Capítulo 0", "Capítulo 1", "Capítulo 2"... "Capítulo 99"... "Capítulo 100"... (Uno o más dígitos). |
| 5)     | Cualquier valor de dos caracteres, cuyo primer carácter sea distinto de un dígito (0-9) y cuyo segundo carácter sea "Z": "aZ"... "zZ", "AZ"... "ZZ", "?Z", "=Z", "*Z"... |
| 6)     | "ABBC", "ABBBC", "ABBBBC", "ABBBBBC". |
| 7)     | El primer carácter debe ser "R". A continuación, deben aparecer obligatoriamente dos o más "S". Finalmente, puede aparecer o no, un dígito del 3 al 8: "RSS", "RSSS"... "RSS3"... "RSS8", "RSSS3"... "RSSS8"... "RSSSSSSSSSSS7"... |
| 8)     | Cualquier valor que contenga en primer lugar "COD", después tres dígitos (0-9) y, finalmente, uno o más caracteres cualesquiera: "COD645pera", "COD646manzana"... |

## Soluciones
1.  Capítulo [0-9] 
    Capítulo \d 
    Capítulo [0|1|2|3|4|5|6|7|8|9]

2. Capítulo [0-9]{1,2}
   Capítulo [0-9][0-9]
   Capítulo \d\d

3. Capítulo [1-9][0-9]
   Capítulo [1-9]\d

4. Capítulo [0-9]+
   Capítulo \d+

5. [^0-9][Z]

6. AB{2,4}C

7. RS{2,}([3-8])?

8. COD[0-9]{3}.+

# Ejercicio
Dado el siguiente documento XML, escribir el contenido del archivo expresiones_regulares.xsd que permita validarlo. 

<?xml version="1.0" encoding="UTF-8"?>
<expresiones-regulares xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="expresiones-regulares.xsd">
   <expresiones>
      <expresion1>Capítulo 0</expresion1>
      <expresion2>Capítulo 0</expresion2>
      <expresion3>Capítulo 1</expresion3>
      <expresion4>Capítulo 0</expresion4>
      <expresion5>aZ</expresion5>
      <expresion6>ABBC</expresion6>
      <expresion7>RSS</expresion7>
      <expresion8>COD645pera</expresion8>
   </expresiones>
   <expresiones>
      <expresion1>Capítulo 9</expresion1>
      <expresion2>Capítulo 99</expresion2>
      <expresion3>Capítulo 99</expresion3>
      <expresion4>Capítulo 99999</expresion4>
      <expresion5>?Z</expresion5>
      <expresion6>ABBBBBC</expresion6>
      <expresion7>RSSSSSSSSSSS7</expresion7>
      <expresion8>COD646manzana</expresion8>
   </expresiones>
</expresiones-regulares>

