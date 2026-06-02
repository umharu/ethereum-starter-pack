# Ethereum Starter Pack — Clase 4

> El Roadmap de Ethereum: trilema, evolución del protocolo y hacia dónde va la red.

**Duración:** 2 h · **Nivel:** intermedio · **Pre-requisitos:** Clases 1, 2 y 3

---

## 🎯 Objetivos

Al finalizar esta clase, vas a poder:

1. Explicar el **trilema de la blockchain** y por qué obliga a tomar decisiones de diseño.
2. Describir el **roadmap real de Ethereum** (no "Ethereum 2.0" — ese término ya no existe) y sus fases.
3. Entender qué hicieron **The Merge, Dencun, Pectra y Fusaka** y cómo cambiaron la red.
4. Diferenciar las formas de hacer **staking** y elegir la que mejor te conviene.
5. Conocer conceptos avanzados que ya son realidad: **MEV, account abstraction, blobs, restaking**.

---

## 🗺️ Agenda

| # | Sección | Duración |
|---|---|---|
| 1 | Hook + repaso | 5 min |
| 2 | El trilema de la blockchain | 15 min |
| 3 | El roadmap real de Ethereum | 20 min |
| 4 | The Surge: blobs, danksharding y por qué L2 es ahora barato | 20 min |
| 5 | Staking en la práctica: solo, pool o liquid | 15 min |
| 6 | MEV y Account Abstraction | 15 min |
| 7 | **Práctica: explorá la Beacon Chain en vivo** | 10 min |
| 8 | Verge, Purge, Splurge y el futuro | 10 min |
| 9 | Cierre, glosario y recursos | 10 min |

---

## 1. Hook + repaso

En clases anteriores aprendimos qué es Ethereum, cómo funciona la EVM, los contratos inteligentes y los casos de uso reales. Hoy nos toca la pregunta más importante:

> **¿Cómo se hace para que Ethereum siga funcionando bien cuando lo usan 1.000 millones de personas?**

Esa pregunta es el motor de todo el desarrollo del protocolo desde hace 10 años. La respuesta no es un cambio único, sino un **roadmap de varias fases** que ya lleva años en ejecución y le quedan otros tantos.

> ⚠️ **Aclaración previa:** el término "Ethereum 2.0" **ya no se usa**. La Ethereum Foundation lo descontinuó oficialmente en 2022. Hoy hablamos del **roadmap de Ethereum** y sus fases. Si ves "Ethereum 2.0" en algún material, es contenido viejo.

---

## 2. El trilema de la blockchain

### 2.1 Las tres propiedades en tensión

El **trilema de la blockchain** —popularizado por Vitalik Buterin— dice que una blockchain quiere tener tres cosas, pero conseguir las tres al mismo tiempo es muy difícil:

| Propiedad | Qué significa | Cómo se mide |
|---|---|---|
| **Seguridad** | La red resiste ataques. Las transacciones son inmutables. | Costo de atacar la red en USD. |
| **Descentralización** | Nadie controla la red. Cualquiera puede correr un nodo. | Número y distribución geográfica de nodos. |
| **Escalabilidad** | La red puede procesar muchas transacciones por segundo. | TPS (transacciones por segundo) y costo por tx. |

### 2.2 Por qué es difícil tener las tres

Si querés más **escalabilidad**, lo más fácil es subir los requisitos para correr un nodo (más CPU, más RAM, más banda). Pero eso **reduce descentralización** porque menos gente puede participar.

Si querés más **seguridad**, agregás más validaciones por transacción. Pero eso **reduce escalabilidad** porque cada transacción tarda más.

Si querés más **descentralización**, mantenés los nodos baratos. Pero eso **limita la escalabilidad** porque el nodo más débil define el techo.

### 2.3 Cómo otras blockchains "resuelven" el trilema

- **Solana** prioriza escalabilidad. Resultado: muy rápida (~3.000 TPS reales), pero hardware caro para correr nodos → más centralizada. Tuvo varios outages.
- **Bitcoin** prioriza seguridad y descentralización. Resultado: la blockchain más segura del mundo, pero ~7 TPS y poco programable.
- **Ethereum** intenta no sacrificar ninguna de las tres. La estrategia es separar capas: **L1 mantiene seguridad y descentralización; las L2 aportan escalabilidad.**

