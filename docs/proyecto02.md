# Documentación: cálculo del sueldo

## Objetivo

El script recibe el sueldo base y el puesto de una persona mediante un formulario, calcula el complemento que corresponde al puesto y muestra el sueldo final.

## Datos de entrada

Los valores se leen desde `$_POST`:

| Campo | Uso | Valor predeterminado |
|---|---|---|
| `sueldo` | Sueldo base, convertido a entero. | `1000` € |
| `puesto` | Categoría laboral. | Cadena vacía |

El formulario que envía estos datos debe utilizar el método `POST`.

## Complemento según el puesto

| Valor de `puesto` | Porcentaje aplicado |
|---|---:|
| `base` | 10 % |
| `directivo` | 15 % |
| `alto` | 20 % |
| Otro valor | 0 % |

## Lógica del cálculo

Primero se determina el porcentaje según el puesto. A continuación, se calcula el sueldo final con estas fórmulas:

```text
complemento = sueldo base × porcentaje / 100
sueldo final = sueldo base + complemento
```

Por ejemplo, para un sueldo base de `2000` € y el puesto `directivo`, el complemento es `300` € y el sueldo final es `2300` €.

## Salida

La página muestra el sueldo base, el porcentaje de complemento aplicado y el sueldo final, todos expresados en euros.

## Observación sobre el valor predeterminado

Para que se use `1000` cuando `sueldo` no se haya enviado, conviene agrupar el operador de coalescencia antes de convertir el resultado:

```php
$sueldo = (int)($_POST["sueldo"] ?? 1000);
```

También es recomendable validar que el sueldo recibido sea numérico y no negativo antes de realizar el cálculo.
