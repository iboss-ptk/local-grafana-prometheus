# Osmosis Local Monitor

Setup local monitoring for Osmosis with Prometheus and Grafana.

This assumes the following configuration:

```toml
# <osmosis_home>/config/app.toml

[telemetry]

# Enabled enables the application telemetry functionality. When enabled,
# an in-memory sink is also enabled by default. Operators may also enabled
# other sinks such as Prometheus.
enabled = true

# PrometheusRetentionTime, when positive, enables a Prometheus metrics sink.
prometheus-retention-time = 1000 # anything > 0
```

```toml
# <osmosis_home>/config/config.toml

[instrumentation]

# When true, Prometheus metrics are served under /metrics on
# PrometheusListenAddr.
# Check out the documentation for the list of available metrics.
prometheus = true

# Address to listen for Prometheus collector(s) connections
prometheus_listen_addr = ":26660" # port must match scrape config in prometheus.yml
```

Where `<osmosis_home>` is, by default, `~/.osmosisd`.


## Grafana setup

Open [localhost:3000](http://localhost:3000) Login with user and password `admin`. And then go to [datasources](http://localhost:3000/connections/datasources). Add Prometheus as a datasource with the following configuration:

Prometheus server URL: `http://prometheus:9090` then click `Save & Test`.


Now you can explore / setup your own dashboards.