### ✅ Check rápido

Si una blockchain dice procesar 100.000 TPS y permite correr un nodo con una Raspberry Pi, ¿qué le falta probablemente?

<details><summary>Ver respuesta</summary>

Probablemente **seguridad o descentralización real**. Si fuera tan fácil tener todo, ya lo tendría todo el mundo. Cuando un proyecto promete las tres propiedades al máximo, hay que mirar dónde está la trampa: nodos centralizados, validación insuficiente, hardware especializado, o un mecanismo de consenso poco probado.

</details>

---

## 3. El roadmap real de Ethereum

Vitalik publicó un roadmap visual con **cinco fases**. No son secuenciales —algunas avanzan en paralelo— pero conviene tenerlas como mapa mental.

### 3.1 Las cinco fases

| Fase | Qué resuelve | Estado |
|---|---|---|
| **The Merge** | Energía y consenso | ✅ Completado (sept 2022) |
| **The Surge** | Escalabilidad (rollups + danksharding) | 🔄 En curso |
| **The Verge** | Verificación más liviana de la cadena | ⏳ Por venir |
| **The Purge** | Reducción de datos históricos | ⏳ Por venir |
| **The Splurge** | Mejoras varias (UX, criptografía, MEV) | 🔄 En curso |

### 3.2 The Merge ✅ (septiembre 2022)

**Qué hizo:** migró Ethereum de **Proof of Work** a **Proof of Stake**.

**Impacto medible:**
- Consumo energético: **-99.95%**.
- Emisión de ETH: **-90%** (la red emite mucho menos ETH nuevo).
- Sentó las bases para todo lo que vino después.

> 💡 **Por qué importa hoy:** sin The Merge, las siguientes upgrades habrían sido imposibles. PoS dio la flexibilidad necesaria para iterar rápido.

### 3.3 Shapella ✅ (abril 2023)

**Qué hizo:** habilitó **retirar el ETH stakeado**. Hasta ese momento, los validadores podían stakear pero no retirar — un riesgo enorme.

### 3.4 Dencun ✅ (marzo 2024)

**Qué hizo:** introdujo los **blobs** (EIP-4844, también llamado proto-danksharding).

**Impacto medible:**
- Costos de transacción en L2: **bajaron 10x a 100x**.
- Hoy una transacción en Arbitrum o Base cuesta centavos gracias a esto.
- Es el cambio que hizo que las L2 sean realmente usables para todos.

### 3.5 Pectra ✅ (mayo 2025)

**Qué hizo:** dos cambios grandes:
- **EIP-7702:** account abstraction parcial — las cuentas EOA pueden tener código temporal. Permite cosas como pagar gas con tokens distintos a ETH, transacciones en batch, y recuperación social.
- **EIP-7251:** subió el máximo efectivo de validadores de 32 a 2.048 ETH. Permite consolidar validadores y reducir overhead.

### 3.6 Fusaka ✅ (diciembre 2025)

**Qué hizo:** introdujo **PeerDAS** (Peer Data Availability Sampling), un cambio fundamental.

**Antes de Fusaka:** cada nodo tenía que guardar todos los blobs (datos de L2). Esto limitaba a 6 blobs por bloque.

**Después de Fusaka:** los nodos muestrean partes de los blobs en vez de guardarlos completos. **Se puede llegar a 48 blobs por bloque.**

**Impacto medible:**
- L2 fees: **-40% a -60%** en el primer mes.
- Gas limit del bloque: subió de 45M a 150M.
- Sienta las bases para el danksharding completo.

### 3.7 Lo que viene en 2026

- **Glamsterdam** (mid-2026): más paralelismo, MEV transparente (ePBS), Verkle trees parciales.
- **Heze-Bogota** (fin 2026): foco en privacidad y seguridad.

