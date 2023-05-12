```yaml
Today is {{ ['Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday'][now().weekday()] }}
```

```yaml
{{ (strptime('1-5-2023','%d-%m-%Y')|as_local).weekday() }}
```

