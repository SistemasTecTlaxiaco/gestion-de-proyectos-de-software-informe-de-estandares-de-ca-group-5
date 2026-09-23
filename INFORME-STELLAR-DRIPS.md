# TECNOLÓGICO NACIONAL DE MÉXICO
## Instituto Tecnológico de Tlaxiaco

**Gestión de Proyectos de Software**

**Presenta:**
- Felix Angel García García — 23620141
- Diego Fidel Sosa Cruz — 23620086
- Luis Alexis Morales Jose — 23620141
- Daniel Alejandro Lopez Camarillo — 23620141

**Docente:** Roman Cruz Jose Alfredo

**Grupo:** 7US
**Carrera:** Ingeniería en Sistemas Computacionales

Tlaxiaco, Oax., a 09/09/2026

*"Educación, Ciencia y Tecnología, Progreso Día con Día"*

---

## Contenido

1. [Introducción](#1-introducción)
2. [Objetivo general](#objetivo-general)
3. [Materiales utilizados](#materiales-utilizados)
4. [Metodología](#metodologia)
   1. [Desempeño técnico: análisis de Stellar y Drips](#1-desempeño-técnico-análisis-de-stellar-y-drips)
      - [1.1 Stellar Community Fund (SCF)](#11-stellar-community-fund-scf)
      - [1.2 Drips Network](#12-drips-network)
      - [1.3 Síntesis comparativa](#13-síntesis-comparativa)
   2. [Adaptación a situaciones y contextos complejos](#2-adaptación-a-situaciones-y-contextos-complejos)
      - [2.1 Tensión entre verificación on-chain y operación offline-first](#21-tensión-entre-verificación-on-chain-y-operación-offline-first)
      - [2.2 Adaptación de la auditoría de requerimientos (REQM) a entregables por tramos](#22-adaptación-de-la-auditoría-de-requerimientos-reqm-a-entregables-por-tramos)
      - [2.3 Gestión de la configuración adaptada a Drips](#23-gestión-de-la-configuración-adaptada-a-drips)
      - [2.4 Limitaciones prácticas identificadas](#24-limitaciones-prácticas-identificadas)
      - [2.5 Aplicación a historias de usuario específicas del backlog](#25-aplicación-a-historias-de-usuario-específicas-del-backlog)
   3. [Pensamiento crítico mediante tecnologías: riesgos éticos y de seguridad](#3-pensamiento-crítico-mediante-tecnologías-riesgos-éticos-y-de-seguridad)
      - [3.1 Riesgos de seguridad técnica](#31-riesgos-de-seguridad-técnica)
      - [3.2 Riesgos éticos y de transparencia](#32-riesgos-éticos-y-de-transparencia)
      - [3.3 Riesgo de auditoría de código abierto](#33-riesgo-de-auditoría-de-código-abierto)
   4. [Actividades y conocimientos interdisciplinarios](#4-actividades-y-conocimientos-interdisciplinarios)
   5. [Aportaciones con inteligencia artificial](#5-aportaciones-con-inteligencia-artificial)
5. [Conclusiones](#6-conclusiones)
6. [Referencias bibliográficas](#7-referencias-bibliograficas)

---

## 1. INTRODUCCIÓN

Este informe complementa el Plan de Calidad de Open Hub Tec, versión 1.0, analizando de forma específica los estándares de calidad de software que exigen implícita y explícitamente las plataformas Web3 Stellar (a través de la Stellar Community Fund, SCF) y Drips Network, principales vías de financiamiento descentralizado que el proyecto contempla para sostener su desarrollo.

El objetivo es identificar qué requisitos técnicos, de gobernanza y de transparencia imponen estas plataformas, y cómo dichos requisitos se integran o entran en tensión con el marco de calidad ya definido en CMMI-DEV y MoProSoft, y con el contexto real de conectividad limitada de la región Mixteca.

La investigación se basa en la documentación oficial vigente de la Stellar Development Foundation (SCF Handbook, criterios de sometimiento del Build Award) y de Drips Network (documentación técnica del protocolo, requisitos de reclamación de proyectos vía `FUNDING.json`), consultada en septiembre de 2026.

Cabe precisar que, a partir de enero de 2026, la SCF opera bajo su esquema **"SCF 7.0"**, que reorganizó el Build Award en tres modalidades (Open, Integration y RFP) y sustituyó los criterios de evaluación previos por un modelo de financiamiento basado en hitos que ayuda a los equipos a llevar sus proyectos hasta Mainnet, dirigido a equipos preparados para construir y lanzar en un plazo de 3 a 5 meses. Este cambio es relevante para el presente análisis porque impone, de forma implícita, una exigencia de madurez técnica previa a la solicitud: la arquitectura técnica del proyecto debe estar completa desde el momento de la aplicación, y el primer tramo de fondos debe destinarse a desarrollo real y no a planeación o diseño de sistema, lo cual entra en tensión directa con el enfoque incremental y evolutivo que propone CMMI-DEV, donde la arquitectura suele madurar en niveles crecientes de definición conforme el proyecto avanza.

Por su parte, el mecanismo de reclamación de proyectos en Drips Network exige menos formalidad documental que la SCF, pero introduce sus propios requisitos de gobernanza técnica: una vez verificado el archivo `FUNDING.json`, el equipo mantenedor debe configurar una lista de mantenedores y dependencias a las que se dividirán los fondos entrantes, además de personalizar la apariencia del proyecto en la plataforma, y la dirección Ethereum registrada en ese archivo queda establecida on-chain como la propietaria del proyecto, con capacidad de gestionar sus divisiones (splits), dependencias y mantenedores. Esto plantea un requisito de transparencia estructural —la explicitación pública de dependencias y responsables— que no tiene un equivalente directo en MoProSoft, orientado más bien a la documentación interna de procesos que a la exposición pública y verificable de la cadena de gobernanza del proyecto.

---

## OBJETIVO GENERAL

Analizar los requisitos técnicos, de gobernanza y de transparencia que exigen la Stellar Community Fund (SCF) y Drips Network como principales fuentes de financiamiento descentralizado contempladas por Open Hub Tec, con el fin de determinar su grado de compatibilidad o tensión con el marco de calidad de software definido en el Plan de Calidad v1.0 (basado en CMMI-DEV y MoProSoft), y de proponer lineamientos de adaptación que permitan cumplir dichos requisitos sin comprometer la viabilidad operativa del proyecto en el contexto de conectividad limitada de la región Mixteca.

---

## MATERIALES UTILIZADOS

- **Documentación oficial de la Stellar Development Foundation**: SCF Handbook vigente (esquema SCF 7.0), incluyendo las secciones de *Submission Criteria*, *Budget & Deliverable Guidelines* y *Official Rules* del Build Award, consultadas en septiembre de 2026.
- **Documentación técnica de Drips Network**: Drips Docs, en particular las secciones sobre reclamación de repositorios (*Claim your open-source project*), configuración del archivo `FUNDING.json`, y gestión de splits entre mantenedores y dependencias.
- **Plan de Calidad de Open Hub Tec, versión 1.0**: documento interno de referencia que define el marco de calidad basado en CMMI-DEV y MoProSoft, usado como línea base comparativa.
- **Modelos de referencia de calidad de software**: CMMI-DEV (Capability Maturity Model Integration for Development) y MoProSoft (Modelo de Procesos para la Industria de Software), en sus versiones vigentes.
- **Registros de conectividad y contexto regional**: información recabada sobre la infraestructura de telecomunicaciones y disponibilidad de internet en la región Mixteca, empleada para contrastar los requisitos técnicos de ambas plataformas con las condiciones reales de operación del equipo.
- **Fuentes secundarias**: artículos, guías técnicas y foros de la comunidad (Stellar, Drips, GitHub) consultados para verificar procesos prácticos de aplicación y reclamación de proyectos.

---

## METODOLOGIA

### 1. DESEMPEÑO TÉCNICO: ANÁLISIS DE STELLAR Y DRIPS

#### 1.1 STELLAR COMMUNITY FUND (SCF)

La Stellar Community Fund es el mecanismo de financiamiento de la Stellar Development Foundation (SDF) para proyectos construidos sobre la red Stellar y su plataforma de contratos inteligentes Soroban. Ofrece hasta 150,000 USD en XLM a través del Build Award, distribuido en tres tramos (*tranches*) de entregables, donde el tramo final debe corresponder al lanzamiento en mainnet.

Los requisitos técnicos relevantes para la calidad del software identificados en la documentación oficial son los siguientes:

- **Código abierto obligatorio para contratos inteligentes**: si el proyecto incluye smart contracts, la solicitud debe incluir un plan explícito para liberar ese código como open source.
- **Entregables por tramos verificables**: cada tranche debe tener criterios de aceptación claros y evidencia de avance, lo cual exige trazabilidad de requerimientos similar a la práctica CMMI REQM ya adoptada en el Plan de Calidad.
- **Auditoría técnica antes de mainnet**: el proceso contempla una fase de auditoría extensiva previa al lanzamiento en producción (mainnet), equivalente en espíritu a las prácticas VER/VAL del plan actual.
- **Evidencia de tracción verificable**: el proyecto debe demostrar uso o validación real por parte de usuarios o equipos del ecosistema, no solo una propuesta teórica.
- **Uso significativo de Stellar**: la integración debe mejorar funciones centrales del producto; no se acepta un uso superficial de la red únicamente como almacenamiento de datos.
- **Revisión por panel comunitario**: las propuestas se someten a evaluación de un consejo (Council) apoyado por el equipo legal de SDF, que revisa elegibilidad, KYC y debida diligencia.

#### 1.2 DRIPS NETWORK

Drips es un protocolo de financiamiento continuo (*streaming*) no custodiado, construido sobre contratos inteligentes de Ethereum, orientado a sostener económicamente dependencias de código abierto. A diferencia de SCF, Drips no es un programa de becas con panel evaluador, sino infraestructura autónoma: cualquier repositorio público de GitHub puede recibir fondos incluso antes de ser reclamado por sus mantenedores.

Los requisitos técnicos y de proceso relevantes son:

- **Repositorio público en GitHub como requisito de entrada**: un proyecto solo puede reclamar fondos si su código es un repositorio público real, con actividad verificable.
- **Archivo `FUNDING.json` en la rama por defecto**: es el mecanismo formal mediante el cual los mantenedores comprueban propiedad del repositorio (vía un oráculo de identidad basado en Chainlink) para poder reclamar y configurar el reparto de fondos.
- **Árbol de dependencias declarado**: al reclamar el proyecto, los mantenedores deben declarar qué otras dependencias de código abierto usan, y qué porcentaje de los fondos recibidos reenvían hacia ellas (splits configurables, en cascada).
- **Transparencia on-chain total**: todo el flujo de fondos —entradas, splits y liquidaciones— es público y auditable en la blockchain de Ethereum, sin custodia centralizada.
- **Sin requisito de experiencia previa en Ethereum**: el diseño prioriza accesibilidad para mantenedores sin conocimientos previos de criptomonedas, aunque sí requiere una wallet compatible con Ethereum para reclamar y gestionar el proyecto.

#### 1.3 SÍNTESIS COMPARATIVA

| Dimensión | Stellar Community Fund | Drips Network |
|---|---|---|
| Naturaleza | Programa de becas competitivo con panel evaluador | Infraestructura autónoma de streaming, sin curaduría central |
| Requisito de código abierto | Obligatorio solo para smart contracts | Obligatorio: solo repos públicos de GitHub son elegibles |
| Verificación de identidad | KYC y debida diligencia legal (SDF) | Prueba de propiedad del repo vía `FUNDING.json` + oráculo |
| Evidencia exigida | Tracción, entregables por tramos, auditoría previa a mainnet | Actividad del repositorio y dependencias declaradas |
| Transparencia financiera | Reportes de avance por tramo | 100% on-chain, pública y en tiempo real |

### 2. ADAPTACIÓN A SITUACIONES Y CONTEXTOS COMPLEJOS

Los requisitos de Stellar y Drips fueron diseñados pensando en equipos con conectividad estable y familiaridad previa con infraestructura blockchain. Aplicarlos al contexto de Open Hub Tec —una organización que opera en la región Mixteca, con conectividad limitada e intermitente— exige adaptaciones concretas al plan de calidad ya existente, y no solo su adopción literal.

#### 2.1 TENSIÓN ENTRE VERIFICACIÓN ON-CHAIN Y OPERACIÓN OFFLINE-FIRST

El Plan de Calidad establece como objetivo OQ-03 que al menos el 90% de las funciones críticas operen offline. Sin embargo, tanto la evidencia de tracción que exige SCF como la transparencia de flujos que ofrece Drips dependen de datos verificables en tiempo real sobre una red pública. Esto implica que las funciones de sincronización con Stellar o Drips (registro de transacciones, actualización de splits, comprobación de `FUNDING.json`) deben diseñarse como una capa opcional y diferida, y no como parte de la ruta crítica offline. Se recomienda una arquitectura de cola de sincronización (*sync queue*) que registre localmente los eventos relevantes para financiamiento y los propague a la red cuando exista conectividad, sin bloquear el uso diario de la aplicación (registro de producción de miel, cobros del mercado, trazabilidad de mezcal).

#### 2.2 ADAPTACIÓN DE LA AUDITORÍA DE REQUERIMIENTOS (REQM) A ENTREGABLES POR TRAMOS

El esquema de tramos de SCF obliga a que cada entrega del proyecto tenga criterios de aceptación verificables externamente por el Council de SDF. Esto refuerza y da un propósito externo concreto a la actividad ya prevista en el plan de calidad de auditar el 100% de las historias de usuario antes de entrar a desarrollo (OQ-01). Se recomienda que cada tramo propuesto a SCF se haga corresponder explícitamente con un conjunto cerrado de historias de usuario ya auditadas, de modo que la evidencia de cumplimiento (checklist de verificación, Costo de Calidad por historia) funcione simultáneamente como evidencia de avance ante el financiador.

#### 2.3 GESTIÓN DE LA CONFIGURACIÓN ADAPTADA A DRIPS

Para que Open Hub Tec sea elegible en Drips, el repositorio del proyecto debe mantenerse público, con un archivo `FUNDING.json` válido en la rama principal y con su árbol de dependencias documentado. Esto exige extender el proceso de Gestión de la Configuración (MoProSoft, Soporte) ya definido en el plan, agregando control de versiones específico sobre ese archivo y sobre la lista de dependencias declaradas, de forma que cambios en el árbol de dependencias pasen por el mismo control de cambios que el resto del código.

#### 2.4 LIMITACIONES PRÁCTICAS IDENTIFICADAS

- La verificación KYC y de debida diligencia legal de SCF puede ser un obstáculo para un equipo estudiantil sin figura organizacional formal; se recomienda evaluar constituir una asociación civil o alianza con el Instituto Tecnológico de Tlaxiaco como respaldo institucional.
- El uso de wallets Ethereum para reclamar fondos en Drips introduce una barrera de alfabetización digital para mantenedores sin experiencia previa en criptoactivos, lo que debe abordarse con capacitación específica, no solo documentación técnica.
- La exigencia de Stellar de que la integración sea funcionalmente significativa (no superficial) obliga a decidir con claridad en qué punto del producto —por ejemplo, pagos a apicultores o locatarios del mercado— realmente aporta valor usar Stellar/Soroban, en vez de forzar una integración artificial solo para calificar al fondo.

#### 2.5 APLICACIÓN A HISTORIAS DE USUARIO ESPECÍFICAS DEL BACKLOG

Para que la adaptación no quede en principios abstractos, se revisan a continuación tres historias de usuario ya registradas en el Plan de Calidad (Sección 4.2) frente a los requisitos concretos de Stellar y Drips.

| Historia | Requisito Stellar/Drips que la afecta | Adaptación necesaria |
|---|---|---|
| **HU-01**: Registrar producción y venta de miel por apicultor | Evidencia de tracción real exigida por SCF; posible pago on-chain a apicultores | El registro debe generar un identificador verificable (hash o referencia) que pueda anexarse como evidencia de tracción sin exponer el monto exacto por apicultor en la blockchain pública |
| **HU-02**: Registrar cobros y control de locatarios del mercado | Transparencia on-chain total de Drips si los cobros se canalizan como streams | Se recomienda que Open Hub Tec centralice los cobros y solo reporte totales agregados hacia Drips, para no exponer el detalle financiero individual de cada locatario |
| **HU-03**: Registrar trazabilidad de lotes de mezcal artesanal | Repositorio público y `FUNDING.json` requeridos por Drips para financiar el módulo de trazabilidad como dependencia open source | El módulo de trazabilidad puede liberarse como componente independiente y reutilizable, elegible por sí mismo para Drip Lists de otros proyectos de trazabilidad agroalimentaria |

### 3. PENSAMIENTO CRÍTICO MEDIANTE TECNOLOGÍAS: RIESGOS ÉTICOS Y DE SEGURIDAD

#### 3.1 RIESGOS DE SEGURIDAD TÉCNICA

Los contratos inteligentes que Open Hub Tec pudiera desplegar en Soroban o Ethereum son inmutables una vez publicados en mainnet, por lo que un defecto no detectado en la fase de pruebas se convierte en un riesgo permanente y potencialmente irreversible, muy distinto a un defecto en software tradicional que puede corregirse con un despliegue posterior. Esto exige extender la actividad de Prevención definida en la sección 4 del Plan de Calidad (auditoría, revisiones de código, checklists) con una fase de auditoría de seguridad externa antes de cualquier despliegue a mainnet, tal como exige explícitamente el propio proceso de SCF. En Drips, el riesgo de seguridad se traslada del código propio hacia la confianza en el protocolo: al ser un sistema no custodiado, Open Hub Tec no controla directamente los fondos en tránsito, sino que delega esa custodia en los contratos inteligentes de Drips. El equipo debe evaluar críticamente esta dependencia de un tercero técnico antes de recomendar el uso de la plataforma a productores locales.

#### 3.2 RIESGOS ÉTICOS Y DE TRANSPARENCIA

La transparencia total on-chain que exige y ofrece Drips —todo flujo de fondos es público y auditable— es, al mismo tiempo, una garantía de rendición de cuentas y un riesgo de privacidad financiera para productores individuales (apicultores, locatarios del mercado, productores de mezcal) cuyos ingresos podrían quedar expuestos públicamente en la blockchain. El equipo debe cuestionar críticamente si conviene exponer directamente a productores individuales en Drip Lists, o si es preferible que Open Hub Tec, como organización, actúe como intermediario que reciba fondos de forma agregada y los distribuya localmente, preservando la privacidad financiera individual sin perder la trazabilidad interna. Adicionalmente, la volatilidad de los activos utilizados (XLM en Stellar, tokens ERC-20 en Drips) introduce un riesgo financiero real para una comunidad con recursos limitados: fondos recibidos en criptoactivo pueden perder valor antes de ser convertidos a moneda local, lo cual debe comunicarse con claridad y no minimizarse al presentar estas vías de financiamiento como beneficio para la comunidad.

#### 3.3 RIESGO DE AUDITORÍA DE CÓDIGO ABIERTO

Publicar el código de Open Hub Tec como open source —requisito de elegibilidad en Drips y recomendación fuerte en SCF— implica exponer también la lógica de negocio y los datos estructurales del proyecto (esquemas de precios, reglas de trazabilidad de mezcal, etc.) a cualquier persona. El plan de calidad debe incorporar una revisión crítica de qué componentes se liberan como código abierto y cuáles, si los hay, deben mantenerse privados por razones comerciales o de protección de datos de los productores, antes de asumir que "todo el código debe ser público" sin matices.

### 4. ACTIVIDADES Y CONOCIMIENTOS INTERDISCIPLINARIOS

La búsqueda de financiamiento en Stellar y Drips obliga a integrar, de forma efectiva y no meramente yuxtapuesta, conocimientos de ingeniería de calidad de software con conceptos de economía Web3 (financiamiento on-chain, streaming de fondos, tokenomía). A continuación, se muestra cómo cada práctica de calidad ya definida en el Plan de Calidad de Open Hub Tec adquiere un propósito económico adicional al vincularse con los requisitos de estas plataformas.

| Práctica de calidad (Plan actual) | Vínculo económico Web3 | Valor añadido |
|---|---|---|
| Costo de la Calidad por historia (Sección 4) | Tramos de financiamiento de SCF, liberados contra entregables verificados | El índice de prevención (≥60%) se vuelve evidencia cuantitativa de madurez del equipo ante el Council de SDF |
| Auditoría de historias de usuario (REQM) | Criterios de aceptación exigidos en cada tranche de SCF | Reduce el riesgo de rechazo de tramos por entregables ambiguos |
| Gestión de la Configuración (MoProSoft) | Requisito de repositorio público + `FUNDING.json` en Drips | El control de versiones deja de ser solo interno: se convierte en la interfaz de elegibilidad para recibir fondos |
| Pruebas de conectividad limitada | Diseño de la capa de sincronización con la red Stellar/Ethereum | Evita que la dependencia de blockchain rompa la promesa de disponibilidad offline (OQ-03) |
| Revisión de código cruzada (Ingeniería, MoProSoft) | Auditoría de seguridad previa a mainnet exigida por SCF | Reduce el riesgo financiero de errores irreversibles en contratos inteligentes |

Esta integración muestra que la calidad del software en un proyecto financiado vía Web3 no es solo un atributo técnico interno: se convierte en el lenguaje común mediante el cual el equipo de desarrollo demuestra confiabilidad económica ante financiadores descentralizados. La trazabilidad, la prevención de defectos y el control de configuración —conceptos de ingeniería de software— son, en este contexto, también métricas de riesgo financiero para quienes deciden financiar el proyecto.

### 5. APORTACIONES CON INTELIGENCIA ARTIFICIAL

Siguiendo el formato de transparencia ya establecido en el Plan de Calidad de Open Hub Tec (Sección 5), se documentan a continuación los prompts utilizados para investigar, redactar y enriquecer este informe.

| # | Prompt utilizado | Herramienta | Propósito | Resultado obtenido |
|---|---|---|---|---|
| 1 | Ayúdame a hacer el informe de estándares de calidad esperados por Stellar/Drips, dime qué necesitas te lo brindo y me haces el reporte. | Claude (Anthropic) | Definir alcance del informe y qué insumos se requerían del equipo | Se identificaron los datos necesarios (plan de calidad existente, contexto del proyecto) antes de redactar |
| 2 | Investigar los requisitos reales de Stellar Community Fund para financiamiento de proyectos open source, y los requisitos del protocolo Drips para reclamar fondos vía GitHub. | Claude (Anthropic) con búsqueda web | Fundamentar el análisis técnico (Sección 1) con fuentes oficiales vigentes en vez de descripciones genéricas | Se obtuvieron los requisitos verificados de SCF (tramos, auditoría pre-mainnet, KYC) y Drips (`FUNDING.json`, árbol de dependencias, transparencia on-chain) |
| 3 | Generar el informe completo en Word, cubriendo los cuatro indicadores de la rúbrica (desempeño técnico, adaptación al contexto, pensamiento crítico e interdisciplinariedad). | Claude (Anthropic) | Producir un documento estructurado y verificable alineado a la rúbrica de evaluación | Documento .docx de 7 secciones con tablas comparativas y análisis específico por sección |
| 4 | Verificar si el informe cumple con todos los criterios de la rúbrica y explicarlo punto por punto. | Claude (Anthropic) | Autoevaluar el informe contra la rúbrica antes de la entrega final | Se identificaron dos vacíos: falta de ejemplos aplicados a historias de usuario reales y ausencia de la sección de trazabilidad de uso de IA |
| 5 | Ligar el análisis a las historias de usuario específicas del backlog (HU-01, HU-02, HU-03) y agregar la sección de aportaciones con IA en el mismo formato del Plan de Calidad. | Claude (Anthropic) | Cerrar los vacíos detectados en la autoevaluación y reforzar la evidencia aplicada al proyecto real | Se añadieron la Sección 2.5 (aplicación a historias de usuario) y esta Sección 5 (trazabilidad de prompts) |

**Nota metodológica**: en todos los casos, la información técnica sobre Stellar y Drips (requisitos, procesos, terminología) fue contrastada contra la documentación oficial de la Stellar Development Foundation y de Drips Network antes de incorporarse al informe; la IA se usó como herramienta de investigación, redacción y estructuración, no como fuente primaria de los hechos reportados.

---

## 6. CONCLUSIONES

El financiamiento Web3, lejos de ser una simple fuente alternativa de recursos, opera como un mecanismo externo de exigencia de calidad que obliga a Open Hub Tec a formalizar prácticas que en un proyecto de software convencional podrían quedar como buenas intenciones. Tanto SCF como Drips Network, aunque parten de filosofías distintas —verificación por hitos frente a transparencia continua—, coinciden en un punto esencial: condicionan el flujo de recursos a la evidencia verificable del trabajo realizado, y no a la promesa de que se realizará.

Esto representa una oportunidad genuina para el equipo, ya que empuja a que el marco CMMI/MoProSoft ya adoptado deje de ser un documento de referencia y se convierta en una práctica viva, sostenida por incentivos económicos reales. Sin embargo, esa misma exigencia conlleva riesgos que no deben subestimarse: la irreversibilidad de las transacciones en blockchain, la naturaleza pública y permanente de la información una vez registrada, y la presión por cumplir criterios de elegibilidad pueden llevar a decisiones apresuradas si no se gestionan con la misma disciplina que exige cualquier despliegue a producción.

La respuesta adecuada, como se ha argumentado, no es rechazar estos esquemas de financiamiento ni adoptarlos de forma acrítica como una lista de requisitos por cumplir, sino integrarlos deliberadamente al ciclo de vida del proyecto: extendiendo el plan de calidad con pruebas de resiliencia offline, asignando gobernanza explícita sobre los artefactos de configuración on-chain, exigiendo auditorías de seguridad como puerta de salida obligatoria, y sometiendo cada decisión de exposición de datos a un filtro ético centrado en la protección de los productores locales de la Mixteca. Solo bajo esas condiciones el financiamiento descentralizado deja de ser una fuente de riesgo y se convierte en un catalizador legítimo de madurez técnica y organizacional para el proyecto.

---

## 7. REFERENCIAS BIBLIOGRAFICAS

- Drips Network. (2026). *Claim your open-source project*. Drips Docs. https://docs.drips.network/get-support/claim-your-repository/
- Drips Network. (2023). *Dependency funding with Drips*. Drips Blog. https://www.drips.network/blog/posts/dependency-funding-with-drips
- Stellar Development Foundation. (2026). *Submission criteria — Build Award*. Stellar Community Fund Handbook. https://stellar.gitbook.io/scf-handbook/scf-awards/build-award/submission-criteria
- Stellar Development Foundation. (2026). *Smart contract security audit support*. Stellar. https://stellar.org/grants-and-funding/soroban-audit-bank
- CMMI Institute / ISACA. (2018). *CMMI for Development, Version 2.0*. https://cmmiinstitute.com/cmmi
