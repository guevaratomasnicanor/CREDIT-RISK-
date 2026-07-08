# 🏦 Credit Risk Prediction

**Dataset:** [Credit Risk Benchmark Dataset – Kaggle](https://www.kaggle.com/datasets/adilshamim8/credit-risk-benchmark-dataset)  
**Observaciones:** 16,714  
**Variables:** 11 (10 numéricas + 1 binaria)  
**Objetivo:** Predecir si un cliente incurrirá en *default* (mora) en los próximos dos años.

---

## 📋 Descripción de las variables

| Variable | Descripción |
|-----------|--------------|
| **rev_util** | Ratio de utilización del crédito rotativo (balance / límite de crédito) |
| **age** | Edad del prestatario |
| **late_30_59** | Cantidad de veces con mora de 30–59 días |
| **late_60_89** | Cantidad de veces con mora de 60–89 días |
| **late_90** | Cantidad de veces con mora de 90 días o más |
| **debt_ratio** | Relación deuda / ingresos o activos |
| **monthly_inc** | Ingreso mensual del prestatario |
| **open_credit** | Número de líneas de crédito o préstamos abiertos |
| **real_estate** | Número de préstamos o líneas de crédito hipotecario |
| **dependents** | Número de dependientes |
| **dlq_2yrs** | **Variable objetivo** — Indica si ocurrira una morosidad seria en los próximos 2 años (0 = No, 1 = Sí) |

---

## 🔍 Principales hallazgos
- 50 % de Personas con morosidad grave en un periodo de 2 años.
- El 68% de las personas no estuvieron atrasadas entre 30 y 59 días
- El 55 % Nunca estuvieron atrasadas.

- Mayor frecuencia de **pagos atrasados** (30–59, 60–89 y +90 días) en los morosos.
  <img width="1342" height="690" alt="Captura de pantalla 2025-11-12 131224" src="https://github.com/user-attachments/assets/be756907-b602-4462-be5e-cd28637e3e16" />
- Los **morosos tienden a ser más jóvenes**.
- Los morosos usan **menor proporción del crédito disponible** o tienen **líneas más pequeñas**.
- Poseen un **menor ratio de deuda actual**, posiblemente porque ya enfrentan restricciones crediticias.  
- Tienen **menores ingresos mensuales promedio**.  
- Los morosos presentan **más dependientes**, lo que podría reflejar mayor presión financiera.

<img width="1354" height="693" alt="Captura de pantalla 2026-01-31 193231" src="https://github.com/user-attachments/assets/84e46579-44e1-476d-a1ec-1a258931166e" />

---

## 🤖 Modelos y resultados

| Modelo | Accuracy | Precision | Recall | F1 Score | AUC-PR |
|---------|-----------|------------|---------|-----------|---------|
| **XGBoost** | 0.7886 | 0.7988 | 0.7713 | 0.7848 | **0.8618** |
| **Random Forest** | 0.7854 | 0.8098 | 0.7458 | 0.7765 | 0.8527 |
| **LightGBM** | 0.7870 | 0.7988 | 0.7670 | 0.7826 | **0.8628** |


EL Mejor modelo es Random XGBOOST con 77,13% de casos malos descubiertos con 80% de precision.

## 💼 Caso de Negocio: Impacto Financiero y Optimización del Punto de Corte

Un modelo predictivo no genera valor por su precisión matemática, sino por las decisiones financieras que habilita. Para conectar la performance del algoritmo con el balance de la compañía, se modeló una función de utilidad considerando costos reales de la industria fintech/bancaria:
* **Pérdida dado el Incumplimiento (LGD):** Costo del capital perdido por cada *default*.
* **Margen de Interés Neto (NIM):** Retorno financiero de los clientes cumplidores.
* **Costos Operativos y de Cobranza preventiva.**

### 📈 Maximización del Beneficio
A través de las curvas de decisión, se determinó el **punto de corte (threshold) óptimo** para la aprobación de créditos:

1. **Eficiencia en la Admisión:** Fijando una tasa de aprobación sostenible del **70%** (requerimiento estándar para mantener la originación de negocio y el crecimiento de la cartera), el modelo logra rechazar al 30% restante con una precisión de filtrado altísima: **9 de cada 10 rechazos eran perfiles con riesgo real de default**.
2. **Retorno Económico:** La implementación automatizada de esta política de admisión generó un **beneficio neto estimado de USD 7.8M** en comparación con una política de aprobación tradicional o basada en reglas expertas lineales.
3. **Estrategia Mitigante:** La detección temprana del 77% de los perfiles de riesgo permite activar células de **cobranza preventiva** y esquemas de **Risk-Based Pricing** (ajuste de tasas de interés indexadas al riesgo individual), protegiendo la rentabilidad sin frenar la expansión comercial.




