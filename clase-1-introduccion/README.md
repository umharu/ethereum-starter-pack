# Ethereum Starter Pack — Clase 1

> Introducción a Blockchain y Ethereum. Material de clase para principiantes.


---

## 🎯 Objetivos

Al finalizar esta clase, vas a poder:

1. Explicar qué es Ethereum y en qué se diferencia de Bitcoin.
2. Tener una wallet propia (MetaMask) con ETH de prueba.
3. Leer una transacción en un explorador de bloques.

---

## 🗺️ Agenda

| # | Sección | Duración |
|---|---|---|
| 1 | Demo en vivo | 10 min |
| 2 | Dinero, confianza e intermediarios | 15 min |
| 3 | Qué es blockchain | 15 min |
| 4 | Qué es Ethereum | 20 min |
| 5 | Bitcoin como contexto | 10 min |
| 6 | Consenso (PoW vs PoS) | 10 min |
| 7 | **Práctica: tu primera wallet** | 35 min |
| 8 | Cierre y FAQ | 5 min |

---

## 1. Demo en vivo

*Demostración en pantalla — sin diapositivas.*

El instructor abre MetaMask, hace una transacción real en testnet Sepolia y la muestra en Etherscan. Cierra con:

> *"Esto que acaban de ver es lo que vamos a entender hoy. Y al final de la clase, cada uno lo va a haber hecho."*

---

## 2. Dinero, confianza e intermediarios

El dinero cumple tres funciones: **medio de pago**, **unidad de cuenta** y **depósito de valor**.

Historia corta:

- **Trueque** → requiere doble coincidencia de necesidades.
- **Mercancías** (oro, sal) → aceptadas, pero incómodas.
- **Dinero estatal** → aparece una autoridad central que respalda el valor.
- **Dinero fiat** (1971+) → ya no respaldado por oro; respaldado por confianza en el emisor.

Todo este sistema depende de **confiar en intermediarios** (bancos, gobiernos, procesadores). Ellos llevan el registro, validan transacciones, pueden congelar tu cuenta.

> **¿Y si pudiéramos tener un sistema donde nadie tenga que confiar en un intermediario porque el sistema mismo garantiza las reglas?**

Esa es la pregunta que blockchain responde.

---

## 3. Qué es blockchain

**Metáfora del cuaderno compartido:** un cuaderno donde se anotan todas las transacciones. Pero en lugar de un banco, **cada participante tiene una copia idéntica actualizada en tiempo real**.

Flujo:

1. Una transacción se anuncia a toda la red.
2. Todos verifican que sea válida.
3. Las transacciones válidas se agrupan en un **bloque**.
4. El bloque se "encadena" al anterior con criptografía → **blockchain**.

**¿Por qué es seguro?** Para falsificar un registro habría que modificar la copia en la mayoría de las computadoras de la red simultáneamente. En Ethereum eso significa atacar cientos de miles de nodos en todo el mundo a la vez.

**Lo verdaderamente nuevo:** por primera vez en la historia, podemos llevar un registro confiable **sin un intermediario que dé credibilidad al registro**.

### ✅ Check rápido

¿Qué garantiza que una transacción no pueda alterarse?

- a) Un banco la firma.
- b) Para alterarla habría que cambiar la copia del registro en la mayoría de la red.
- c) Está encriptada con una contraseña.
- d) Vitalik la aprueba.

<details><summary>Ver respuesta</summary>

**b)** La seguridad viene de la replicación distribuida, no de una autoridad central.

</details>

---

## 4. Qué es Ethereum

> **Bitcoin = calculadora** (hace una cosa, muy bien).
> **Ethereum = computadora** (corre programas arbitrarios).

Ethereum es una red mundial de computadoras que ejecutan un protocolo común. Sobre esa red, cualquiera puede:

- Crear una cuenta sin permiso.
- Transferir valor (token nativo: **ETH**).
- Ejecutar **contratos inteligentes**: programas que corren solos al cumplirse ciertas condiciones.
- Construir aplicaciones (DeFi, NFTs, juegos, identidad) usables por cualquiera.

### Contratos inteligentes

Un contrato tradicional necesita un notario o un abogado para hacerse cumplir. Un **contrato inteligente** se ejecuta solo cuando se cumplen sus condiciones, y nadie puede impedirlo.

