# Ethereum Starter Pack — Clase 2

> Ethereum en Profundidad: cuentas, EVM, contratos inteligentes, Solidity y el ecosistema.

**Duración:** 2 h · **Nivel:** principiante–intermedio · **Pre-requisitos:** Clase 1

---

## 🎯 Objetivos

Al finalizar esta clase, vas a poder:

1. Diferenciar **cuentas externas (EOA)** de **cuentas de contrato** y entender qué es el "estado" de Ethereum.
2. Explicar qué hace la **EVM** y por qué garantiza que todos los nodos lleguen al mismo resultado.
3. Leer un **contrato Solidity** básico y entender qué hace cada línea.
4. Identificar los grandes pilares del ecosistema: **tokens, NFTs, DeFi, DAOs y Layer 2**.
5. **Leer un contrato real en Etherscan** e interactuar con él.

---

## 🗺️ Agenda

| # | Sección | Duración |
|---|---|---|
| 1 | Repaso ultracorto y hook | 5 min |
| 2 | Cuentas en Ethereum: EOA vs Contratos | 10 min |
| 3 | Transacciones, gas y mempool | 15 min |
| 4 | La EVM y el estado de Ethereum | 15 min |
| 5 | Contratos inteligentes en profundidad | 15 min |
| 6 | Solidity: tu primer contrato | 15 min |
| 7 | El ecosistema: tokens, NFTs, DeFi, DAOs | 20 min |
| 8 | Layer 2: el Ethereum que se usa hoy | 10 min |
| 9 | **Práctica: leé un contrato real en Etherscan** | 10 min |
| 10 | Cierre y próximos pasos | 5 min |

---

## 1. Repaso ultracorto y hook

En la **Clase 1** vimos que Ethereum es una computadora descentralizada donde corren programas (contratos inteligentes) que cualquiera puede invocar. Cada uno tiene su wallet, hizo una transacción y la vio en Etherscan.

Hoy nos metemos adentro: **¿cómo funciona realmente esa "computadora"?**

> **Hook:** ¿Cómo puede Ethereum garantizar que un programa devuelva el mismo resultado en cientos de miles de computadoras distintas, en todo el mundo, sin que se contradigan? La respuesta es la **EVM** + el concepto de **determinismo**, y los vamos a entender hoy.

---

## 2. Cuentas en Ethereum: EOA vs Contratos

En Ethereum existen **dos tipos de cuentas**. Esto es clave porque todo lo demás se construye sobre esa distinción.

### 2.1 Externally Owned Account (EOA)

Es tu cuenta de MetaMask: una cuenta controlada por una **clave privada**.

- La controlás vos con tu frase semilla.
- Puede iniciar transacciones (enviar ETH, llamar contratos).
- No tiene código asociado: solo guarda un saldo.

### 2.2 Cuenta de Contrato

Es una cuenta controlada por **código**, no por una persona.

- Se crea cuando alguien despliega un contrato inteligente.
- Tiene una dirección (igual que una EOA, empieza con `0x...`).
- Guarda código y datos persistentes (storage).
- **No puede iniciar transacciones por sí sola.** Solo reacciona cuando una EOA u otro contrato la llama.

### 2.3 Comparación

| | EOA | Contrato |
|---|---|---|
| Controlada por | Clave privada (humano) | Código (lógica del contrato) |
| Puede iniciar tx | ✅ Sí | ❌ No (solo responde) |
| Tiene código | ❌ No | ✅ Sí |
| Tiene saldo en ETH | ✅ Sí | ✅ Sí |
| Tiene storage | ❌ No | ✅ Sí |

> 💡 **Idea clave:** todo en Ethereum empieza con una EOA enviando una transacción. Los contratos son "reactivos": esperan a que alguien los llame.

### ✅ Check rápido

Si un contrato necesita ejecutarse automáticamente todos los días a las 9 AM, ¿puede hacerlo solo?

<details><summary>Ver respuesta</summary>

