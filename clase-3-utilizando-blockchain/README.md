# Ethereum Starter Pack — Clase 3

> Utilizando Blockchain: casos de uso reales, ecosistema argentino y herramientas que vas a usar todos los días.

**Duración:** 2 h · **Nivel:** principiante–intermedio · **Pre-requisitos:** Clases 1 y 2

---

## 🎯 Objetivos

Al finalizar esta clase, vas a poder:

1. Entender por qué Ethereum tiene **adopción real en Argentina y LatAm**, no solo especulación.
2. Conocer **proyectos argentinos** referentes del ecosistema global (OpenZeppelin, POAP, Ripio, TravelX).
3. Saber qué hace **Lendoor** y por qué los préstamos sin colateral son una innovación importante.
4. Identificar **categorías de dApps** y casos de uso (pagos, identidad, finanzas, coleccionables, dominios).
5. Interactuar con una **dApp real** desde tu wallet (ENS o POAP).

---

## 🗺️ Agenda

| # | Sección | Duración |
|---|---|---|
| 1 | Hook + repaso | 5 min |
| 2 | El problema "unbanked": por qué Argentina entiende esto antes que nadie | 15 min |
| 3 | Pagos transfronterizos y stablecoins | 15 min |
| 4 | Proyectos argentinos en el mapa global | 25 min |
| 5 | Lendoor: préstamos sin colateral con reputación on-chain | 15 min |
| 6 | Otras dApps que vale la pena conocer | 15 min |
| 7 | **Práctica: registrá tu primer dominio `.eth` o reclamá un POAP** | 20 min |
| 8 | Cierre y próximos pasos | 10 min |

---

## 1. Hook + repaso

En las clases anteriores entendimos **cómo funciona** Ethereum: bloques, EVM, contratos, gas, L2s.

Hoy nos preguntamos: **¿para qué se usa realmente?** Y más específicamente: **¿qué de esto importa en Argentina?**

> **Hook:** Argentina tiene una de las **tasas más altas de adopción de stablecoins per cápita del mundo**. ¿Por qué? Porque cuando vivís con inflación de tres dígitos, restricciones para comprar dólares, y costos de remesas del 10%, los conceptos abstractos de la Clase 1 dejan de ser abstractos. Son la diferencia entre conservar tu salario o perderlo.

---

## 2. El problema "unbanked": por qué Argentina entiende esto antes que nadie

### 2.1 ¿Qué significa "unbanked"?

**Unbanked** = personas sin acceso a servicios bancarios tradicionales (cuentas, tarjetas, créditos).

Según el Banco Mundial, **~1.400 millones de adultos** en el mundo son unbanked. En LatAm, más del 30% de la población adulta.

### 2.2 Causas

- **Falta de documentación:** muchos no tienen DNI o comprobantes de residencia que pide el banco.
- **Distancia geográfica:** zonas rurales sin sucursales cercanas.
- **Costos:** mantener una cuenta tiene un costo mensual que muchos no pueden absorber.
- **Desconfianza institucional:** corralitos, devaluaciones, quiebras bancarias dejaron secuelas.
- **Subbancarizados:** tienen cuenta pero no acceden a crédito, inversión o ahorro real.

### 2.3 El caso argentino

Argentina es un **laboratorio natural** de adopción cripto. Razones:

- **Inflación crónica:** el peso pierde valor mes a mes. Ahorrar en pesos es perder dinero.
- **Restricciones cambiarias:** el "cepo" limita comprar dólares oficiales.
- **Costos de remesas:** mandar/recibir dinero del exterior por bancos cuesta caro y tarda días.
- **Sistema bancario percibido como frágil:** memoria del 2001.
- **Población muy educada en tecnología:** alta penetración de internet y smartphones.

**Resultado:** millones de argentinos ya usan stablecoins (USDT, USDC) en su día a día para guardar valor, cobrar trabajos del exterior, y operar sin pasar por el banco.

### 2.4 Cómo Ethereum cambia el juego

Ethereum permite construir **infraestructura financiera abierta**: cualquiera con un smartphone e internet puede acceder a servicios que antes requerían un banco.