> 💡 **Idea clave:** Ethereum no se renueva con un Big Bang. Es **iterativo, predecible y conservador**. Cada upgrade se testea en testnets primero, durante meses, antes de ir a mainnet.

---

## 4. The Surge: blobs, danksharding y por qué L2 es ahora barato

Esta es la fase **más importante en el presente** de Ethereum. Vale la pena entenderla bien.

### 4.1 El problema original

Hasta 2024, Ethereum mainnet era el cuello de botella. Las L2 publicaban datos en mainnet usando *calldata*, que era caro. Una transacción en L2 podía costar $0.50–$2 USD, no centavos.

### 4.2 La solución: blobs (EIP-4844)

Un **blob** es un nuevo tipo de dato en Ethereum diseñado **específicamente para que las L2 publiquen sus transacciones**. Tiene tres propiedades clave:

1. **Es más barato** que calldata.
2. **Es temporal:** se borra después de ~18 días. No vive para siempre en la cadena.
3. **Solo lo usan rollups**, no las transacciones normales.

> 💡 **Analogía:** antes, las L2 escribían en "el papel oficial caro" (calldata). Ahora escriben en "papel borrador" (blobs) — más barato, suficiente para sus necesidades, y se descarta cuando ya no hace falta.

### 4.3 PeerDAS (Fusaka, dic 2025)

PeerDAS resolvió el siguiente problema: **¿cómo escalar los blobs si cada nodo tiene que guardarlos todos?**

Solución: los nodos **muestrean** pequeñas partes de cada blob. Con suficientes nodos muestreando partes distintas, se reconstruye toda la información. **Es el mismo principio que las pruebas estadísticas: no hace falta revisar todo para tener certeza.**

Resultado: la red puede manejar mucho más data sin que cada nodo tenga que crecer en hardware.

### 4.4 El destino final: danksharding completo

El plan es llegar a **128 blobs por bloque** (hoy son 48 post-Fusaka). Cuando eso pase:
- Las L2 podrán procesar **>100.000 TPS combinados**.
- Las fees en L2 se acercarán a cero (fracciones de centavo).
- Ethereum mainnet seguirá siendo lo que es: la capa de **liquidación y seguridad**.

### 4.5 Por qué esto cambia la estrategia de Ethereum

Ethereum decidió: **L1 = seguridad. L2 = donde sucede el día a día.**

Hoy, cuando alguien dice "estoy usando Ethereum", probablemente está usando **Arbitrum, Base, Optimism o zkSync**, no mainnet directamente. Mainnet es donde se asientan los pagos finales y donde hay liquidez profunda.

> 📊 **Dato actual:** las L2 ya manejan más volumen de transacciones que mainnet. Mucho más.

---

## 5. Staking en la práctica: solo, pool o liquid

Si vas a participar en PoS, tenés tres caminos. Conviene saber cuál te conviene.

### 5.1 Solo staking

**Cómo funciona:** corrés tu propio nodo validador. Stakeás 32 ETH (mínimo) o hasta 2.048 ETH (post-Pectra).

| Pro | Con |
|---|---|
| Máxima recompensa (sin fees) | 32 ETH = mucha plata (>$80.000 USD a precios actuales) |
| Apoyás la descentralización | Necesitás hardware confiable 24/7 |
| Control total | Riesgo de slashing si te equivocás |

**Ideal para:** developers, entusiastas con capital y conocimiento técnico.

### 5.2 Staking pools

**Cómo funciona:** juntás tu ETH con el de otra gente, alguien corre el validador, comparten recompensas y costos.