**Ejemplo:** *"Si Juan envía 1 ETH antes del 31 de diciembre, el contrato le transfiere el NFT X. Si no, devuelve los fondos."* Se programa una vez, se ejecuta solo, para siempre.

### Qué puede hacer Ethereum

- **Servicios financieros abiertos** (DeFi): prestar, ahorrar, intercambiar sin banco.
- **Propiedad digital real:** activos que son tuyos sin depender de una empresa.
- **Coordinación global** (DAOs): organizaciones donde las reglas las hace el código.
- **Aplicaciones componibles** (como piezas de LEGO).
- **Resistencia a la censura.**

### ¿Quién controla Ethereum?

**Nadie.** Existe mientras haya computadoras (nodos) ejecutando el protocolo. Cualquiera puede correr un nodo. Las decisiones se discuten en propuestas abiertas (EIPs). El código es open source con múltiples implementaciones independientes.

### Bitcoin vs Ethereum

| | Bitcoin | Ethereum |
|---|---|---|
| Año | 2009 | 2015 |
| Propósito | Dinero digital | Computadora descentralizada |
| Programable | Muy limitado | Sí (smart contracts) |
| Token | BTC | ETH |
| Suministro | 21M (fijo) | Sin límite duro |
| Consenso (2026) | Proof of Work | Proof of Stake |
| Tiempo por bloque | ~10 min | ~12 seg |

---

## 5. Bitcoin como contexto

En 2008, **Satoshi Nakamoto** publicó el whitepaper de Bitcoin: una moneda digital sin banco central. En enero de 2009 se minó el primer bloque.

**Lo que Bitcoin trajo:**

- Descentralización real (no hay "Bitcoin Inc.").
- Transacciones peer-to-peer.
- Escasez digital (21M de BTC, inalterable).
- Propiedad inconfiscable: quien tiene la clave privada controla los fondos.

### Claves privadas y públicas

Concepto crítico (aplica también a Ethereum):

- **Clave pública / dirección:** como un número de cuenta. La compartís para recibir.
- **Clave privada:** prueba que sos el dueño. **Quien la tiene, controla los fondos.**

> ⚠️ **Esto es lo más importante de la clase.** Reaparece cuando creemos la wallet.

### Por qué Bitcoin no alcanzaba

Bitcoin resolvió "dinero digital sin banco", pero su lenguaje es limitado a propósito: no se pueden programar contratos complejos. En 2013, **Vitalik Buterin** propuso una blockchain con un lenguaje completo. Esa propuesta se volvió Ethereum (2015).

---

## 6. Consenso

Si miles de computadoras llevan una copia del mismo registro, **¿cómo se ponen de acuerdo sobre la versión correcta?** Con un algoritmo de consenso.

### Proof of Work (Bitcoin)

Los **mineros** compiten resolviendo un acertijo computacional. El primero que lo resuelve agrega el bloque y gana una recompensa.

- Seguro: atacar la red requiere más cómputo que el resto del mundo combinado.
- Costoso: consume mucha energía.

### Proof of Stake (Ethereum desde 2022)

Los **validadores** apuestan (stakean) ETH como garantía. La red elige al azar quién propone el siguiente bloque, ponderado por cuánto stakearon. Si un validador actúa mal, **pierde su stake** (*slashing*).

- Seguro: atacar requiere arriesgar enormes cantidades de ETH.
- Eficiente: **~99.95% menos energía que PoW.**

### The Merge

En septiembre de 2022, Ethereum migró de PoW a PoS. Esto desmiente el mito "Ethereum gasta mucha energía" — ya no.

### ¿Puedo ser validador?

Sí, con 32 ETH y un nodo propio. Como eso es mucho dinero, la mayoría participa vía:

- **Staking pools** (juntan ETH de varias personas).
- **Liquid staking** (Lido, Rocket Pool): stakeás cualquier cantidad y recibís un token que representa tu stake.

### ✅ Check rápido

¿Cuál es verdadera sobre Ethereum hoy?

- a) Usa PoW y consume mucha energía.
- b) Para validar hay que resolver problemas matemáticos.
- c) Usa PoS desde 2022 y consume muy poca energía.
- d) Solo Vitalik puede validar.

<details><summary>Ver respuesta</summary>

**c)** Desde The Merge (sep 2022), Ethereum usa PoS.

