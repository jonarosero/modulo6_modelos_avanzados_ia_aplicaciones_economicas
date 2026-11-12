# Datos del Módulo 6

Los notebooks leen estos archivos desde disco. En Colab, la celda de preparación los descarga de este repositorio.

## `impago_tarjetas.csv`

Clientes de tarjeta de crédito de un banco de Taiwán, con su comportamiento de abril a septiembre de 2005 y si impagaron en octubre de 2005. 30 000 filas, 25 columnas. Los montos están en dólares taiwaneses (NT$).

**Fuente:** Yeh, I. C. y Lien, C. H. (2009). *Default of Credit Card Clients*. UCI Machine Learning Repository, https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients (licencia CC BY 4.0). Es el mismo conjunto `UCI_Credit_Card.csv` del proyecto final del Módulo 3; aquí solo se renombraron las columnas al español.

| Columna | Original | Significado |
|---|---|---|
| `id` | `ID` | identificador del cliente (no se usa como predictor) |
| `limite_credito` | `LIMIT_BAL` | cupo de la tarjeta (NT$) |
| `sexo` | `SEX` | 1 = hombre, 2 = mujer |
| `educacion` | `EDUCATION` | 1 = posgrado, 2 = universidad, 3 = secundaria, 4 = otros; 0, 5 y 6 = no documentado |
| `estado_civil` | `MARRIAGE` | 1 = casado, 2 = soltero, 3 = otro; 0 = no documentado |
| `edad` | `AGE` | años |
| `atraso_sep`, `atraso_ago`, `atraso_jul`, `atraso_jun`, `atraso_may`, `atraso_abr` | `PAY_0`, `PAY_2`, ..., `PAY_6` | estado de pago de cada mes: −2 = sin consumo, −1 = pagó todo, 0 = pagó el mínimo, 1 = un mes de atraso, 2 = dos meses, ..., 8 = ocho meses |
| `factura_sep`, ..., `factura_abr` | `BILL_AMT1`, ..., `BILL_AMT6` | saldo facturado de cada mes (NT$) |
| `pago_sep`, ..., `pago_abr` | `PAY_AMT1`, ..., `PAY_AMT6` | monto pagado en cada mes (NT$) |
| `impago` | `default.payment.next.month` | **objetivo**: 1 = no pagó en octubre, 0 = pagó |

Tasa de impago: 22.1 % (6 636 de 30 000).

**Advertencias**

- Es un conjunto público para aprender. No representa a ninguna cartera ecuatoriana y un modelo entrenado con él no se puede trasladar a otra institución.
- Incluye sexo, edad y estado civil. En un caso real hay que revisar si la regulación permite usarlos para decidir sobre un crédito.

## `series_economicas.csv`

La misma tabla mensual del Módulo 5 (enero 1969 a noviembre 2026; cada columna empieza cuando la fuente empieza a publicarla). Fuentes: INEC (IPC) y Banco Central del Ecuador (Información Estadística Mensual).

| Columna | Unidad | Desde |
|---|---|---|
| `ipc_indice`, `ipc_var_mensual` | índice / % mensual | 1969 |
| `tasa_activa_ref_pct`, `tasa_pasiva_ref_pct` | % | ene 2015 |
| `liquidez_m2_musd` | millones de USD | ene 2000 |
| `reservas_internacionales_musd` | millones de USD | ene 2000 |
| `exportaciones_fob_musd`, `exportaciones_petroleras_musd`, `importaciones_fob_musd`, `balanza_comercial_musd` | millones de USD FOB | ene 1990 |
| `riesgo_pais_pb` | puntos básicos (EMBI, promedio del mes) | ene 2000 |
| `precio_crudo_oriente_usd`, `precio_wti_usd` | USD por barril | ene 2000 |
| `salario_real_indice` | índice | ene 2002 |

En este módulo se usa en la Unidad 2 (regresión bayesiana de la inflación y red bayesiana crudo → riesgo país → reservas), en la Unidad 4 (red para pronosticar la inflación y detección de meses anómalos) y en la ruta de pronóstico del proyecto final.