**Ejemplos:** [Rocket Pool](https://rocketpool.net/), [StakeWise](https://www.stakewise.io/).

| Pro | Con |
|---|---|
| Mínimo bajo (0.01 ETH en algunos) | Pagás fee al pool (5-15%) |
| No necesitás hardware | Confiás en el operador |

### 5.3 Liquid staking

**Cómo funciona:** depositás ETH en un protocolo, recibís un **token líquido** que representa tu stake y lo podés usar en DeFi mientras gana recompensas.

**Ejemplos:**
- [Lido](https://stake.lido.fi/) — el más usado. Depositás ETH, recibís stETH.
- [Rocket Pool](https://rocketpool.net/) — también opera como liquid. Recibís rETH.

| Pro | Con |
|---|---|
| Tu ETH sigue siendo "líquido" (usable en DeFi) | Riesgo de smart contract |
| Sin mínimos altos | Riesgo de despeg del token |
| Una sola tx para entrar | Centraliza si un solo proveedor crece mucho |

### 5.4 Restaking (EigenLayer y otros)

**Concepto nuevo (2023-2024):** restakeás tu ETH stakeado para asegurar **otros protocolos** además de Ethereum, ganando recompensas adicionales.

**Ejemplo:** [EigenLayer](https://www.eigenlayer.xyz/).

⚠️ Mayor rendimiento, **mayor riesgo**. Si los protocolos que asegurás fallan, podés perder tu ETH. Solo para usuarios avanzados.

### ✅ Check rápido

Tenés 5 ETH y querés stakear pero también querés que ese ETH siga siendo útil. ¿Qué opción te conviene?

<details><summary>Ver respuesta</summary>

**Liquid staking** (Lido o Rocket Pool). Solo staking requiere 32 ETH mínimo. Un staking pool tradicional bloquea tu ETH. Liquid staking te da un token (stETH, rETH) que podés usar como colateral en Aave, swappear en Uniswap o tener en tu wallet mientras gana recompensas.

</details>

---

## 6. MEV y Account Abstraction

Dos temas que ya son centrales en Ethereum y que vale la pena conocer aunque sean avanzados.

### 6.1 MEV (Maximum Extractable Value)

**Qué es:** el valor extra que un validador puede obtener al **elegir el orden de las transacciones** en su bloque.

**Ejemplo clásico:** alguien quiere comprar mucho de un token en Uniswap. Esa compra grande va a mover el precio. Un bot puede:
1. Ver la transacción en la mempool.
2. Insertar su propia compra **antes** (front-running).
3. Esperar que la compra grande mueva el precio.
4. Vender inmediatamente después con ganancia.

Esto se llama **sandwich attack** y le quita dinero al usuario original.

**MEV no es solo malo:** también incluye arbitraje legítimo y liquidaciones en protocolos de lending. Pero los abusos son un problema real.

**Soluciones en desarrollo:**
- **PBS (Proposer-Builder Separation):** separa quién propone bloques de quién los arma. Reduce el incentivo al front-running.
- **Encrypted mempools:** transacciones encriptadas hasta que se incluyen en un bloque.
- **MEV-Boost:** software que ya usan los validadores hoy para participar en el mercado de MEV de forma transparente.

🔗 [Flashbots Documentation](https://docs.flashbots.net/) para profundizar.

### 6.2 Account Abstraction (ERC-4337 y EIP-7702)

**El problema histórico:** las EOA son rígidas. Una sola clave privada → si la perdés, perdés todo. Solo se puede pagar gas con ETH. No se pueden combinar acciones.

**Account Abstraction** hace que las cuentas se comporten como **smart wallets**. Hoy:

- **Pagar gas con stablecoins** en vez de ETH.
- **Transacciones en batch** (varias acciones en una sola tx).
- **Recuperación social** (si perdés tu wallet, amigos designados pueden ayudarte a recuperarla).
- **Sesiones temporales** (autorizar a una app a hacer cosas durante 1 hora sin firmar cada vez).
- **Passkeys / login con biometría** en lugar de frase semilla.

**Estándares:**
- **ERC-4337** (2023): account abstraction sin cambios al protocolo. Ya en producción.
- **EIP-7702** (Pectra, 2025): account abstraction parcial directa en el protocolo. Hace que las EOA puedan tener código temporal.

**Wallets que ya implementan AA:**
- [Safe](https://safe.global/) (antes Gnosis Safe) — la más usada para tesorerías.
- [Argent](https://www.argent.xyz/) — wallet con recuperación social.
- [Coinbase Wallet Smart Wallet](https://www.coinbase.com/wallet/smart-wallet) — login con passkey, sin frase semilla.

> 💡 **Por qué importa:** la frase semilla es la **peor experiencia de usuario** del cripto. Account abstraction es lo que va a permitir que tu mamá use Ethereum sin entender qué es una clave privada.

---

## 7. 🛠️ Práctica: explorá la Beacon Chain en vivo

> ⏱️ **10 minutos.**

Vamos a ver el corazón de Ethereum PoS funcionando en tiempo real.

### Paso 1 — Abrí beaconcha.in

Andá a **[beaconcha.in](https://beaconcha.in)**. Es el "Etherscan" de la capa de consenso (la Beacon Chain).

### Paso 2 — Identificá los conceptos clave

En la pantalla principal:

- **Slot actual:** un "tic" de la red, cada 12 segundos. Hay 32 slots por epoch.
- **Epoch actual:** unidad de tiempo más grande, ~6.4 minutos. Las finalizaciones pasan acá.
- **Validators:** cantidad total de validadores activos en la red. Hoy son **>1 millón**.
- **APR:** rendimiento anual aproximado del staking.
- **Network %:** participación de los validadores (qué porcentaje está online y firmando).

### Paso 3 — Entrá a un slot

Hacé clic en cualquier slot reciente. Vas a ver:

- Quién fue el **proposer** (validador que propuso el bloque).
- Cuántos **attestations** se incluyeron (votos de otros validadores confirmando).
- Las transacciones de execution layer (lo que conocemos de Etherscan).
- El **MEV reward** si hubo.

### Paso 4 — Mirá un validador específico

Andá a **Validators → Top**. Vas a ver los validadores más grandes. Muchos pertenecen a:
- Lido (representa ~28% del staking)
- Coinbase
- Binance
- Kraken

> 💡 **Observación importante:** la concentración del staking es uno de los riesgos abiertos de Ethereum. Que un solo protocolo (Lido) tenga casi un tercio del staking genera debate constante en la comunidad.

### Paso 5 — Bonus: simulá ser validador

[ethereum.org/staking/saas](https://ethereum.org/staking/saas) te muestra opciones para empezar a stakear. No tenés que hacer nada, solo mirar precios y compararlos.

---

## 8. Verge, Purge, Splurge: el futuro

### 8.1 The Verge

**Objetivo:** hacer que correr un nodo full sea trivial.

**Cómo:** **Verkle trees** — una estructura de datos que reemplaza las Merkle trees actuales. Permite que un nodo verifique el estado sin guardarlo entero. Solo necesita pruebas compactas.

**Estado:** parcialmente implementado en Fusaka. Glamsterdam y posteriores completarán.

### 8.2 The Purge

**Objetivo:** simplificar el protocolo eliminando datos antiguos.

**Cómo:** Ethereum carga con años de historia que la mayoría de los nodos no necesitan. El Purge define qué se puede tirar (sin perder seguridad).

**EIP relevante:** EIP-4444 (historical data expiry).

### 8.3 The Splurge

**Objetivo:** mejoras de calidad de vida.

**Incluye:**
- Account abstraction completa (más allá de EIP-7702).
- Mejoras criptográficas (EIP-7251 para curvas más eficientes).
- Más mejoras de MEV (ePBS).
- Mejoras de UX general.

---

## 9. Cierre, glosario y recursos

### Lo que vimos hoy

- El **trilema** es el marco mental para entender todas las decisiones de diseño.
- Ethereum **ya no es "2.0"** — es un protocolo en evolución continua con fases concretas.
- **The Merge, Dencun, Pectra y Fusaka** ya pasaron y cambiaron la red.
- **The Surge** (presente): rollups + blobs + danksharding hacen que L2 sea barato.
- Para stakear: **solo, pool, liquid, restaking** — cada uno con su trade-off.
- **MEV y account abstraction** son los problemas/oportunidades de la frontera.
- Beaconcha.in es la herramienta para entender Ethereum PoS en vivo.

### Qué viene en la próxima clase

**Clase 5 — Criptografía y Ethereum:** firmas digitales, hashes, claves privadas/públicas, Merkle trees, zk-proofs. Lo que hace que toda esta magia funcione por debajo.

---

## 📖 Glosario

| Término | Definición |
|---|---|
| **Account Abstraction** | Hacer que las cuentas se comporten como smart contracts (recuperación social, gas en cualquier token, batches). |
| **Beacon Chain** | La capa de consenso de Ethereum (donde viven los validadores). |
| **Blob** | Tipo de dato temporal para que los rollups publiquen transacciones barato. |
| **Danksharding** | Visión final de escalabilidad: muchos blobs por bloque, validación distribuida. |
| **Dencun** | Upgrade de marzo 2024 que introdujo blobs. |
| **EIP** | Ethereum Improvement Proposal. Una propuesta formal de mejora. |
| **Epoch** | Unidad de tiempo de la Beacon Chain (32 slots = ~6.4 min). |
| **Fusaka** | Upgrade de diciembre 2025: PeerDAS, blob capacity 6→48. |
| **Liquid Staking** | Stakear ETH y recibir un token (stETH, rETH) que se puede usar en DeFi. |
| **MEV** | Maximum Extractable Value. Ganancia extra por elegir orden de tx en un bloque. |
| **PeerDAS** | Peer Data Availability Sampling. Muestreo distribuido de blobs. |
| **Pectra** | Upgrade de mayo 2025: account abstraction parcial, max balance 2048 ETH. |
| **Proto-danksharding** | Versión inicial de danksharding (EIP-4844). |
| **Restaking** | Stakear ETH ya stakeado para asegurar otros protocolos (EigenLayer). |
| **Roadmap** | Plan de fases (Merge, Surge, Verge, Purge, Splurge). |
| **Slot** | Unidad mínima de tiempo en Beacon Chain (12 segundos). |
| **The Merge** | Migración a PoS (septiembre 2022). |
| **The Purge** | Fase de simplificación del protocolo y eliminación de datos viejos. |
| **The Splurge** | Mejoras varias (UX, criptografía, MEV). |
| **The Surge** | Fase actual: escalabilidad vía rollups y danksharding. |
| **The Verge** | Fase futura: Verkle trees para nodos más livianos. |
| **Trilema** | La tensión entre seguridad, descentralización y escalabilidad. |
| **Verkle Tree** | Estructura de datos que reemplaza Merkle trees para nodos más livianos. |

---

## 📚 Recursos

### Roadmap y upgrades

- [Ethereum Roadmap (oficial)](https://ethereum.org/roadmap/)
- [Vitalik's blog](https://vitalik.eth.limo/) — análisis de primera mano.
- [Endgame post de Vitalik](https://vitalik.eth.limo/general/2021/12/06/endgame.html) — la visión de largo plazo.

### Herramientas para explorar

- [beaconcha.in](https://beaconcha.in) — explorador de Beacon Chain.
- [L2Beat](https://l2beat.com) — comparador de L2s.
- [Rated Network](https://www.rated.network/) — métricas de validadores.

### Staking

- [Lido](https://stake.lido.fi/) — liquid staking dominante.
- [Rocket Pool](https://rocketpool.net/) — staking descentralizado.
- [Ethereum.org Staking](https://ethereum.org/staking/) — guía oficial completa.

### MEV y Account Abstraction

- [Flashbots](https://docs.flashbots.net/) — referencia de MEV.
- [Safe](https://safe.global/) — smart wallets para teams.
- [ERC-4337 Specification](https://eips.ethereum.org/EIPS/eip-4337)

### Lectura avanzada

- [Proto-Danksharding FAQ](https://notes.ethereum.org/@vbuterin/proto_danksharding_faq) — explicación oficial de blobs.
- [The State of Ethereum (EthMagicians)](https://ethereum-magicians.org/) — discusiones de upgrades en vivo.

---

## 📜 Licencia

Material adaptado por **maximilian0.eth**.

Los derechos del contenido original pertenecen a [**ETH Kipu**](https://ethkipu.notion.site/Ethereum-Starter-Pack-Clase-4-Hacia-Ethereum-2-0-1ac9a4ffa20e83c5b3c5018142972f14).
