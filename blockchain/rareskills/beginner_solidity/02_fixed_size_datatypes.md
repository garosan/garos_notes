# Fixed Size Datatypes: Solidity is a typed language.

[Original Article](https://www.rareskills.io/learn-solidity/solidity-types)

A diferencia de Python o JavaScript, en Solidity tenemos qué decirle al compilador de qué tipo es la variable que declaramos y no podemos cambiarla más adelante.

Lo mismo para las funciones, tenemos qué declarar el tipo de cada parámetro que pasemos a nuestra función y el tipo del dato que va a regresar nuestra función.

Los tipos más comunes son:

- unsigned integer o uint256
- variable booleana o bool
- address que puede ser un smart contract o una wallet

Solidity tiene arrays, strings, structs y otros tipos, pero los veremos más adelante.

3 funciones que regresan estos 3 tipos diferentes:

```solidity
contract FirstDataTypes {
  function getANumber() public pure returns (uint256) {
    uint256 x = 1;
    return x;
  }

  function getABoolean() public pure returns (bool) {
    bool y = true;
    return y;
  }

  function getAnAddress() public pure returns (address) {
    address z = 0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045;
    return z;
  }
}
```

### Address

Este tipo de dato representa una dirección de una wallet o de un smart contract. Siempre debe tener 40 caracteres y siempre comienza con 0x.

Si creamos una variable address con más de 40 caracteres nuestro programa no compilará.

Toma nota que los 40 caracteres son sin contar el `0x` del principio.

### uint256

La `u` en `uint256` significa _unsigned_, es decir que este tipo de dato no puede representar números negativos, solamente positivos enteros.

El 256 significa que puede guardar números de hasta 256 bits. Este sería el número más grande que se puede representar con un `uint256`:

`115792089237316195423570985008687907853269984665640564039457584007913129639935`

Esto va a compilar en Solidity:

```solidity
function getBiggestNumber() public pure returns (uint256) {
  return 115792089237316195423570985008687907853269984665640564039457584007913129639935;
}
```

Pero trata de cambiar el último 5 por un 6 y automaticamente obtendrás un error.

En Solidity, tenemos desde `uint8` hasta `uint256` en incrementos de 8, es decir `uint8`, `uint16`, `uint24`, etc.

Algunos ejemplos:

- `uint8`: 8-bit unsigned integer (range: 0 to 2^8 - 1)
- `uint16`: 16-bit unsigned integer (range: 0 to 2^16 - 1)
- `uint24`: 24-bit unsigned integer (range: 0 to 2^24 - 1)
- `uint32`: 32-bit unsigned integer (range: 0 to 2^32 - 1)
- `uint40`: 40-bit unsigned integer (range: 0 to 2^40 - 1)
