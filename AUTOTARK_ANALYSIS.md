AUTO TARK v4.5.1 FINDINGS — READ ONLY

APK size: ~57 MB

Confirmed classes/strings:
- com.lin.autoTrak.data.autoservice.AutoserviceClient
- com.lin.autoTrak.data.autoservice.AdbOnDeviceClient
- com.lin.autoTrak.data.charging.AutoserviceChargingDetector
- com.lin.autoTrak.cluster.ClusterMirrorService
- XDJAScreenProjection
- helper/autoservice
- http://127.0.0.1:8080
- http://127.0.0.1:8774
- EC_database.db

Room schema v48 includes:
- trips
- trip_points
- charges
- charge_points
- battery_snapshots
- odometer_samples
- last_state
- vehicle_write_log
- automation_rules

Safety decision:
AutoTark also contains service-call / ADB vehicle-write related strings.
WH Auto does not reproduce, invoke, or expose those commands.
v1.3 probes localhost helper endpoints with HTTP GET only.