**No.** Los contratos solo se ejecutan cuando alguien los llama. Para "automatizar" ejecuciones periódicas hay que usar servicios externos como [Chainlink Automation](https://chain.link/automation) o [Gelato](https://www.gelato.network/), que son EOAs robotizadas que llaman al contrato según un schedule.

</details>

---

## 3. Transacciones, gas y mempool

### 3.1 Anatomía de una transacción

Cuando enviás una transacción desde tu wallet, lo que viaja por la red contiene:

- **From:** tu dirección (EOA).
- **To:** dirección destino (otra EOA o un contrato).
- **Value:** cuánto ETH enviás.
- **Data:** si llamás a un contrato, qué función llamás y con qué parámetros.
- **Gas limit:** cuánto gas estás dispuesto a pagar como máximo.
- **Max fee per gas:** cuánto pagás por unidad de gas.
- **Signature:** la firma con tu clave privada.

### 3.2 ¿Qué es el gas?

El **gas** mide el costo computacional de una operación. Cada paso que ejecuta la EVM tiene un costo en gas:

- Sumar dos números: barato.
- Guardar un dato en storage: caro.
- Llamar a otro contrato: muy caro.

**¿Por qué existe el gas?**

1. Para **pagar a los validadores** que procesan tu transacción.
2. Para **evitar que la red se sature** con loops infinitos o spam (cada operación cuesta, los recursos no son gratis).

> ⚠️ **Si el gas se acaba antes de terminar:** la transacción **falla y se revierten todos los cambios**, pero **pagás el gas consumido igual**. Es como pagar el taxi aunque no llegues a destino.

### 3.3 La mempool

La **mempool** ("memory pool") es la **sala de espera** donde van todas las transacciones antes de ser incluidas en un bloque.

Flujo:

1. Tu wallet firma la transacción y la envía a un nodo.
2. El nodo la propaga a otros nodos. Todos la guardan en su mempool.
3. El próximo **validador** elegido para proponer un bloque selecciona transacciones de la mempool — generalmente prioriza las que pagan **más gas por unidad**.
4. Las transacciones elegidas entran al bloque. El bloque se confirma. La transacción sale de la mempool.

> 🔧 **Post-Merge:** desde septiembre 2022, Ethereum usa Proof of Stake. Los que arman bloques son **validadores**, no mineros. Aunque muchos textos viejos sigan diciendo "mineros", en Ethereum hoy son validadores.

### 3.4 Ver la mempool en vivo

Recurso visual para mostrar en clase:

**[txcity.io/v/eth-btc](https://txcity.io/v/eth-btc)**

Cada personita en la vereda es una transacción esperando en la mempool. Cada colectivo que sale es un bloque que se confirma.

---

## 4. La EVM y el estado de Ethereum

### 4.1 Ethereum como máquina de estado

Pensá a Ethereum como una **máquina de estado** gigante y global. ¿Qué es eso?

Una máquina de estado tiene:

- Un **estado actual** (toda la información en este momento: cuánto ETH tiene cada cuenta, qué dato guarda cada contrato).
- **Reglas de transición** (cómo el estado cambia cuando ocurre algo).

En Ethereum:

- El **estado** es el conjunto de todas las cuentas con sus saldos, código y datos.
- Las **transacciones** son los eventos que cambian el estado.
- Las **reglas de transición** las define la **EVM**.

Cada bloque transforma el estado anterior en uno nuevo aplicando las transacciones que contiene.

### 4.2 ¿Qué es la EVM?

La **Ethereum Virtual Machine (EVM)** es el "motor" que ejecuta los contratos inteligentes. Cada nodo de Ethereum tiene una EVM corriendo.

Analogía: la EVM es como una computadora virtual con su propio "procesador" y su propia "memoria". Cuando llamás a un contrato, la EVM ejecuta su código y actualiza el estado.

### 4.3 Determinismo: la propiedad clave

La EVM es **determinística**: dado un contrato y unos datos de entrada, **siempre** produce el mismo resultado, en cualquier nodo del mundo.

> 💡 **Por qué importa:** si la EVM no fuera determinística, los nodos podrían no estar de acuerdo en cuál es el estado actual de Ethereum. Como sí lo es, todos llegan al mismo resultado y la red se mantiene sincronizada.

Esto tiene una consecuencia práctica: en Solidity **no podés usar números aleatorios reales ni hora del sistema** (esas cosas son diferentes en cada computadora). Para aleatoriedad se usan servicios externos como [Chainlink VRF](https://chain.link/vrf).

### 4.4 Bytecode

Los contratos no se ejecutan en Solidity directamente. Se **compilan a bytecode**: una secuencia de instrucciones de bajo nivel que la EVM entiende.

Analogía: Solidity es como Python; bytecode es como código máquina. La EVM solo entiende bytecode.

Cuando desplegás un contrato, lo que queda en la blockchain es **el bytecode**, no el código fuente. Por eso Etherscan tiene una función "Verify Contract": permite a los autores subir el código fuente original y demostrar que coincide con el bytecode desplegado.

---

## 5. Contratos inteligentes en profundidad

### 5.1 Qué son (versión técnica)

Un **contrato inteligente** es código que vive en una dirección de Ethereum. Tiene:

- **Funciones públicas** que cualquiera puede llamar.
- **Storage** (datos que persisten entre llamadas).
- **Eventos** que emite para que las aplicaciones puedan reaccionar.

### 5.2 Propiedades

- **Inmutable:** una vez desplegado, el código no se puede modificar (a menos que el contrato esté diseñado a propósito para ser actualizable, lo cual es un patrón complejo).
- **Determinístico:** mismo input → mismo output, siempre.
- **Público:** cualquiera puede leer el código (si está verificado) y llamarlo.
- **Permisionless:** no hace falta pedir permiso a nadie para interactuar.
- **Componible:** un contrato puede llamar a otro contrato. Por eso a las aplicaciones DeFi se las llama "money legos".

### 5.3 Limitaciones reales

No es "cualquier cosa imaginable". Hay límites importantes:

- **Costo:** ejecutar un contrato cuesta gas. Cálculos pesados son prohibitivamente caros en mainnet.
- **Latencia:** un bloque cada ~12 segundos. No sirve para apps que necesitan respuesta en milisegundos.
- **Sin acceso al mundo exterior:** un contrato no puede llamar una API ni leer una base de datos. Para eso existen los **oráculos** (ej. Chainlink).
- **Privacidad nula por default:** todo es público. Cualquiera puede leer el estado de tu contrato.
- **Bugs son permanentes:** si tu contrato tiene un error, no podés "subir una actualización". El [hack de The DAO en 2016](https://www.coindesk.com/learn/understanding-the-dao-attack) drenó $50M por un bug que no se pudo arreglar — terminó causando un fork de Ethereum.

### 5.4 Ejemplos reales de contratos famosos

- **USDC** (stablecoin de Circle): un contrato que emite tokens respaldados 1:1 por dólares.
- **Uniswap V3**: contratos que permiten intercambiar tokens sin intermediarios.
- **Bored Ape Yacht Club**: contrato que emite 10.000 NFTs únicos.
- **ENS (Ethereum Name Service)**: contratos que asocian nombres legibles (`vitalik.eth`) a direcciones (`0x...`).

---

## 6. Solidity: tu primer contrato

**Solidity** es el lenguaje más usado para escribir contratos en Ethereum. Su sintaxis recuerda a JavaScript pero tiene reglas propias adaptadas a la EVM.

### 6.1 Anatomía de un contrato mínimo

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Contador {
    // Variable de estado: queda guardada en la blockchain
    uint256 public numero;

    // Función pública: cualquiera puede llamarla
    function setNumero(uint256 _nuevo) public {
        numero = _nuevo;
    }

    // Función de solo lectura: no modifica nada, no cuesta gas si la llamás desde afuera
    function getNumero() public view returns (uint256) {
        return numero;
    }
}
```

**Línea por línea:**

- `SPDX-License-Identifier: MIT` → declara la licencia del código. Es buena práctica.
- `pragma solidity ^0.8.20;` → versión del compilador a usar (≥ 0.8.20).
- `contract Contador { ... }` → define un contrato llamado "Contador". Análogo a `class` en otros lenguajes.
- `uint256 public numero;` → declara una variable de tipo entero positivo de 256 bits. `public` hace que Solidity genere automáticamente una función para leerla desde afuera.
- `function setNumero(uint256 _nuevo) public` → función que toma un parámetro `_nuevo` y lo guarda. **Modifica el estado, entonces cuesta gas.**
- `function getNumero() public view returns (uint256)` → función de solo lectura (`view`). No modifica nada. **Si la llamás desde afuera, no cuesta gas.**

### 6.2 Tipos de funciones por costo

| Tipo | Modifica estado | Cuesta gas |
|---|---|---|
| `view` / `pure` | No | No (si se llama externamente) |
| Normal | Sí | Sí |
| `payable` | Sí (puede recibir ETH) | Sí |

### 6.3 Probalo vos mismo

[**Remix IDE**](https://remix.ethereum.org/) es un entorno web donde podés escribir, compilar y desplegar contratos sin instalar nada.

> 💡 **Demo sugerida para clase:** pegá el contrato `Contador` en Remix, compilalo, desplegalo en la "JavaScript VM" (un Ethereum simulado, gratis), llamá las funciones y mostrá cómo cambia el valor.

### 6.4 Otros lenguajes

Solidity domina, pero no es el único:

- **Vyper:** sintaxis tipo Python, menos features, más enfocado en seguridad.
- **Huff:** ensamblador para la EVM, máxima optimización de gas (para expertos).
- **Yul:** lenguaje intermedio entre Solidity y bytecode.

Y en algunas L2 modernas (como Arbitrum con Stylus) ya podés escribir contratos en **Rust** o **C++**.

### ✅ Check rápido

¿Por qué `getNumero()` no cuesta gas si la llamás desde afuera, pero `setNumero()` sí?

<details><summary>Ver respuesta</summary>

Porque `getNumero()` es `view`: no modifica el estado, así que no necesita un bloque ni validadores que la procesen. Solo lee datos locales del nodo al que le preguntás.

`setNumero()` sí modifica el estado, entonces tiene que ser parte de una transacción, ser propagada por la mempool, incluida en un bloque y validada por la red. Todo eso cuesta gas.

</details>

---

## 7. El ecosistema: tokens, NFTs, DeFi, DAOs

Sobre Ethereum hay **estándares** (llamados **ERC**, *Ethereum Request for Comment*) que definen interfaces comunes para que las aplicaciones se puedan hablar entre sí.

### 7.1 Tokens fungibles: ERC-20

Un **token ERC-20** es un contrato que sigue un estándar para representar una moneda o activo intercambiable. Todas las unidades son idénticas: 1 USDC es igual a cualquier otro USDC.

**Ejemplos famosos:**

- **USDC, USDT, DAI** → stablecoins (1 token = 1 dólar).
- **LINK** → token de Chainlink.
- **UNI** → token de Uniswap.

Funciones que todo ERC-20 implementa:

- `balanceOf(address)` → cuántos tokens tiene una dirección.
- `transfer(to, amount)` → transferir tokens.
- `approve(spender, amount)` → autorizar a otro contrato a mover tus tokens.

### 7.2 Tokens no fungibles: ERC-721 (NFTs)

Un **NFT (ERC-721)** representa un activo **único** e indivisible. Cada token tiene un ID distinto y propiedades distintas.

**Casos de uso reales:**

- **Arte digital:** [Art Blocks](https://www.artblocks.io/), [Bored Ape Yacht Club](https://boredapeyachtclub.com/).
- **Coleccionables:** cromos digitales (NBA Top Shot, Sorare).
- **Identidad/dominios:** [ENS](https://ens.domains/) — cada `.eth` es un NFT.
- **Tickets:** entradas a eventos como NFT, imposibles de falsificar.
- **Activos in-game:** propiedad real de skins, espadas, terrenos virtuales.

> 💡 **Aclaración:** un NFT no es la imagen en sí; es un **certificado de propiedad** registrado en blockchain que apunta a la imagen (o a cualquier otro contenido).

### 7.3 Otros estándares importantes

- **ERC-1155:** tokens "mixtos" — un mismo contrato puede manejar tokens fungibles y no fungibles. Muy usado en gaming.
- **ERC-4626:** estándar para "vaults" (bóvedas) de yield en DeFi.

### 7.4 DeFi (Finanzas Descentralizadas)

**DeFi** es el conjunto de servicios financieros que viven en Ethereum como contratos inteligentes, sin bancos.

**Categorías principales:**

- **Intercambios descentralizados (DEX):** [Uniswap](https://uniswap.org/), [Curve](https://curve.fi/). Permiten intercambiar tokens directamente, sin orden book ni intermediario.
- **Préstamos:** [Aave](https://aave.com/), [Compound](https://compound.finance/). Depositás colateral, pedís prestado contra él. Todo automatizado por contratos.
- **Stablecoins descentralizadas:** [DAI](https://makerdao.com/) (de MakerDAO) está respaldada por colateral cripto, no por una empresa.
- **Yield aggregators:** [Yearn](https://yearn.fi/). Mueven tus fondos entre protocolos buscando el mejor rendimiento.

**Composabilidad:** podés combinar protocolos como LEGO. Pedís prestado en Aave, intercambiás en Uniswap, depositás en Yearn — todo en una sola transacción.

### 7.5 DAOs (Organizaciones Autónomas Descentralizadas)

Una **DAO** es una organización donde las decisiones se toman votando con tokens, y se ejecutan automáticamente por contratos.

**Ejemplos:**

- **Uniswap DAO:** decide cambios al protocolo Uniswap.
- **MakerDAO:** gobierna las reglas de DAI.
- **ENS DAO:** gobierna el servicio de nombres `.eth`.

> 💡 **Idea clave:** una DAO no tiene CEO ni junta directiva. Las propuestas se votan en blockchain, y si pasan, los contratos las ejecutan solos.

### 7.6 dApps

Una **dApp** (aplicación descentralizada) es una aplicación cuyo backend vive en contratos inteligentes en lugar de servidores centrales. La interfaz (frontend) suele ser una web normal, pero las acciones críticas pasan por la blockchain.

Para explorar: [ethereum.org/dapps](https://ethereum.org/es/dapps/)

---

## 8. Layer 2: el Ethereum que se usa hoy

### 8.1 El problema de Ethereum mainnet

Ethereum mainnet es seguro pero **lento y caro**:

- ~15 transacciones por segundo.
- Una transacción puede costar entre $2 y $14 USD.
- Para una transferencia chica o un mint de NFT, eso es prohibitivo.

### 8.2 La solución: rollups (Layer 2)

Una **Layer 2 (L2)** es una blockchain que procesa transacciones por su cuenta y después **publica un resumen comprimido en Ethereum mainnet** (Layer 1).

Resultado: **misma seguridad que Ethereum, mucha más velocidad, mucho menos costo**. Una transacción en L2 cuesta unos centavos.

### 8.3 Las L2 más usadas (2026)

| L2 | Tipo | TVL aprox. | Costo tx |
|---|---|---|---|
| **Arbitrum One** | Optimistic Rollup | ~$17B | ~$0.09 |
| **Base** (Coinbase) | Optimistic Rollup | ~$13B | ~$0.05 |
| **Optimism (OP Mainnet)** | Optimistic Rollup | ~$2B | ~$0.09 |
| **zkSync Era** | ZK Rollup | ~$400M | ~$0.07 |
| **Starknet** | ZK Rollup | ~$600M | $0.05–0.19 |

> 💡 **Dato de contexto:** las L2s ya manejan **más volumen de transacciones que Ethereum mainnet**. La mayoría de los usuarios reales hoy interactúan con L2s, no directamente con mainnet.

### 8.4 Dos familias de rollups

- **Optimistic Rollups** (Arbitrum, Base, Optimism): asumen que las transacciones son válidas, y permiten un período de ~7 días para que alguien las cuestione. Más baratos y maduros, pero retirar fondos a mainnet tarda 7 días (a menos que uses bridges como Across).
- **ZK Rollups** (zkSync, Starknet, Scroll, Linea): generan una **prueba criptográfica** de que las transacciones son válidas. Retiros casi instantáneos, pero tecnología más nueva.

### 8.5 ¿Cómo se usa una L2?

Exactamente igual que mainnet:

1. En MetaMask, agregás la red (Arbitrum, Base, etc.).
2. Pasás ETH desde mainnet usando un **bridge** (puente) oficial.
3. Ya podés usar la red con cualquier dApp que esté desplegada ahí.

Recurso: **[L2Beat](https://l2beat.com)** — comparador en tiempo real de todas las L2s con métricas de seguridad, TVL y costos.

---

## 9. 🛠️ Práctica: leé un contrato real en Etherscan

> ⏱️ **15 minutos.** Trabajo individual o en parejas.

Vamos a abrir un contrato real, famoso y verificado en Etherscan, y entender qué hace.

### Paso 1 — Abrí el contrato de USDC

Entrá a la dirección del contrato de USDC en mainnet:

**[etherscan.io/token/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48](https://etherscan.io/token/0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48)**

(Si preferís Sepolia testnet, podés buscar cualquier token verificado en [sepolia.etherscan.io](https://sepolia.etherscan.io).)

### Paso 2 — Identificá información básica

En la pantalla principal, encontrá:

- **Total Supply:** cuántos USDC existen en circulación.
- **Holders:** cuántas direcciones tienen USDC.
- **Transfers:** transferencias recientes.

### Paso 3 — Mirá el contrato

Hacé clic en la pestaña **"Contract"**. Vas a ver tres sub-pestañas:

- **Code:** el código fuente verificado en Solidity. **Leelo.** Vas a reconocer estructuras parecidas al contrato `Contador` que vimos antes.
- **Read Contract:** funciones de solo lectura. Podés llamarlas directamente desde la web. Probá `balanceOf` con cualquier dirección.
- **Write Contract:** funciones que modifican el estado. Para usarlas necesitás conectar MetaMask.

### Paso 4 — Encontrá una transacción real

En la pestaña principal, hacé clic en cualquier transferencia reciente. Identificá:

- ¿Quién transfirió (from) a quién (to)?
- ¿Cuánto?
- ¿Cuánto pagó de gas?
- ¿En qué bloque quedó?

### 🎉 Lo que acabás de hacer

Acabás de:
- Leer el código de un contrato que mueve miles de millones de dólares.
- Llamar a una función de ese contrato desde la web.
- Ver cómo ese contrato es usado, en vivo, por miles de personas.

**El código que leíste es el mismo código que se ejecuta cada vez que alguien transfiere USDC.** Sin intermediario. Sin oficina central. Solo código en una blockchain.

---

## 10. Cierre y próximos pasos

### Lo que vimos hoy

- Ethereum tiene dos tipos de cuentas: EOAs (controladas por humanos) y contratos (controladas por código).
- Cada transacción modifica el estado de Ethereum, y la EVM define las reglas.
- La EVM es **determinística**: por eso todos los nodos están de acuerdo.
- Los contratos se escriben en Solidity y se compilan a bytecode.
- Sobre Ethereum se construyen tokens (ERC-20), NFTs (ERC-721), DeFi, DAOs y dApps.
- **Layer 2** es donde se mueve la mayor parte del uso real de Ethereum hoy.
- Leímos un contrato real en Etherscan.

### Qué viene en la próxima clase

**Clase 3 — Utilizando Blockchain:** vamos a interactuar con dApps reales (Uniswap, Aave, ENS), explorar L2s en MetaMask, y prepararnos para escribir nuestro propio contrato.

---

## 📖 Glosario

| Término | Definición |
|---|---|
| **Bridge** | Servicio que mueve activos entre L1 y L2 (o entre L2s). |
| **Bytecode** | Código de bajo nivel que ejecuta la EVM (resultado de compilar Solidity). |
| **Composabilidad** | Capacidad de combinar contratos como piezas de LEGO. |
| **DAO** | Organización gobernada por votos en blockchain y ejecutada por contratos. |
| **dApp** | Aplicación cuyo backend vive en contratos inteligentes. |
| **DeFi** | Servicios financieros (préstamos, intercambios) en blockchain. |
| **Determinismo** | Propiedad de la EVM: mismo input → mismo output, siempre. |
| **EOA** | Externally Owned Account: cuenta de humano controlada por clave privada. |
| **ERC-20** | Estándar para tokens fungibles. |
| **ERC-721** | Estándar para NFTs (tokens no fungibles). |
| **EVM** | Ethereum Virtual Machine. El motor que ejecuta contratos. |
| **Gas** | Unidad de costo computacional, se paga en ETH. |
| **L1 / L2** | Layer 1 (Ethereum mainnet) / Layer 2 (rollups). |
| **Mempool** | Pool de transacciones esperando ser incluidas en un bloque. |
| **NFT** | Non-Fungible Token. Activo digital único. |
| **Optimistic Rollup** | L2 que asume validez y permite cuestionarla por 7 días. |
| **Oráculo** | Servicio que trae datos del mundo real a un contrato (ej. Chainlink). |
| **Remix** | IDE web para escribir y desplegar contratos. |
| **Rollup** | Tipo de L2 que comprime transacciones y las publica en L1. |
| **Solidity** | Lenguaje de programación más usado para contratos en Ethereum. |
| **Storage** | Almacenamiento persistente de un contrato. |
| **TVL** | Total Value Locked: cuánto valor está depositado en un protocolo. |
| **Validador** | Quien propone y valida bloques en PoS (reemplaza al "minero" de PoW). |
| **ZK Rollup** | L2 que usa pruebas criptográficas para validar transacciones. |

---

## 📚 Recursos

### Documentación oficial

- [Ethereum.org — EVM](https://ethereum.org/en/developers/docs/evm/)
- [Solidity Docs](https://docs.soliditylang.org/)
- [ERC-20 Standard](https://eips.ethereum.org/EIPS/eip-20)
- [ERC-721 Standard](https://eips.ethereum.org/EIPS/eip-721)

### Herramientas

- [Remix IDE](https://remix.ethereum.org/) — escribir y desplegar contratos en el navegador.
- [Etherscan](https://etherscan.io) — explorador de bloques de mainnet.
- [Sepolia Etherscan](https://sepolia.etherscan.io) — explorador de testnet.
- [L2Beat](https://l2beat.com) — comparador de L2s.
- [DeFi Llama](https://defillama.com) — métricas de DeFi en todas las cadenas.

### Para profundizar

- [CryptoZombies](https://cryptozombies.io/) — aprender Solidity programando un juego.
- [Speed Run Ethereum](https://speedrunethereum.com/) — challenges para aprender desarrollo Ethereum.
- [Solidity by Example](https://solidity-by-example.org/) — ejemplos de contratos comentados.
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/) — librería de contratos seguros y auditados.

### Lectura

- [Mastering Ethereum](https://github.com/ethereumbook/ethereumbook) — Andreas Antonopoulos & Gavin Wood (gratis en GitHub).
- [The DAO Hack explicado](https://www.coindesk.com/learn/understanding-the-dao-attack) — caso histórico clave.

---

## 📜 Licencia

Material adaptado por **maximilian0.eth**.

Los derechos del contenido original pertenecen a [**ETH Kipu**](https://ethkipu.notion.site/Ethereum-Starter-Pack-Clase-2-Ethereum-en-Profundidad-7519a4ffa20e8303b7680101402072e4).