- **Cuenta:** una wallet (MetaMask, Ripio, Lemon, etc.). Sin formularios, sin scoring crediticio, sin distancia.
- **Ahorro:** tener stablecoins atadas al dólar.
- **Inversión:** participar en protocolos DeFi con cualquier monto.
- **Crédito:** protocolos como Aave o Lendoor.
- **Pagos:** mandar y recibir dinero globalmente en minutos.

> 💡 **Punto importante:** Ethereum no "reemplaza" al banco — convive. Pero ofrece una alternativa para quienes el banco no cubre, no quiere cubrir, o cubre mal.

---

## 3. Pagos transfronterizos y stablecoins

### 3.1 El problema de las remesas tradicionales

Si vivís en Argentina y un cliente del exterior te paga:

- **Banco/SWIFT:** 3-7 días, comisiones del 5-10%, papeleo, posible retención.
- **Western Union/MoneyGram:** rápido pero caro (8-15% en comisiones + spread).
- **PayPal:** restricciones según el país, fees, conversión forzada a pesos.

Para un freelancer que cobra $1.000 USD/mes, perder 10% en comisiones son **$1.200 USD al año**.

### 3.2 La alternativa cripto

Mismo escenario con USDC en una L2 como Base o Arbitrum:

- **Tiempo:** ~10 segundos.
- **Costo:** $0.05–0.20 USD por transacción.
- **Sin papeleo, sin retención automática.**

> ⚠️ **Aclaración importante:** "sin retención automática" no significa "sin impuestos". En Argentina los ingresos en cripto están alcanzados por impuestos (Ganancias, Bienes Personales según el caso). La diferencia es que vos elegís cuándo y cómo declararlos, no el sistema bancario por vos.

### 3.3 Stablecoins: el dólar digital

Una **stablecoin** es un token cuyo valor está atado a una moneda fiat (generalmente el dólar).

**Las más usadas:**

- **USDC** (Circle): respaldada 1:1 por dólares en cuentas bancarias reguladas. La más confiable.
- **USDT** (Tether): la más líquida globalmente. Reservas menos transparentes históricamente.
- **DAI** (MakerDAO): descentralizada, respaldada por colateral cripto. No depende de una empresa.

**Y desde 2025/2026, stablecoins regionales:**

- **wARS** (Ripio): atada 1:1 al peso argentino. Funciona en Ethereum, Base y World Chain. Útil para pagos locales on-chain sin convertir a USD.

> 💡 **Para el día a día en Argentina:** muchos usuarios mantienen ahorros en USDC y operan en pesos con wARS cuando necesitan transaccionar localmente.

---

## 4. Proyectos argentinos en el mapa global

Argentina tiene una presencia desproporcionada en el ecosistema cripto global respecto a su tamaño. Estos son algunos de los proyectos referentes fundados o liderados por argentinos.

### 4.1 OpenZeppelin

**Qué es:** la **librería de contratos inteligentes más usada del mundo**. Si un proyecto serio despliega un token ERC-20 o un NFT ERC-721, casi seguro está usando OpenZeppelin como base.

**Fundadores:** Demian Brener y Manuel Aráoz, ambos graduados del ITBA.

**Por qué importa:** auditaron contratos por más de **$1.500 millones** en valor. Sus contratos son código abierto, gratis para usar, y son el estándar de seguridad del ecosistema.

**Para los que van a programar:**

```solidity
// Ejemplo: crear un token ERC-20 seguro usando OpenZeppelin
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MiToken is ERC20 {
    constructor() ERC20("Mi Token", "MTK") {
        _mint(msg.sender, 1000 * 10**decimals());
    }
}
```

Con tres líneas tenés un token funcional, auditado y seguro. **Eso es OpenZeppelin.**

