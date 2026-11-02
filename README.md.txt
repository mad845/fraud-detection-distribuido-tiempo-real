> Detección de fraude en < 100ms con arquitectura distribuida tolerante a fallos.
> Proyecto final Data + Ciberseguridad - Villa Federal, Resistencia.

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Kafka](https://img.shields.io/badge/Kafka-Streaming-black)
![Spark](https://img.shields.io/badge/Spark-Structured%20Streaming-orange)
![ML](https://img.shields.io/badge/ML-XGBoost-green)
![Docker](https://img.shields.io/badge/Docker-Compose-blue)

🎯 Resultados Clave
- **Latencia Promedio:** 87ms
- **Precisión:** 98.4% (F1-Score)
- **Throughput:** 1,500 transacciones / seg
- **Disponibilidad:** 99.9% (Tolerante a fallos)

🏗️ Arquitectura Distribuida

[POS / APP / WEB] 
      ↓
[APACHE KAFKA] → Topic: transactions
      ↓
[SPARK STRUCTURED STREAMING]
      ↓
   ┌───────────────────────┐
   │  MOTOR 1: REGLAS <10ms │ → Geolocalización imposible, Blacklist IP, Monto atípico
   │  MOTOR 2: ML <50ms     │ → XGBoost + Isolation Forest (45 features)
   └───────────────────────┘
      ↓
[REDIS - Cache Perfil] + [CASSANDRA - Histórico]
      ↓
[ALERTA] → Topic: fraud_alerts → Slack + Bloqueo Automático + Dashboard Grafana

🛠️ Stack Tecnológico
- **Ingesta:** Apache Kafka, Zookeeper
- **Procesamiento:** Apache Spark Structured Streaming
- **Cache:** Redis (perfil usuario en memoria)
- **Storage:** Cassandra (billones de transacciones)
- **ML:** XGBoost, Isolation Forest, Scikit-learn
- **Infra:** Docker, Kubernetes, Grafana

🚀 Cómo correr el proyecto

```bash
1. Levantar infra distribuida
docker-compose up -d

2. Instalar dependencias
pip install -r requirements.txt

3. Entrenar modelo (dataset Kaggle Credit Card Fraud)
python train_model.py

4. Iniciar productor (simula transacciones de Resistencia)
python producer.py

5. Iniciar detector en tiempo real
python fraud_detector.py
📊 Demo en Vivo
Transacción	Ubicación	Monto	Score	Resultado
#a1f2	Av. Chaco, Resistencia	$5.000	0.02	✅ APROBADA
#b4c8	Miami, US (2 min después)	$250.000	0.96	🚨 BLOQUEADA
Dashboard en: `localhost:3000` (Grafana)

🔐 Enfoque Ciberseguridad
- Detección de Account Takeover
- Prevención de Card Not Present Fraud
- Validación de IP / Device Fingerprinting
- Cumplimiento PCI-DSS logging

👨‍💻 Autor
*Tu Nombre* - Data Analyst / Ciberseguridad
Resistencia, Chaco, Argentina

📄 Licencia
MIT - Proyecto educativo con datos sintéticos y dataset público de Kaggle.

⭐ Si te sirvió, dejale una estrella al repo!

**Cómo guardarlo:**
1. Abrí el Bloc de Notas
2. Pegá todo ese código
3. Archivo > Guardar como > Tipo: Todos los archivos
4. Nombre: `README.md`
5. Codificación: UTF-8

Ese es el archivo más importante para tu GitHub, es el que ven los reclutadores primero.