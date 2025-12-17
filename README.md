# Sistem Monitoring Reaktor Nuklir dengan Streaming, Kafka, MQTT, InfluxDB dan Grafana
## Proyek Akhir Pemrosesan Infrastruktur Data Kelas C

### Dosen
- Nur Hazbiy Shaffan, S.T., M.T.

### Anggota Kelompok
- M Dzakir Thuha Al Ghaffar (245150307111004)
- Abdillah Abyan Ilman Nafian (245150300111003)
- Faaza Fauzan Adzim (245150307111010)
- Ivang Arfandia (245150307111003)
- Fathian Auzaie Hanzalah (245150307111007) 

## Cara Menjalankan

### Start
```bash
docker compose up -d
```

### Buat topic Kafka
```bash
docker compose exec kafka kafka-topics.sh --create   --topic iot.sensors --bootstrap-server localhost:9092   --partitions 3 --replication-factor 1
```

### Jalankan MQTT Publisher
```bash
python mqtt_publisher.py
```

### Jika ingin melihat log bridge
```bash
   docker compose logs -f bridge
```

### Jika ingin melihat log telegraf
```bash
   docker compose logs -f telegraf
```

### InfluxDB dan Grafana

- InfluxDB: <http://localhost:8086>  
  user: `admin` / pass: `admin123`

- Grafana: <http://localhost:3000>  
  user: `admin` / pass: `admin123`  

---

## Struktur Proyek

```
grafana/
  provisioning/
    datasources/datasource.yml
    dashboards/dashboards.yml
    dashboards/json/dashboard.json
telegraf/telegraf.conf
mosquitto/mosquitto.conf
bridge/
  Dockerfile
  requirements.txt
  mqtt_to_kafka.py
screenshot_prototype/
  KondisiDanger.jpeg
  KondisiMaintenance.jpeg
  KondisiWarning.jpeg
  KondisiSafe.jpeg
  OutputTerminal.jpeg
Dashboard_Grafana_Sistem_Monitoring_Reaktor_Nuklir.json
docker-compose.yml
mqtt_publisher.py
README.md
```
---
## Screenshot

### Kondisi Safe
![kondisi safe](https://github.com/DzakirT/Sistem_Monitoring_Reaktor_Nuklir/blob/main/screenshot_prototype/KondisiSafe.jpeg?raw=true)

### Kondisi Warning
![kondisi warning](https://github.com/DzakirT/Sistem_Monitoring_Reaktor_Nuklir/blob/main/screenshot_prototype/KondisiWarning.jpeg?raw=true)

### Kondisi Maintenance
![kondisi maintenance](https://github.com/DzakirT/Sistem_Monitoring_Reaktor_Nuklir/blob/main/screenshot_prototype/KondisiMaintenance.jpeg?raw=true)

### Kondisi Danger
![kondisi danger](https://github.com/DzakirT/Sistem_Monitoring_Reaktor_Nuklir/blob/main/screenshot_prototype/KondisiDanger.jpeg?raw=true)

### Output Terminal
![output terminal](https://github.com/DzakirT/Sistem_Monitoring_Reaktor_Nuklir/blob/main/screenshot_prototype/OutputTerminal.jpeg?raw=true)
