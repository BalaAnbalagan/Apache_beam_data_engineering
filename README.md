# Apache Beam Features Demonstration

A comprehensive demonstration of Apache Beam's core features using a Smart Building IoT Sensor Monitoring pipeline.

## Overview

This project demonstrates all 7 required Apache Beam features through a practical IoT use case that processes temperature and humidity sensor data from smart buildings.

## Features Demonstrated

### 1. Pipeline I/O
- Reading sensor data from CSV files
- Writing results to JSON and text outputs
- Multiple output destinations

### 2. Map Transform
- Temperature unit conversion (Fahrenheit to Celsius)
- Field transformations
- 1:1 element processing

### 3. Filter Transform
- Data validation and quality checks
- Removing out-of-range sensor readings
- Conditional element filtering

### 4. ParDo (Parallel Do)
- Custom DoFn implementation
- Anomaly detection logic
- Flexible output (0, 1, or many elements per input)

### 5. Composite Transform
- Reusable processing components
- Encapsulated multi-step transformations
- Code organization and modularity

### 6. Partition
- Data routing by severity (Normal, Warning, Critical)
- Multiple output streams
- Category-based processing

### 7. Windowing
- Time-based data segmentation
- Fixed window aggregations
- Temporal analytics

## Use Case: Smart Building IoT Monitoring

The pipeline processes sensor data to:
- Monitor temperature and humidity levels across multiple buildings
- Detect environmental anomalies
- Categorize readings by severity
- Generate time-windowed statistics for trend analysis
- Route alerts based on severity levels

## Getting Started

### Run in Google Colab

1. Open the notebook in Colab:
   ```
   https://colab.research.google.com/github/BalaAnbalagan/Apache_beam_data_engineering/blob/main/apache_beam_features_demo.ipynb
   ```

2. Run all cells sequentially or use Runtime → Run All

3. The notebook will:
   - Install Apache Beam
   - Generate sample sensor data
   - Demonstrate each feature individually
   - Run the complete integrated pipeline
   - Display visualizations

### Local Setup

If running locally:

```bash
pip install apache-beam[interactive]
pip install matplotlib pandas jupyter
jupyter notebook apache_beam_features_demo.ipynb
```

## Pipeline Architecture

```
CSV Input
    ↓
Pipeline I/O (Read)
    ↓
Composite Transform (Process & Validate)
    ├─ Map (Temperature Conversion)
    └─ Filter (Validation)
    ↓
ParDo (Anomaly Detection)
    ↓
Partition (Split by Severity)
    ├─ Normal → JSON Output
    ├─ Warning → JSON Output
    └─ Critical → JSON Output
    ↓
Windowing (Time-based Aggregation)
    ↓
Pipeline I/O (Write Statistics)
```

## Sample Data

The notebook generates 100 realistic sensor records with:
- Sensor IDs and locations (building, floor)
- Temperature readings (°F and °C)
- Humidity percentages
- ISO timestamps for windowing
- Mix of normal and anomalous readings

## Visualizations

The notebook includes:
- Temperature distribution with threshold markers
- Severity breakdown (pie chart)
- Average temperature by building
- Temperature vs humidity correlation

## Output Files

The pipeline generates:
- `output_normal.json` - Normal temperature readings
- `output_warning.json` - Warning-level readings
- `output_critical.json` - Critical temperature alerts
- `output_windowed_stats.txt` - Time-windowed statistics

## Key Learnings

- **Unified Model**: Same API works for both batch and streaming data
- **Composability**: Build complex pipelines from simple transforms
- **Scalability**: Runs locally or on distributed runners (Dataflow, Flink, Spark)
- **Flexibility**: Custom processing with DoFns and composite transforms
- **Time Handling**: Built-in windowing for temporal analytics

## Real-World Applications

This pipeline pattern applies to:
- IoT device monitoring
- Log analysis and processing
- E-commerce transaction processing
- Financial fraud detection
- Healthcare patient monitoring
- Environmental data analysis

## Technologies

- **Apache Beam** - Unified batch and stream processing
- **Python** - Pipeline implementation
- **Pandas** - Data manipulation
- **Matplotlib** - Visualizations
- **Google Colab** - Interactive notebook environment

## License

MIT

## Author

Created for Apache Beam features demonstration assignment.