</details>

---

## 7. 🛠️ Práctica: tu primera wallet

**Esto es lo más importante de la clase.** Al terminar tenés wallet propia, ETH de prueba, y una transacción tuya en la blockchain.

> ⚠️ Todo se hace en **Sepolia testnet**. El ETH no tiene valor real. Es un sandbox seguro.

### Paso 1 — Instalá MetaMask

1. Andá a **[metamask.io](https://metamask.io)**.
2. Descargá la extensión para tu navegador (Chrome, Firefox, Brave o Edge).
3. **Verificá la URL oficial.** Hay extensiones falsas que roban fondos.
4. Hacé clic en el ícono del zorrito → **"Create a new wallet"**.
5. Creá una contraseña fuerte (protege la wallet en *este* navegador).

### Paso 2 — Guardá tu frase semilla ⚠️

MetaMask te muestra **12 palabras en un orden específico**: la **frase semilla** (*seed phrase*).

> 🚨 **Reglas no negociables:**
>
> 1. **Escribila en papel.** No foto, no mensaje, no email, no Google Docs, no Notas.
> 2. **Guardala en lugar seguro.** Si la perdés, perdés acceso para siempre.
> 3. **Nunca se la compartas a nadie.** Ni a "soporte", ni a "MetaMask oficial", ni a un amigo. **Nadie legítimo te la va a pedir.** Sin excepciones.
> 4. **Quien tiene tu frase semilla, controla tus fondos.**

Confirmá la frase ordenando las palabras. Listo, tu wallet está creada.

### Paso 3 — Cambiá a Sepolia testnet

1. En MetaMask, hacé clic en el nombre de la red arriba ("Ethereum Mainnet").
2. Activá **"Show test networks"** si no aparecen.
3. Seleccioná **Sepolia**.
4. Tu saldo debería decir **0 SepoliaETH**.

### Paso 4 — Conseguí ETH de prueba en un faucet

Un **faucet** regala ETH de testnet para experimentar.

Faucets activos:

- [sepoliafaucet.com](https://sepoliafaucet.com) (requiere cuenta Alchemy)
- [alchemy.com/faucets/ethereum-sepolia](https://www.alchemy.com/faucets/ethereum-sepolia)
- [cloud.google.com/application/web3/faucet/ethereum/sepolia](https://cloud.google.com/application/web3/faucet/ethereum/sepolia)

1. Copiá tu dirección pública desde MetaMask (empieza con `0x...`).
2. Pegala en el faucet y solicitá ETH.
3. En ~30 segundos vas a ver el saldo actualizado.

### Paso 5 — Hacé tu primera transacción

1. En MetaMask, hacé clic en **Send**.
2. Pegá una dirección de destino (la tuya misma o la de un compañero).
3. Ingresá una cantidad pequeña (ej. `0.001`).
4. Revisá:
   - **From / To**
   - **Amount**
   - **Gas fee** (lo que se paga a los validadores; también en ETH).
5. Confirmá. Estado: *Pending → Confirmed*.

### Paso 6 — Encontrá tu transacción en Etherscan

[Etherscan](https://sepolia.etherscan.io) es un explorador público de la blockchain.

1. En MetaMask, hacé clic en la transacción.
2. **"View on block explorer"**.
3. Identificá:
   - **Transaction Hash** (DNI de la transacción)
   - **Status** (Success/Failed)
   - **Block** (número de bloque donde quedó)
   - **From / To**
   - **Value**
   - **Transaction Fee**

### 🎉 Lo que acabás de hacer

- Creaste una wallet propia.
- Usaste la red Ethereum.
- Hiciste una transacción permanente.
- La viste en un explorador público mundial.

**No le pediste permiso a ningún banco. No diste tu nombre ni tu DNI. Funcionó.**

---

## 8. Cierre

**Lo que vimos hoy:**

- El dinero históricamente dependió de intermediarios.
- Blockchain permite registros confiables sin intermediarios.
- Ethereum no es solo dinero: es una computadora descentralizada.
- Bitcoin fue el primero; Ethereum lo expandió.
- Ethereum usa PoS desde 2022 (eficiente).
- Ya cada uno tiene wallet y usó la red.

**Próxima clase:** Ethereum en Profundidad — contratos inteligentes, EVM, tokens (ERC-20, ERC-721), DeFi, DAOs, L2s.

---

## 🌐 Bonus: viendo Ethereum en vivo

**[TxCity](https://txcity.io/v/eth-btc)** es un visualizador en tiempo real de Ethereum (izquierda) y Bitcoin (derecha).

Metáfora:

- 👤 Cada persona = una transacción.
- 🚌 Cada colectivo = un bloque.
- 🛣️ El colectivo arranca = el bloque se confirmó.
- 💰 El "precio del pasaje" = el gas/fee.

Las personitas en la vereda son el **mempool** (transacciones esperando ser incluidas en un bloque).

**Cosas que se ven de inmediato:**

- Los colectivos de Ethereum salen mucho más seguido (~12s vs ~10min de Bitcoin).
- Ethereum sube más gente por colectivo (más transacciones por bloque).
- Cuando hay congestión, las transacciones que pagan más fee se suben primero → por eso las fees suben en momentos de alta demanda.

**Frase de cierre:** *"Lo que están viendo es economía global moviéndose en vivo, sin que ningún banco o gobierno tenga que aprobarlo."*

---

## 📖 Glosario

| Término | Definición |
|---|---|
| **Blockchain** | Base de datos distribuida que registra transacciones de forma inmutable. |
| **Bloque** | Conjunto de transacciones validadas que se agrega a la cadena. |
| **Clave privada** | Secreto criptográfico que prueba propiedad de los fondos. |
| **Clave pública / Dirección** | Identificador para recibir fondos (empieza con `0x...`). |
| **Contrato inteligente** | Programa que se ejecuta automáticamente al cumplirse sus condiciones. |
| **ETH** | Token nativo de Ethereum. |
| **EVM** | Ethereum Virtual Machine: el motor que ejecuta los contratos. |
| **Explorador de bloques** | Web que muestra la actividad pública de la blockchain (Etherscan). |
| **Frase semilla** | 12-24 palabras que permiten recuperar una wallet. Llave maestra. |
| **Gas** | Costo computacional de una operación; se paga en ETH. |
| **Hash** | Código único generado a partir de datos. |
| **Mainnet** | Red principal de Ethereum (ETH tiene valor real). |
| **Mempool** | Sala de espera de transacciones antes de entrar a un bloque. |
| **Nodo** | Computadora que ejecuta el protocolo de Ethereum. |
| **PoS** | Proof of Stake: consenso basado en stake. Ethereum desde 2022. |
| **PoW** | Proof of Work: consenso basado en cómputo. Lo usa Bitcoin. |
| **Testnet** | Red de prueba (Sepolia). ETH sin valor real. |
| **Validador** | Participante en PoS que stakea ETH para proponer/validar bloques. |
| **Wallet** | Programa que guarda claves e interactúa con la red (MetaMask). |

---

## 📚 Recursos

### Sitios oficiales

- [ethereum.org](https://ethereum.org/) — sitio oficial.
- [Ethereum Whitepaper](https://ethereum.org/en/whitepaper/) — documento fundacional.
- [Vitalik Buterin Blog](https://vitalik.eth.limo/)

### Para profundizar

- [ETH Kipu — Fundamentos de Blockchain](https://eth-kipu.gitbook.io/ethereum-developer-pack/modulo-1/fundamentos-de-blockchain)
- [TxCity (visualización en vivo)](https://txcity.io/v/eth-btc)
- [Sepolia Etherscan](https://sepolia.etherscan.io)

### Libros

**Principiantes:**
- *Blockchain Basics* — Daniel Drescher
- *The Basics of Bitcoins and Blockchains* — Antony Lewis
- *Read Write Own* — Chris Dixon

**Historia:**
- *The Infinite Machine* — Camila Russo (historia de Ethereum)
- *Out of the Ether* — Matthew Leising

**Técnico:**
- *Mastering Ethereum* — Antonopoulos & Wood
- *Token Economy* — Shermin Voshmgir

---

## 📜 Licencia

Material adaptado por **maximilian0.eth**.

Los derechos del contenido original pertenecen a [**ETH Kipu**](https://ethkipu.notion.site/Ethereum-Starter-Pack-Clase-1-Introducci-n-a-Blockchain-y-Ethereum-979994adeea3478181dcc74e2ea949ab).

---

> **¿Errores o sugerencias?** Abrí un issue o un PR.