🔗 [openzeppelin.com](https://www.openzeppelin.com/) · [docs.openzeppelin.com](https://docs.openzeppelin.com/contracts/)

### 4.2 POAP (Proof of Attendance Protocol)

**Qué es:** un protocolo para crear **NFTs como "souvenires" de eventos**. Asististe a una conferencia, charla, hackathon o meetup → te dan un POAP. Es un NFT ERC-721 único.

**Fundador:** Patricio Worthalter, argentino. Lanzado en ETH Denver 2019.

**Por qué importa:** convirtió el concepto de "demostrar que estuviste en un lugar" en un estándar usado por miles de eventos en todo el mundo. Hoy tiene **millones de POAPs minteados** y se usa en conferencias de Ethereum, comunidades, equipos deportivos, marcas, etc.

**Caso de uso real:** si vas a un evento de cripto, probablemente puedas reclamar un POAP. Lo vas a usar en la práctica de esta clase.

🔗 [poap.xyz](https://poap.xyz/) · [collectors.poap.xyz](https://collectors.poap.xyz/)

### 4.3 Ripio

**Qué es:** la exchange de cripto más antigua de LatAm. Fundada en Argentina en 2013, hoy con más de 3 millones de usuarios en Argentina, Brasil, Colombia, México, Uruguay y España.

**CEO:** Sebastián Serrano.

**Por qué importa más allá de ser una exchange:**

- Lanzó **wARS**, la primera stablecoin del peso argentino respaldada 1:1, ya operativa en Ethereum, Base y World Chain.
- Tiene infraestructura propia (Ripio Chain) y wallet Web3.
- Permite operar el bono soberano AL30 en formato tokenizado (wAL30rd).

🔗 [ripio.com](https://ripio.com/)

### 4.4 TravelX

**Qué es:** plataforma que tokeniza **boletos de avión como NFTs**. El pasaje se vuelve un activo digital que se puede revender, transferir o usar como garantía.

**Origen:** argentino, en alianza con Air Europa, Avianca, Iberia y otras aerolíneas.

**Por qué importa:** caso de uso "no especulativo" claro. Resuelve un problema real (cambiar de nombre un pasaje hoy es burocrático y caro) usando blockchain de forma transparente.

🔗 [travelx.io](https://www.travelx.io/)

### 4.5 Lemon, Buenbit y otras

El ecosistema argentino tiene varias **wallets/exchanges locales** con buen UX y soporte a tarjetas Visa para gastar cripto: **Lemon Cash**, **Buenbit**, **Belo**. No son protocolos Ethereum en sí, pero forman el punto de entrada para millones de usuarios.

---

## 5. Lendoor: préstamos sin colateral con reputación on-chain

### 5.1 El problema con DeFi tradicional

En protocolos como Aave o Compound, para pedir prestado tenés que **depositar más de lo que pedís**. Querés $1.000? Depositá $1.500 en ETH como colateral.

¿Por qué? Porque la blockchain **no sabe quién sos**. No hay scoring crediticio, no hay forma de saber si vas a devolver. El colateral es la única garantía.

**Problema:** esto excluye exactamente a quienes más necesitan crédito: personas sin patrimonio previo.

### 5.2 La propuesta de Lendoor

**Lendoor** es un protocolo de préstamos **sin colateral** en Ethereum mainnet, enfocado específicamente en LatAm.

**Cómo funciona:**

1. **Probás tu identidad** usando **zkPassport** (prueba criptográfica que confirma datos de tu pasaporte **sin revelar el pasaporte**).
2. **Construís reputación on-chain** mostrando tu historial de transacciones, ingresos verificables y comportamiento financiero — todo de forma privada.
3. El protocolo te asigna una **línea de crédito** basada en esa reputación, sin pedirte colateral.
4. La liquidez del lado de los prestamistas se divide en **dos tramos**:
   - **Senior (sUSDC):** más seguro, menor retorno.
   - **Junior (jUSDC):** absorbe pérdidas primero si hay defaults, retorno más alto pero variable.

### 5.3 Por qué importa para Argentina y LatAm

Esto es exactamente el tipo de innovación que **no puede salir de Wall Street**:

- Resuelve un problema que existe principalmente en mercados emergentes (acceso a crédito).
- Usa criptografía moderna (zk-proofs) para preservar privacidad — algo crucial cuando la gente no quiere exponer todos sus datos al protocolo.
- Demuestra que DeFi puede ser **más que especulación**: puede ser infraestructura financiera real.

🔗 [lendoor.xyz](https://lendoor.xyz/)

### ✅ Check rápido

¿Por qué Lendoor puede prestar sin colateral mientras Aave no?

<details><summary>Ver respuesta</summary>

Porque Lendoor verifica **identidad y reputación on-chain** con zk-proofs (sin revelar datos sensibles). Aave es totalmente anónimo: no sabe quién pide prestado, entonces necesita colateral como única garantía. Lendoor cambia el modelo: identidad verificable → menos colateral necesario.

</details>

---

## 6. Otras dApps que vale la pena conocer

### 6.1 ENS (Ethereum Name Service)

**Qué hace:** asocia nombres legibles (`vitalik.eth`) a direcciones de Ethereum (`0xd8dA6BF...`).

**Por qué importa:** así como DNS convierte `google.com` en una IP, ENS convierte `tu-nombre.eth` en tu dirección Ethereum. Más fácil de recordar, más fácil de compartir, y funciona en cualquier wallet y dApp.

Cada nombre `.eth` es un **NFT** (ERC-721). Es tuyo, lo podés vender, transferir, asignar.

🔗 [ens.domains](https://ens.domains/) · [app.ens.domains](https://app.ens.domains/)

### 6.2 Uniswap

**Qué hace:** intercambio descentralizado de tokens. El DEX más usado del mundo.

**Cómo:** en lugar de un libro de órdenes (como Binance), usa **pools de liquidez**: contratos que mantienen pares de tokens y permiten intercambiarlos al precio determinado por una fórmula matemática.

🔗 [app.uniswap.org](https://app.uniswap.org/)

### 6.3 Aave

**Qué hace:** préstamos colateralizados. El mayor protocolo de lending en Ethereum (~$44B TVL).

Depositás un activo → ganás interés. Pedís prestado contra tu colateral → pagás interés. Todo automatizado.

🔗 [aave.com](https://aave.com/)

### 6.4 OpenSea / Blur

**Qué hacen:** marketplaces de NFTs. Comprar, vender, descubrir colecciones.

🔗 [opensea.io](https://opensea.io/) · [blur.io](https://blur.io/)

### 6.5 Snapshot

**Qué hace:** sistema de votación off-chain para DAOs. Los miembros votan firmando con su wallet, sin pagar gas. Las decisiones aprobadas se ejecutan después on-chain.

🔗 [snapshot.org](https://snapshot.org/)

### 6.6 Etherscan

Más que un explorador — es **la herramienta más usada del ecosistema**. Verificar transacciones, leer contratos, auditar wallets, todo pasa por acá.

🔗 [etherscan.io](https://etherscan.io/)

---

## 7. 🛠️ Práctica: interactuá con una dApp real

> ⏱️ **20 minutos.** Elegí una de las dos opciones (o hacé las dos si te queda tiempo).

### Opción A — Reclamá un POAP

Si hubo un POAP creado para esta clase (preguntale al instructor), reclamalo:

1. Conectá MetaMask en [collectors.poap.xyz](https://collectors.poap.xyz/).
2. Ingresá el código que te dé el instructor o escaneá el QR.
3. El POAP se mintea a tu wallet — sin que pagues gas (POAP usa una L2 para que sea gratis).
4. Andá a tu colección en `collectors.poap.xyz/scan/[tu-dirección]` y vas a ver el POAP listado.

**Lo que pasó por debajo:** un contrato ERC-721 acaba de mintear un NFT único asignado a tu dirección. Es tuyo, está en blockchain, y vale como prueba criptográfica de que estuviste en esta clase.

### Opción B — Buscá un dominio `.eth`

> ⚠️ Esto se hace en **mainnet** y cuesta ETH real (entre $5–$50 USD según el nombre). Si no querés gastar, hacé solo la búsqueda sin completar la compra.

1. Entrá a [app.ens.domains](https://app.ens.domains/).
2. Conectá MetaMask.
3. Buscá un nombre que quieras (ej. `tu-nombre.eth`).
4. Si está disponible, mirá el costo:
   - 5+ caracteres: ~$5/año
   - 4 caracteres: ~$160/año
   - 3 caracteres: ~$640/año
5. Si querés completarlo: seguí el flujo de registro. Te va a hacer firmar dos transacciones (una commit y una reveal — es una protección anti-front-running).
6. Una vez registrado, podés asignarle tu dirección y otros campos (avatar, twitter, etc.).

**Lo que pasó por debajo:** el contrato del registry de ENS te asignó un NFT con el nombre que elegiste. Ese NFT te da control sobre los registros DNS-like de ese nombre.

### Si no querés hacer ninguna de las dos

Probá esto: en Etherscan buscá la dirección `vitalik.eth`. Vas a ver toda la actividad on-chain del cofundador de Ethereum. **Eso es la transparencia radical de blockchain en acción.**

---

## 8. Cierre y próximos pasos

### Lo que vimos hoy

- Ethereum no es solo especulación: resuelve problemas reales para los unbanked y para mercados con sistemas financieros frágiles.
- Argentina tiene una presencia enorme en el ecosistema global: **OpenZeppelin, POAP, Ripio, TravelX**.
- Lendoor muestra el futuro: DeFi con identidad y reputación, sin colateral.
- ENS, Uniswap, Aave, OpenSea son herramientas que vas a encontrar en cualquier camino que tomes en cripto.
- Reclamaste un POAP o buscaste un dominio: ya interactuaste con dApps reales.

### Qué viene en la próxima clase

**Clase 4 — Hacia Ethereum 2.0:** Proof of Stake en detalle, staking, validadores, MEV, escalabilidad, danksharding, el roadmap de Ethereum hacia los próximos años.

---

## 📖 Glosario

| Término | Definición |
|---|---|
| **Bridge** | Servicio que mueve activos entre redes (L1 ↔ L2, o entre L2s). |
| **Colateral** | Activo depositado como garantía de un préstamo. |
| **DEX** | Decentralized Exchange. Intercambio sin intermediario (ej. Uniswap). |
| **ENS** | Ethereum Name Service. Nombres `.eth` en lugar de direcciones `0x...`. |
| **OpenZeppelin** | Librería de contratos auditados más usada. Fundada en Argentina. |
| **POAP** | Proof of Attendance Protocol. NFTs como prueba de asistencia a eventos. |
| **Remesa** | Transferencia de dinero entre países, típicamente trabajador → familia. |
| **Reputación on-chain** | Historial de actividad de una wallet que sirve como base de credibilidad. |
| **Stablecoin** | Token atado al valor de una moneda fiat (USDC, USDT, DAI, wARS). |
| **TVL** | Total Value Locked. Cuánto valor hay depositado en un protocolo. |
| **Unbanked** | Persona sin acceso a servicios bancarios tradicionales. |
| **wARS** | Stablecoin del peso argentino, emitida por Ripio. |
| **zk-proof** | Prueba criptográfica que verifica algo sin revelar la información subyacente. |

---

## 📚 Recursos

### Proyectos mencionados

- [OpenZeppelin](https://www.openzeppelin.com/) — librería de contratos seguros.
- [POAP](https://poap.xyz/) — NFTs de asistencia.
- [Ripio](https://ripio.com/) — exchange y wARS.
- [TravelX](https://www.travelx.io/) — boletos de avión tokenizados.
- [Lendoor](https://lendoor.xyz/) — préstamos sin colateral con zk-proofs.
- [ENS](https://ens.domains/) — nombres `.eth`.
- [Uniswap](https://app.uniswap.org/) — DEX.
- [Aave](https://aave.com/) — lending protocol.
- [Snapshot](https://snapshot.org/) — votación DAOs.

### Para entender DeFi y el ecosistema

- [Ethereum.org — DeFi](https://ethereum.org/es/defi/)
- [DeFi Llama](https://defillama.com/) — métricas en tiempo real de todos los protocolos.
- [L2Beat](https://l2beat.com/) — comparador de L2s.
- [Dune Analytics](https://dune.com/) — análisis on-chain.

### Para programar usando OpenZeppelin

- [Docs de OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/)
- [Wizard de OpenZeppelin](https://wizard.openzeppelin.com/) — generador visual de contratos seguros.

### Lectura sobre el caso argentino

- [Ripio Launchpad](https://launchpad.ripio.com/blog) — blog en español sobre cripto.
- [Lemon Blog](https://lemon.me/blog) — contenido educativo.

---

## 📜 Licencia

Material adaptado por **maximilian0.eth**.

Los derechos del contenido original pertenecen a [**ETH Kipu**](https://ethkipu.notion.site/Ethereum-Starter-Pack-Clase-3-Utilizando-Blockchain-de99a4ffa20e8346a3700122f9f6703c).
