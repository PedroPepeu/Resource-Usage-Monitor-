# Resource Usage Monitor - Architecture

## Overview
A lightweight Docker-based system for monitoring system resources, storing metrics, visualizing trends, and sending alerts.

resource-monitor/
│
├── docker-compose.yml
│
├── prometheus/
│   ├── prometheus.yml
│   └── alert_rules.yml
│
├── grafana/
│   └── (empty - Grafana data will be stored in Docker volume)
│
├── alertmanager/
│   └── alertmanager.yml
│
└── README.md (optional documentation file)

Usage Instructions

    Access the monitoring tools:

        Prometheus: http://localhost:9090

        Grafana: http://localhost:3000 (default credentials admin/admin)

        Node Exporter metrics: http://localhost:9100/metrics

        Alertmanager: http://localhost:9093

    Set up Grafana:

        Log in to Grafana

        Add Prometheus as a data source (URL: http://prometheus:9090)

        Import dashboards (use dashboard ID 1860 for Node Exporter metrics)

    Configure alerts:

        Modify thresholds in prometheus/alert_rules.yml as needed

        Update email settings in alertmanager/alertmanager.yml

Customization Options

    To monitor additional hosts:

        Add more node-exporters to the compose file

        Update Prometheus config with new targets

    To add more metrics:

        Explore available node-exporter metrics at http://localhost:9100/metrics

        Add new alert rules as needed

    To change visualization:

        Create custom Grafana dashboards

        Use different visualization types

Maintenance

    To update configurations:

        Edit the appropriate YAML files

        Run docker-compose restart <service> to apply changes

    To stop the system:
    bash

    docker-compose down

    To preserve data between restarts:

        The Docker volumes will maintain data for Prometheus and Grafana

This lightweight monitoring solution provides comprehensive resource tracking with minimal overhead, suitable for development environments or small production deployments.

    Open Grafana at http://localhost:3000

    Log in with admin/admin (you'll be prompted to change the password)

    Add Prometheus as a Data Source:

        Go to Configuration (⚙) > Data Sources

        Click Add data source

        Select Prometheus

        Set URL: http://prometheus:9090 (Docker internal DNS)

        Click Save & Test (should show "Data source is working")

    Import a Dashboard (optional but recommended):

        Go to Create (+) > Import

        Enter dashboard ID 1860 (Node Exporter Full)

        Click Load

        Select Prometheus data source

        Click Import